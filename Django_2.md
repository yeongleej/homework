## Template 상속
* base.html에서 중복되는 코드가 들어갈 위치에
	``` {% block content %}...{% endblock %}```
* 중복되는 코드가 있는 detail.html에서는 
	1)  코드 맨 위에는 __{% extends 'base.html' %}__ 작성
	2)  ``` {% block content %} ... 중복된 코드 ... {% endblock %}```
* setting.py에서 TEMPLATES 부분에
	* __DIRS':['lionprj/templates'],__ 또는 
	* 'DIRS': [ os.path.join(BASE_DIR, 'templates') ],
* url.py 관리
	* 애플리케이션 파일( blog )에 __'url.py'__를 생성
	* 프로젝트 파일의 url.py에서 앱에 해당하는 path를 애플리케이션 파일의 'url.py'로 이동





## Static
* 장고에서 다루는 파일
	* __ 정적파일__: 미리 서버에 저장되어 있는 파일, 서버에 저장된 그대로를 서비스해주는 파일
	* __동적파일__: 서버의 데이터들이 어느정도 가공된다음 보여지는 파일 (상황에 따라 달라질 수 있음)
* 정적파일
	* Static => 개발자가 서버를 개발할 때 미리 넣어놓은 정적파일(img, js, css)
	* Media => 사용자가 업로드 할 수 있는 파일
* static 파일 사용
	1) 애플리케이션 안에 static 폴더 생성
	2) setting.py에서
		``` STATICFILES_DIRS = [os.path.join(BASE_DIR, 'main', 'static'),] ```
		=> 현재 static 파일이 어디에 있는지 확인
		``` STATIC_ROOT = os.path.join(BASE_DIR, 'static') ```
		=> static 파일을 'static'폴더에 모음
	3) python manage.py collectstatic 명령어로 static 파일 모음
	4) static 파일을 사용할 html 파일의 상단에 __{% load static %}__
	5) __{% static '파일이름' %}__으로 static 파일 사용






## Media
* 서버가 사진 파일을 보낼때 "사진의 url을 보냄"
* setting.py 수정
	``` MEDIA_ROOT = os.path.join(BASE_DIR, 'media') ```
	``` MEDIA_URL = '/media/' ```
* urls.py 수정
	* __+ static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)__
* models.py 수정
	* __image = models.ImageField(upload_to= 'blog/', blank = True, null = True)__ 추가
		* upload_to는 업로드할 폴더를 지정
		* setting.py에 MEDIA_URL로 지정해둔 media안에 blog 폴더를 만들어서 관리하겠다는 설정
	* models.py의 컬럼값을 변경할 때는 기존의 데이터들을 삭제 후 변경
* 이미지를 효과적으로 다루기 위한 패키지 설치
	* __pip install pillow__
* 새로운 글 작성 html(new.html) 수정
	* 사진을 올릴 수 있는 태그 생성
	* 예) < p>사진 : < input type="file" name="image">< /p>
	* form 태그 속성에서  파일을 같이 넘기기 위해서 인코딩파일 속성 추가
		* 예) < form action="{%url 'create'%}" method="post" enctype="multipart/form-data">
* view.py 수정
	* 새로운 블로그 만들 때 이미지도 생성해야하므로 수정
	* 예) new_blog.image = request.FILES['image']
* 저장된 글 확인 html (detail.html) 수정
	* < p>< img src="{{blog.image.url}}" alt="">< /p>
	* 사진이 없을 경우 에러를 없애기 위해 템플릿언어 추가
	* {%if blog.image%} < p>< img src="{{blog.image.url}}" alt="">< /p> {%endif%}






## Form
* form은 입력공간
* 장고에서는 forms.py를 통해 객체지향으로 접근 가능
	* 장점: 데이터베이스에 모델이 변할 때마다 각 파일 변경안해도 됨.
	* 유효성 검사 가능
* forms.py 생성
	```
	from django import forms
	from .models import Blog
	
	class BlogForm(forms.ModelForm):
    	class Meta:
        	model = Blog
        	fields = ['title', 'writer', 'body', 'image'] 
	```
	=> Meta 클래스는 Meta클래스의 정보를 가지고 BlogForm을 만들 것이라는 정보를 제공해주는 역할을 함.
* views.py
	* __from .forms import BlogForm__ 로 BlogForm 임포트
	* 새로운 블로그 객체를 만드는 함수(new())에서 BlogForm 객체 생성해서 전달
	* 예)  
	``` 
	from .forms import BlogForm
	...
	def new(request):
    form = BlogForm()
    return render(request, 'new.html', {'form':form}) 
	```
	* 새로운 블로그를 저장하는 함수(create())에서도 BlogForm 객체 사용하여 유효성 검사 실시하도록 수정
	* 예)
	```
	def create(request):
    form = BlogForm(request.POST, request.FILES)
    if form.is_valid():
        new_blog = form.save(commit=False)
        new_blog.pub_date = timezone.now()
        new_blog.save()
        return redirect('detail', new_blog.id)
    return redirect('home')
	```
	
	
	
	
## User확장과 인증
* 장고에서는 User 테이블 지원해줌.
* auth(Authentication): 장고에서 제공해주는 인증
	* 클라이언트가 회원가입 요청을 보내면 서버에서 user 테이블에 회원 정보 저장
	* 클라이언트가 로그인 요청을 보내면 서버는 user 테이블을 바탕으로 매칭이 맞으면 응답함.
	* auth 모듈
		* __authenticate()__
		* __login()__
		* __logout()__




## User확장과 인증(실습1)
* 로그인, 로그아웃, 회원가입을 관리하는 app(account) 생성 :
* setting.py에서 앱 등록
* views.py
	* __AuthenticationForm__: 로그인 폼
	* __UserChangeForm__: 회원가입 폼 임포트
	* 로그인 함수 login_view() 생성
	* 예)
	```
	def login_view(request):
    if request.method == 'POST':
        form = AuthenticationForm(request=request, data = request.POST)
        if form.is_valid():
            username = form.cleaned_data.get("username")
            password = form.cleaned_data.get("password")
            user = authenticate(request=request, username=username, password=password)
            # 로그인정보를 입력한 유저가 존재하는지 유효성 검사
            if user is not None:
                login(request, user)
            return redirect('home')
    else:
        form = AuthenticationForm()
        return render(request, 'login.html', {'form':form})
	```
	
	* 로그아웃 함수 logout_view()생성
	* 예)
	```
	def logout_view(request):
    logout(request)
    return redirect('home')
	```
	* urls.py에서 로그아웃 path 연결=> path('logout/', logout_view, name="logout"),
* 앱의 urls.py를 생성하여 login_view와 연결하고, 프로젝트의 urls.py에서 앱(account)의 urls.py로 연결시켜줌.





## User확장과 인증(실습2)
* views.py
	* 회원가입 함수 register_view()생성
	* 예)
	```
	def register_view(request):
    if request.method == "POST":
        form = UserCreationForm(request.POST)
        if form.is_valid():
            user = form.save()
            login(request, user)
        return redirect('home')
    else:
        form = UserCreationForm()
        return render(request, 'signup.html', {'form':form})
	```
	* urls.py에서 path('register/', register_view, name="signup") 추가

* user 확장
* models.py
	* 새로운 user 필드 생성
	* 예)
	```
	from django.contrib.auth.models import AbstractUser
	
	class CustomUser(AbstractUser):
    	nickname = models.CharField(max_length=100)
    	university = models.CharField(max_length=50)
    	location = models.CharField(max_length=200)
	```
* settings.py에서 인증받을 모델을 무엇으로 사용할 지 설정
	* AUTH_USER_MODEL = 'account.CustomUser'
	=> 'account.CustomUser'를 인증 모델로 사용하겠다고 설정
* forms.py
	* 새로운 폼 양식 생성
	* 예)
	```
	from django.contrib.auth.forms import UserCreationForm
	from .models import CustomUser
	class ResgisterForm(UserCreationForm):
    	class Meta:
        	model = CustomUser
        	fields = ['username', 'password', 'password2', 'nickname', 'location', 'university']
	```
* admin.py
	* 새로운 폼 양식 등록
	* 예)
	```
	from django.contrib import admin
	from .models import CustomUser
	
	admin.site.register(CustomUser)
	```




## Pagination
* 이용자와 글이 많아지면 관리하기 힘들기 때문에
* 장고에서는 블로그 객체를 잘라서 보내주는 paginator를 제공
* paginator가 블로그 객체를 잘라서 보내줌
	* get 방식 => localhost/?page=paginator.어떤페이지

* veiws.py
	* home함수 수정
	* 예)
	```
	from django.core.paginator import Paginator
	
	def home(request):
    	blogs = Blog.objects.all()
    	# paginator 객체 만듦
    	paginator = Paginator(blogs, 3)
    	# page: 현재 페이지
    	page = request.GET.get('page')
    	# blogs: paginator를 통해 새로 만든 블로그 객체 
    	blogs = paginator.get_page(page)
    	return render(request, 'home.html', {'blogs':blogs}
	```
* html 파일
	* paginator 이용
	* 예)
	```
	{% if blogs.has_previous %}
    <a href="?page=1">처음</a>
    <a href="?page={{blogs.previous_page_number}}"></a>
    {% endif %}
    
    <span>{{blogs.number}}</span>
    <span>of</span>
    <span>{{blogs.paginator.num_pages}}</span>
    
    {% if blogs.has_next %}
    <a href="?page={{blogs.next_page_number}}">다음</a>
    <a href="?page={{blogs.paginator.num_pages}}">마지막</a>
    {% endif %}
	```