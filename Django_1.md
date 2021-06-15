# Django 프레임 워크

## MTV 패턴
* 웹 개발을 여러명이 담당하는 경우 1) 프론트엔드(HTML, CSS) 2) 백엔드(데이터 처리) 부분으로 나뉨
* Django는 세 부분 Model, Template, View으로 나뉜 MTV 패턴
	* Template은 프론트엔드, Model, View는 백앤드 담당이라고 생각
	* __Template__
		* 사용자가 보이는 영역
		* HTML, CSS
		* 템플릿 언어 
	* __Model__
		* 데이터베이스(DataBase, DB)
	* __View__
		* MTV에서 가장 핵심 요소
		* 데이터를 처리하는 곳
		* 데이터를 가공해서 템플릿에게 넘겨주는 역할



## MTV 패턴 실습_1
* App : Django 프로젝트를 구성하는 작은 단위 

__1) App 만들기__
	```
	cd [프로젝트 파일]
	python manage.py startapp [애플리케이션이름]
	```

* 프로젝트 파일에 App 등록
	* 프로젝트 파일의 settings.py의 INSTALLED_APPS 부분에
	* '[애플리케이션이름].apps.[애플리케이션이름(첫 문자 대문자)]Config', 추가
	* == '[애플리케이션이름].apps.[애플리케이션클래스이름]'
	* 예) __'firstapp.apps.FirstappConfig',__ 

* 웹사이트 구동 순서
	1. 사용자가 서버에 요청
	2. 서버의 View는 Model에게 요청에 필요한 데이터를 받음
	3. View는 받은 데이터를 적절하게 처리해서 Template으로 넘김
	4. Template은 받은 정보를 사용자에게 보여줌


__2) HTML 템플릿 만들기__
	* 애플리케이션 파일에 템플릿 폴더(예: templates) 생성
	* 템플릿 폴더 안에 html 파일 생성 (예: welcome.html)
	* 템플릿 생성

__3) View 만들기__
* 애플리케이션 파일의 views.py에서 생성
* view 코드는 파이썬 함수식으로 작성
```
def welcome(request) :
	return render(request, "welcome.html")
	# welcome함수를 호출하면 render함수에 의해 'welcome.html'호출
```


__4) URL과 View함수 연결하기__
	* 프로젝트 파일의 urls.py 수정
	1. views.py를 urls.py에서 사용할 수 있도록 임포트
	=> __from firstapp import views__
    2. path 설정: urlpatterns에 path("연결할 url주소", 연결할 views, name="") 추가
    => __path('', views.welcome, name="welcome"),__
		* 이는 url주소와 view가 연결됨을 나타냄.
		* 여기서 url주소에 아무것도 적지 않으면(' '), 서버를 구동시키고 처음 들어가는 페이지가 welcome이 되도록하게 함. 
		* 또한 name="welcome"은 다른 html 파일에서 welcome의 url을 사용하고자할 때 사용하는 이름.
		* 서버를 구동해보면 서버주소 다음에 아무것도 적혀있지 않으므로 views.welcome으로 이동한 것을 알 수 있음.

__5) 인터박스에 넣은 값 페이지 화면에 재출력__
	* 앞의 단계(1~4) 반복
	* 여기서 app은 이미 만들었으므로 템플릿 생성부터 시작
	1. hello.html 생성, 출력 양식 작성
	2. views.py에서 view 생성
		```
		def hello(request):
    		username = request.GET["name"]
    		return render(request, "hello.html", {"username":username})
    		# welcome.html의 "name"이란 이름의 input태그의 값을 읽어서 저옴.
    		# reder함수의 세 번째 인자값으로 딕셔너리 형태의 값을 전달하면 해당 데이터들을 hello.html파일로 넘겨줌.
    	```
	3. hello.html에서 템플릿 언어를 사용하여 값 전달 받아서 출력
		* 템플릿 언어 사용: __{{ }}__: 중괄호 두개 사이에 값 입력
		=> __{{username}}__
	4. url과 view 연결
		* path()로 연결
		* 이떄, paht의 URL주소는 모두 달라야함!!
		=> __path('hello/', views.hello, name="hello"),__


* 순서
	1. App을 생성
	2. Template 제작
	3. View 제작
	4. URL 연결






## MTV 패턴 실습_2
* 입력한 단어 수를 세는 Word counter 만들기
* __split()__메소드 이용 : 인자를 주지 않으면 띄어쓰기를 기준으로 분할
* 가상환경 만들기 -> 장고 설치하기 -> 애플리케이션 등록하기 -> 템플릿 만들기 -> view 만들기 -> url과 view함수 연결하기

* __템플릿 언어__ : html에서 파이썬 변수와 문법을 사용하게 해주는 언어
	* 변수명 => __{{변수명}}__
	* 조건문,  반복문 등 => __{% 반복문%} ... {%endfor%}__
		예) {%for word in wordDict%} ... {%endfor%}, {%if word%} ... {%endif%}
* <주의>
	* URL 연결할 때, 애플리케이션의 views를 임포트할 때, 여러 애플리케이션이 존재하면 겹치므로 'as'를 이용하여 각 이름을 지정해준 뒤 path()작성
	* 예) 
	```
    from firstapp import views as first
    from wordCount import views as wc
    
    urlpatterns = [
    	path('', first.welcome, name="welcome"),
        path('hello/', first.hello, name="hello"),
    	path('wc/', wc.home, name="wc"),
    	path('wc/result/', wc.result, name="result"),
	]
	```






## Git 사용법
* git
	* 개발을 진행하는 과정마다 분기점을 만들어서 필요한 경우 그 지점으로 돌아 올 수 있게 만드는것
	* 게임에서 savepoint
* git vs github
	* git은 혼자 작업한 코드를 저장하는 곳
	* github는 git의 정보를 다른사람과 공유하는 플랫폼
* github 사용
	1) github 계정 생성
	2) 레퍼지토리 생성
	3) 터미널에서 git사용
		* __echo " #fistproject" >> README.md__
		: README.md 파일을 만들고 'firstproject' 작성
			* 보통 README.md에는 프로그램의 사용법, 프로그램을 사용하는데 있어 필요한 패키지 설치법 등을 적어줌.
		* __git init__
			: 현재 디렉토리를 새로운 git 저장소로 초기화
			* 여러 프로젝트를 독립적으로 사용하려면 각각 git init으로 초기화해줘야함.
		* __git add__
			: 선택한 파일들을 Staging area에 올림.
			1. 저장할 파일 선택
			2. 선택한 파일을 Staging area에 저장
			* 예) git add file1 file2 
			* 예) git add . => 전체 파일 업로드
			* 올리지 말아야 할 파일 지정
			=> 폴더에 __.gitignore__를 만들어서 올리지 말아야할 파일들 적어줌.
			* 이때, 올리지 말아야할 파일들은 "gitignore.io"사이트를 통해 확인
		* __git commit -m "message"__
			: git add로 Staging area에 올린 파일들을 저장해주는 명령어
			* -m "massage"은 주석처럼 commit의 메세지를 남기는 것
		* __git branch -M main__
			: 마스터 브랜치의 이름을 main으로 바꾼다는 명령어
			* 마스터 브랜치를 계속 사용하려면 필요 X
			* branch는 현재 작업 중인 프로젝트에서 새로운 분기점을 만듦.
		* __git branch [branch 이름]__ : 새로운 브랜치 생성
		* __git checkout [옮길 brach 이름]__ : 브랜치 이동
		* 레퍼지토리 연결
			* __git remote add [remote이름] [repository 주소]__
			* __git push [remote 이름] [branch 이름]__ : 레퍼지토리에 파일 업로드





## Django와 데이터베이스
* __ORM(Object Relation Mapping)__
	* 데이터베이스에 명령을 내리지 않아도 파이썬의 객체지향적인 방법으로 데이터베이스의 데이터를 생성, 삭제, 수정 등을 할 수 있음
* 데이터베이스의 표를 파이썬으로 표현
	* 파이썬의 __class__이용
	* 이렇게 class를 이용하는 것을 객체지향 프로그래밍이라고 함.





## Model 실습
1. models.py에 Blog class 생성
	```
	class Blog(models.Model):
    	title = models.CharField(max_length=200)
    	writer = models.CharField(max_length=100)
    	pub_date = models.DateTimeField()
    	body = models.TextField()
	
    	def __str__(self):
        	return self.title
	```

2. models.py에 테이블을 만들거라는 명령어 작성
	* makemigrations : 앱 내의 migration 폴더를 만들어서 models.py의 변경사항 저장 
	=> __python manage.py makemigrations__
	* migrate : Migration 폴더를 실행시켜 데이터베이스에 적용
	=> __python manage.py migrate__ : migrations 폴더의 변경사항들을 dbsqlite에 적용 시킴
* Django는 admin 패널을 지원해주므로 데이터베이스 쉽게 확인 가능
* 데이터베이스를 관리할 super user 생성
	=> __python manage.py createsuperuser__	
	
	
	
	


## CRUD_Read
* __CRUD(Create Read Update Delete)__: 데이터베이스를 생성하고 읽고 수정하고 삭제하는 것
* view.py
	```
	from .models import Blog
	def home(request):
		blogs.objects.all()
		return render(request, 'home.html', {'blogs':blogs})
	```
* models.py
	```
	...
	def summary(self):
		return self.body[1:100]
	```
	: 내용 요약 함수 생성
* Path-convert
	* views.py
	```
	def detail(request, id):
		blog = get_object_or_404(Blog, pk=id)
		return render(request, 'detail.html', {'blog':blog})
	```
	* url.py
	```
	path('<str:id>', detail, name="detail")
	```





## CRUD_Create
* views.py의 함수
	* __new__: new.html 보여주는 함수
	```
	def new(request):
		return render(request, 'new.html')
	```
	* __create__: 데이터베이스에 저장하는 함수
	```
	def create(request):
		new_blog = Blog()
		new_blog.title = request.POST['title']
		new_blog.writer = request.POST['writer']
		new_blog.body = request.POST['body']
		new_blog.pub_date = timezone.now()
		new_blog.save()
		return redirect('detail', new_blog.id)
	```
* GET vs POST
	* GET
		- 데이터를 얻기 위한 요청
		- 데이터가 url에 보임
		- 보안 취약
	* POSt
		- 데이터를 생성하기 위한 요청
		- 데이터 url에 안보임
		- Csrf공격 방지




## CRUD_Update
* 수정할 데이터의 id값을 받아야함
* views.py의 함수
	* __edit__ : edit.html 보여주는 함수
	```
	def edit(request, id):
		edit_blog = Blog.objects.get(id=id)
		return render(request, 'edit.html', {'blog': edit_blog})
	```
	* __update__: 데이터베이스에 적용하는 함수
	```
	def update(request, id):
		update_blog = Blog.objects.get(id=id)
		udate_blog.title = request.POST['title']
		udate_blog.wirter = request.POST['wirter']
		udate_blog.body = request.POST['body']
		udate_blog.pub_date = timezone.now()
		udate_blog.save()
		return redirect('detail', update_blog.id)
	```
	
	
	
	
## CRUD_Delete
* views.py의 함수
	* delete
	```
	def delete(request, id):
		delete_blog = Blog.objects.get(id=id)
		delete_blog.delete()
		return redirect('home')
	```