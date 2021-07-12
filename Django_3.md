## 배포 사전 준비
* 환경변수 설정
	* 시스템에 저장되어 있는 변수
	* 보통 비밀키 등 유출되면 안되는 정보
	* 또는 환경에 차이를 둘 때 사용(테스트/프로덕션 구별 등)
	* os.environ 에서 dict 형식으로 불러올 수 있음
	* __os.environ.get('변수명','기본값')__으로 사용
* requirements.txt
	* 내 파이썬 (장고) 앱을 실행하기 위해 우선 설치되어야 하는 패키지들
		* 예) Django, Pillow(사진)
	* '패키지명 == 버전' 으로 저장
	* 보통 requirements.txt 파일에 저장
	* __pip freeze__ 명령어는 해당 환경에 설치된 모든 패키지를 보여줌
	* > 는 프로그램의 출력을 파일에 저장한다는 뜻
	* __pip freeze > requirements.txt__ 로 생성
* AWS
	* IAM (Identity and Access Management)의 줄임말
	* IAM에서 계정을 만든 후 해당 계정 로그인 정보,(엑세스 키 & 시크릿 키)를 이용하여 AWS의 API 활용
		* settings.py 설정
		* 예)
		```
		SECRET_KEY = os.environ.get('SECRET_KEY', 'django-insecure-#s^_kt0@_hn$@(s=^&07j%++fg+0*ytli6i325b(sr7ify+9hd')
		```
	* 보안을 위해 권한을 최대한 보수적으로 잡음
	* S3(Simple Storage Service)의 줄임말
	* AWS에서 제공하는 구글드라이브 정도로 생각할 수 있음
	* 최초 용량 지정없이 사용한 만큼과 과금이되므로 용량 예측 필요 X
	* 여러 서버에서 동시에 접속 가능(부하 분산 유리)
	* BeJfq/gddinCpCRbMrlCALXAw7iPyNJXKTBtI1Uf 
	* 버킷 생성
		* s3에서 사용하는 폴더역할
		* 여러 앱을 나눌 때 유용
	* pip install boto3 => aws에서 파이썬 API를 사용할 때 유용한 패키지
	*  settings.py 설정
		* 예) 
		```
        DEFAULT_FILE_STORAGE = 						'storages.backends.s3boto3.S3Boto3Storage'
		
		# AWS_ACCESS_KEY_ID = 'AKIAZPU4YLCZUCXXIYAR'
		# AWS_SECRET_ACCESS_KEY = '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'
		# AWS_STORAGE_BUCKET_NAME = 'likeliondjangolesson'
		AWS_ACCESS_KEY_ID = os.environ.get('AWS_ACCESS_KEY_ID')
		AWS_SECRET_ACCESS_KEY = os.environ.get('AWS_SECRET_ACCESS_KEY')
		AWS_STORAGE_BUCKET_NAME = 'likeliondjangolesson'
		AWS_S3_SIGNATURE_VERSION = 's3v4'
		AWS_S3_REGION_NAME = 'ap-northeast-2'
		AWS_S3_CUSTOM_DOMAIN = ''
		```




## 배포하기
* Heroku 배포하기
	1) Heroku 회원가입
	2) Heroku CLI 설치
	3) 환경변수 적용
		* Debug
		``` DEBUG = (os.environ.get('DEBUG', 'True') != 'False')```
	4) .gitignore 파일 적용
		* git에 적용할 파일 구분해주는 것
		* .gitignore.io에서 Django 선택 후 '생성' 클릭
		* 페이지에 나온 텍스트를 모두 복사 후 .gitignore 파일로 저장
	5) heroku 용 파일 작성
		* Procfile은 heroku에게 실행시킬 파일을 알려줌
		* Procfile 이라는 파일을 만들어 아래 내용 작성
		``` web: gunicorn 프로젝트명.wsgi --log-file -```
		* runtime.txt는 실행시킬 파이썬 버전을 알려줌
		* runtime.txt 파일에 아래 내용 작성
			``` python-3.91```
	6) 필요한 Dependency 설치
		* pip install gunicorn whitenoise dj-database-url psycopg2-binary
	7) settings.py 수정
		* Whitenoise 설치
			* MIDDLEWARE 부분에 SecurityMiddleware 바로 아래에 아래내용 추가
			``` 'whitenoise.middleware.WhiteNoiseMiddleware' ```
		*ALLOWED_HOST 수정
			* ALLOWED_HOST =[] 를 ALLOWED_HOST =['*']로 수정 (전체 접근 가능)
		* DB 관련 코드 수정
			* settings.py 제일 밑 아래에 내용 추가
			```
			import dj_database_url
			db_from_env = dj_database_url.config(conn_max_age=500)
			DATABASES['default'].update(db_from_env)
			```
	8) requirements.txt 생성
		* pip freeze > requirements.txt
	9) git에 수정된 파일들 추가
		* git add -A
		* 
		
	10) Heroku 관련 명령어들 실행
		* heroku login
		* heroku create
		* git push heroku main
		* heroku run python manage.py migrate
		* heroku run python manage.py createsuperuser
		* heroku open
	11) Heroku 에서 환경 변수 설정
		* "dashboard.heroku.com"에서 앱 선택
		* Settings
		* Config Vars > Reveal Config Vars
		* KEY VALUE 값 입력후 저장
		


## Ubuntu 배포하기
* AWS EC2 (Ubuntu)배포 (주의: 요금이 청구될 수 있으니 실습이후 바로 삭제 권함)
1. EC2 인스턴스 만들기
	1) aws 콘솔 페이지 접속
	2) 우측 상단 지역이 서울인지 확인
	3) EC2 검색
	4) Instances > Launch Instances
	5) Ubuntu Server 20.04 LTS 다운
	6) t2.micro (Free tier eligible)
	7) Storage 설정 (Free Tier는 30GB 까지 가능)
	8) Security Group > Add Rule
		1. HTTP
		2. HTTPS
        3. Custom >TCP > 8000 > 0.0.0.0/0.=/0
	9) Review and Launch > Launch
		1. Create a new key pair
		2. 이름은 원하는 이름 설정
		3. Download Key Pair 
2. Elastic IP 받기
	1) Network & Security > Elastic IPs
	2) Allocate Elastic IP address
	3) Allocate
	4) Associate Elastic IP Address
	5) Instance > 아까 생성된 인스턴스 검색
	6) Associate
3. SSH 연결하기
	1) ssh ubuntu@이전에_받은_Elastic_IP -i 다운받은_PEM_FILE
4. 필요한 패키지 설치
	* 자세한 명령어 강의 재참조
5. 패키지 설치하는 동안 settings.py 수정
	* 자세한 명령어 강의 재참조
6. 매번 하던 것들(장고 시작단계)
	* 자세한 명령어 강의 재참조
7. PostgreSQL 설치
	* 자세한 명령어 강의 재참조
8. settings.py 에 DB 설정
	* 자세한 명령어 강의 재참조





## Docker 란?
* Docker? Container? 
	* 간단히 말하면 캠핑카 > 내 작업들을 도커 이미지에 담아 이동, 저장할 수 있음
* Docker 사용
	* Gitpod 사용
		1) settings에서 Feauture Prieview 선택 체크
		2) Defualt IDE Theia 선택 (code는 vscode인데 아직 호환성 문제 존재)
		3) sudo docker up 입력
		4) 이후 자세한 명령어 강의 재참조


## Docker 이미지 생성
* Docker는 각 요소들이 설치된 모습을 '이미지'라는 형태로 저장하고 도커 이미지들을 git으로 저장된 내용들이 github에 올려지는 것 처럼 DockerHub라는 곳에 저장
1. 준비사항
	1) Gitpod.io 계정 생성(free or Student)
		* free는 월 50시간 제한 / student는 월 100시간 제한
	2) Gitpod 설정 수정
		1. Gitpod > Settings
			* Feature Preview > Enable Feature Preview 체크
			* Default IDE 선택
				1. Theia: 이클립스 팀이 만든 IDE (강의에서 이것 사용)
				2. Code: VScode의 웹 버전 IDE(호환성 이슈 존재)
	3) Gitpod 인스턴스 생성
		1. 본인의 GitHub 레포지토리로 이동
		2. 레포지토리 주소 앞에 gitpod.io/# 을 붙임.
	4) DockerHub 계정 설정
2. requirements 설치
	1) pip install -r requirements
3. Whitenoise 설치
	1) pip install whitenoise
	2) MIDDLEWARE에서 SecurityMiddleware 바로 아래 내용 추가
		* 'whitenoise.middleware.WhiteNoiseMiddleware'
4. Gunicorn 설치
	1) pip install gunicorn
5. Dockerfile 생성
	* 자세한 명령어는 강의 재참조





## Docker 서버에 배포하기
1. 준비사항
	1) EC2 인스턴스 (AWS EC2 전반부 참고)
	2) DockerHub에 등록된 이미지
2. 서버 세팅
	1) Docker 설치
	2) Docker Compose 설치
	3) 앱 설치 폴더 지정
	4) docker-compose-yml 생성
	* 이후 자세한 명령어는 강의 재참조
	
	
	




## Docker 이미지 자동 생성 (Github Actions)
1. 준비사항
	1) Docker로 배포하기가 끝난 레포지토리
	2) github 계정
2. github의 내 레포지토리로 이동하기
3. Actions 버튼 선택
* 이후 자세한 명령어는 강의 재참조