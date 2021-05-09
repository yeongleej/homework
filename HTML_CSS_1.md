# <HTML & CSS>
## Intro
* __프로그램 코드(Program code)__: 컴퓨터 프로그램을 프로그래밍 언어로 작성한 글
* __프로그래밍(Programing)__:  코드를 작성하는 행위
* __프로그래밍 언어(Programing Language)__: 컴퓨터에 명령 내리기 위한 언어
	* C, java, java Script 등등


###### HTML / CSS, Javascript
* __HTML__: Hyper Text Markup Language
	* Hyper Text : 하이퍼링크를 통해서 독자가 원하는 순서로 다른 문서로 접근할 수 있는 텍스트
	* Markup Language: 태그(마크, 표시)를 이용하여 문서나 데이터 구조를 명시하는 언어
	=> __웹 페이지의 구조 혹은 데이터 작성을 위한 마크업 언어__
* __CSS__: Cascating Style Sheets
	* Style Sheets: 웹 페이지의 스타일(문자크기, 색상 등등)과 관련된 모든 것을 정해둠
	* Cascading: 우선순위를 가지고 적용
	=> __웹 페이지에 관한 다양한 스타일 들을 정의__
* __Javascript__: 웹을 이용하는 유저와 상호작용 하기 위한 기능을 추가할 때 쓰는 언어
	* 유일안 프로그래밍 언어(HTML, CSS는 프로그래밍언어 X)
* HTML: 구조(structure)를 담당
* CSS: 스타일(style)을 담당
* Javascript: 동작(behaviors)을 담당





## HTML 기초

###### HTML 기초 문법(요소와 태그)
* __HTML 요소__
	* <시작태그> 내용 </종료태그>
	* 태그는 소문자로 권장
	 예) <h1> 웹 프로그래밍 강좌 </h1>
	* __태그__: 내용을 나누고 어떤 역할을 하는지 구조를 정의
	* __시작 태그__: 컨텐츠의 시작을 표시
	* __종료 태그__: 컨텐츠의 끝을 표시
	* HTML을 통해서 컨텐츠를 구조화함



###### HTML 문서 구조
* 브라우저: 인터넷을 사용하기 위한 도구
	
	* 크롬, 익스플로러, 파이어폭스 등
* __<!DOCTYPE html>__ : 문서 형식을 정의
* <html lang = "kr">: html을 감싸는 태그, 본격정인 태그의 시작으로 사용하는 주 언어를 정의
	
	* 주의: html 문서안에서 한 번만 써야함. 또한 html태그 밖에 다른 태그가 존재해서도 안됨
	* lang = "kr": 해당 페이지의 주 언어를 한국어로 정함
* <head></head>: html 문서에 대한 정보를 가짐
	* html 문서에서 한 번만 써야함
	* <meta charset="utf-8">: 문서와 관련된 정보를 담음
	* <title></title>: 웹 페이지의 제목을 담음
* <body></body>: html 문서에 보여지는 부분
	* html 문서에서 한 번만 써야함.
	* 위치는 head태그 아래
	* 단, head태그와 body태그 안의 태그들은 여러번 쓸 수 있음



###### 레이아웃과 관련된 기본 태그
* 시맨틱 태그(Semantic tag): 의미를 가지고 있는 태그
* header: 웹 페이지 혹은 section의 소개나 제목을 담기 위해 사용하는 요소
* nv: 네비게이션 역할을 하는 요소, 페이지 이동을 위한 메뉴를 담고 있음
* section: 기준에 따라 구획을 구분하기 위해 사용하는 요소
* article: 주 내용을 담기 위해 사용하는 요소
* aside: 광고나 사이트의 주변 부분에 해당하는 내용을 담기 위해 사용하는 요소
* footer: 웹 사이트의 가장 아래에 들어가는 회사 정보 등의 추가 정보를 담기 위해 사용하는 요소







## 텍스트와 관련된 태그

* __제목 태그__: 제목을 나타내고 싶을 때 사용
	
	* 중요도에 따라 1~6까지 씀 (h1이 가장 중요)
* 태그를 감싸지 않고 body태그 안에 작성한 텍스트는 태그로 감싼 텍스트와 동일하게 보임 단, 되도록이면 태그로 감싸기
* __본문 태그__:
	* < p>< /p>: paragraphs(단락, 문단)
	* hmtl에서 엔터(enter)는 스페이스바 하나로 인식
	* <br>: break, 줄바꿈
		
		* <br>은 종료 태그를 사용하지 않음
		* __빈 요소(Empty element)__: 종료 태그를 사용하지 않는 요소 즉, 태그 사이가  비어있음을 의미 (예: <br>, <img> 등등)
	* <pre></pre>: preformated(형식화된), 코드에 작성한 형식대로 화면에 출력
	* 글자와 관련된 태그
		* <strong></strong>: 굵은 글씨체
		* <em></em>: italic체 
		* <sub></sub>: 일반 위치보다 위로 올림 (예: 로그, 지수표현)
		* <sup></sup>: 일반 위치 보다 아래로 내림
		* <ins></ins>: 단어나 문장아래에 밑줄추가
		* <del></de>: 단어나 문장에 취소선 추가







## 링크 태그

##### <a></a>: 링크 태그
* __속성(Attributes)__:  태그에 대한 추가적인 정보 제공
	* 시작 태그의 바로 뒤에 들어감
	* HTML 의 모든 태그는 속성을 가질 수 있음
	* 형태: < a __키 = "값"__> 
	* 두 가지 이상의 속성을 사용할 때는 띄어쓰기로 구분
* __href__: 연결할 웹 사이트 주소를 가짐, a태그의 필수적인 속성

* * __경로(path)__: 지나는 길
	* / 이용
* __주소(Address) + 경로(Path) => URL(Uniform Resource Locator)__
* __URL__: 인터넷에서 HTML페이지, CSS문서, 이미지등 자원(resource)의 위치를 나타냄
	* 절대 URL(Absolute URL): 접근하는 최초 시작점부터 경유한 경로를 모두 기록하여 리소스의 위치를 나타냄
	* 상태 URL(Relative URL): 기준점을 기준으로 상대적인 경로를 기록하여 리소스의 위치를 나타냄

* __target__ 속성: 클릭으로 링크를 열 때 어디에 오픈 할 것인지 정하는 속성
	* target="___self__": 현재 탭에서 링크를 여는 속성
	* target="___blank__": 새 탭(창)에서 링크를 여는 속성








## 멀티미디어와 관련된 태그

###### 이미지 태그
* <img>: 이미지 태그
	* __src="이미지 URL"__: 불러올 이미지의 URL을 속성 값으로 가짐
	* src는 source의 약자
	* __alt="사진 설명"__: 불러올 이미지가 없거나 불러오는데 실패했을 경우 대신 표시되는 문장, alternative text(대체문구)의 약자
	* __weight="수치"__: 이미지의 너비를 지정할 때 쓰는 속성
	* __height="수치"__: 이미지의 높이를 지정할 때 쓰는 속성
		* 이미지 크기는 CSS에서 조정하기 권장
* < video>< /video>: 비디오 태그
* < audio>< /audio>: 오디오 태그
* 유튜브 영상 넣기: 유튜브 공유 -> 동영상 퍼가기 -> 코드 복사 붙여넣기
	* <ifram></ifram>이용
	* 동영상 url 중 영상 ID부분을 이용하여 원하는 영상 가져올 수 있음





## 테이블과 리스트

###### 테이블의 구성
* 표(table) 
	* <table></table>: 표 전체를 감싸는 태그
	* <tr></tr>: 표에서 행을 구분하는 태그
	* <th></th>: 표의 행 내부에 제목 셀을 담는 태그
	* <td></td>: 표의 행 내부에 데이터 셀을 담는 태그
	```
	<table>
		<tr>
			<th></th>...
		</tr>
		<tr>
			<td></td>...
		</tr>
	</table>
	```
	
	* __rowspan="숫자"__: "숫자"만큼 셀이 행을 점유
	* __colspan="숫자"__: "숫자"만큼 셀이 열을 점유


###### 목록
* 목록(List)
	* __순서 없는 목록(Unordered List)__
		* 아이템1
		* 아이템2
		* 아이템 3
		```
		<ul>
			<li>아이템1</li>
			<li>아이템2</li>
			<li>아이템3</li>
		</ul>
		```

	* __순서 있는 목록(Ordered List)__
		1.아이템1
		2.아이템2
		3.아이템3
		```
		<ol>
			<li>아이템1</li>
			<li>아이템2</li>
			<li>아이템3</li>
		<ol>
		```
	* 리스트는 기본적으로 들여쓰기가 포함됨
	* 리스트는 서로 중첩이 가능함


###### 목록과 관련 있는 속성
* 순서있는 목록
	
	ur태그 속성
	* __start="숫자"__: 리스트가 시작하는 숫자를 정함
	* __type="문자"__: 순서를 시작하는 문자를 정함(예: a,b,c...)
	* __reversed__: 순서를 반대로 시작, 다른 속성과 달리 키(key)만 써서 사용
	
	li태그 속성
	* __value="숫자"__: 해당하는 리스트 아이템의 번호를 지정
		* value를 쓰고난 이후부터 숫자가 매겨지는 점 유의






## 폼 태그

###### form
* < form> < /form>: 폼에 포함되는 다양한 입력 양식 태그들을 감싸줌
	* __action__: 데이터를 보낼 URL을 지정
	* __method__: 보내는 방식을 지정
		* method="get"  => header(url)부분끝에 데이터를 붙여 눈에 보이게 보냄
			* GET방식 특징: 데이터 조회 만을 목적으로 할 때 주로 쓰임(예: 검색)
		* method="post"  => 데이터를 url에 적지 않고 내부(body)에 숨겨서 보냄
			* POST방식 특징:  서버에 있는 데이터를 쓰거나 수정, 삭제 할 때 주로 사용(예: 게시물 작성, 로그인 등)


* < input>: 사용자에게 입력을 받기 위해 사용 되는 태그, 빈 태그
	* __type="text"__: < input>태그의 종류를 결정
	* __name="id"__: < input>태그 중 같은 타입과 구분되는 이름을 결정
	* __placeholder="아이디를입력하세요"__: input에 아무 값도 입력 되지 않았을 때 나타나는 텍스트
	* __value="soonho"__: 실제 할당되는 값, 우리가 데이터를 넣으면 이 속성에 값이 들어감(초기값처럼 둘 수 있음)
* < label>< /label>: 해당하는 라벨 클릭 시 < input>태그가 활성화됨
	__for="input태그의 id"__
	* 페이지에서 label을 누르면 input 태그 활성화됨
* < div>< /div>: 태그들을 구분 짓고 나누기 위해 사용되는 태그, division의 약자


* < select>< /select>: 여러 개의 선택지를 제시하고 싶을 때 씀
	* __name="gender"__: < input>태그의 name속성과 동일하게 작동
		* < select>태그는 name속성 반드시 가져야함
	* < option>< /option>
		* __value="male"__: < input>태그에서 입력한 값과 동일한 역할

* < textarea>< /textarea>: 한 번에 많은 글을 입력 받을 때 사용
	* __id="input태그의 id"__
	* __cols="숫자"__: 글자 수는 "숫자"
	* __rows="숫자"__: 글의 줄 수는 "숫자"

* < button>< /button>: < input>태그의 버튼타입과 동일하게 버튼 생성





## CSS 기초
#### CSS(Cascading Style Sheet)
* Style Sheet: 스타일 명세서
* __선택자(Selector)__: 스타일을 적용하고자 하는 HTML요소를 선택하는 역할
	* 예)  __p__{}
	* {} => 선언블록(Declaration block), 중괄호로 다음 선언블록과 구분
* __속성(Property)__: 지정한 스타일의 속성명에 해당
	* __속성: 값;__이 한 단위 => 이 쌍을 선언(Declaration)이라고함.
	* ;(세미콜론)을 이용하여 구분
* __값(Value)__: 키워드나 특정 단위를 이용하여 원하는 스타일을 적용
	* 속성(property)와 쌍을 이룸


#### HTML에 CSS 적용
1. Link Style: HTML에 외부에 있는 CSS파일을 불러옴
2. Embedding Style: HTML의 <head>에 <style>를 이용하여 CSS 작성
3. Inline Style: HTML요소에 직접 Style 속성(Attributes)을 이용하여  CSS를 작성






## 선택자
#### 선택자 기초
* 일반적인 태그: h1, p, span, div, a 등등
* 선택자(Selector): 스타일을 적용하고자 하는 HTML요소를 선택하는 역할
* 여러개의 선택자를 ,(콤마)를 이용하여 스타일을 한번에 지정 가능
	* 예) h1, p, td {}


#### 단순 선택자
* __타입 선택자(Type Selector)__: 해당 태그를 가지는 모든 요소에 스타일을 적용
	* 예) p {color: red;} => <p>태그를 가지는 모든 요소 red로 적용
* __아이디 선택자(Id Selector)__: Id로 스타일을 적용, 해당 Id 하나에 적용(Id는 단 하나)
	* 아이디(Id): HTML문서 내에서 동일한 아이디는 존재할 수 없음, 다른 요소와 구분되는 점을 만들어줌 
	* __#(아이디) {}__  로 적용
* __클래스 선택자(Class Selector)__: 클래스 이름으로 스타일을 적용, 같은 클래스 이름이면 모두 적용
	* 클래스(Class): 비슷한 특징을 갖는 요소를 지정하여 묶을 수 있음, 여러 번 사용 가능
	* __.(클래스 이름) {}__  로 적용
* __전체 선택자(Universal Selector)__: 모든 요소에 스타일을 적용, 모든 요소에 적용하기 때문에 속도 저하 가능성 있음.
	* __* {}__ 로 적용
* __속성 선택자(Attribute Selector)__: 특정 속성을 소유하는 모든 요소에 스타일을 적용
	* __선택자[속성명="속성값"] {}__ 로 적용
	* 예) a[target="blank"]{color:red;} => <a>태그의 target속성의 값이 "blank"인 태그들의 요소를 red로 적용
* __복합 선택자__
	* 부모 <- 나 -> 자식
	```
	<section>				// 부모
		<article>			// 나
			<div></div>		// 자식
			<div></div>
				<p></p>		// 후손	
		</article>
	</section>
	```
	* 자식(Child) 요소: 해당 태그 바로 아래의 요소들
	* 후손(Descendant) 요소: 해당 태그 아래의 모든 요소들
	<img src = "C:\Users\xzba1\Desktop\likelion\HTML_CSS\복합선택자.png">
	* __자식 선택자(Child Selector)__: 선택자A의 모든 자식 중 선택자B와 일치하는 요소 선택
		* __선택자A > 선택자B {}__ 로 적용
		* 예) article > p {color:red;} => article태그의 자식 중 p태그만 red로
	* __후손 선택자(Descendant Selector)__: 선택자A의 모든 후손 중 선택자B와 일치하는 요소 선택
		* __선택자A 선택자B {}__ 로 적용(띄어쓰기로 구분)
		* 예) article p {color:red;} => article태그의 후손 중 p 태그만 red
* __pseudo 클래스 선택자__: 요소의 특별한 상태를 지정할 때 씀
	* __선택자:pesudo-class {}__ 로 적용
	* pseudo(가상의) => pseudo-class(가상의 클래스)
	* :link => 방문하지 않은 링크일 경우
	* :visited => 방문한 링크일 경우
	* :hover => 요소에 마우스가 올라와 있을 경우





## 값과 단위
#### 숫자값과 백분율
* CSS 값의 종류: 숫자값, 키워드, 색 등등
* 숫자값
	* 보통 글자의 크기(Font-size)를 숫자값으로 조정
	* 단위
		* __px(픽셀)__: 화소로, 디스플레이를 구성하는 최소 단위
			* 1px은 장치의 해상도에 따라 다른 크기를 갖기 때문에 
			* 브라우저에서는 1px = 1/96 in(인치) => 절대크기
		* em, rem => 상대적인 길이
		* __em__: 현재 스타일이 지정된 요소의 font-size기준
		* __rem__: 최상위 요소의 font-size기준
		* __1em(1rem) = 기준 font-size * 1em(1rem)__
			* 예) 10em(10rem) = 16px * 10 = 160px
		* em과 rem은 크기가 다양한 브라우저 환경에서 상대적으로 크기를 조정할 수 있기 때문에 절대적인 px보다 유용 (그러나 em은 상속의 문제가 있기 때문에 rem을 쓰는 것을 권장)
		* __%(퍼센트)__: 상대 길이, 보통 이미지나 레이아웃의 너비나 높이를 지정할 때 씀.
* 색상
	* 키워드로 표현: blue; orange; 예) color:blue;
	* __hex code__: #000000; #ffffff; 등등 예) background-color:#ffffff;
		* 투명도 설정 => #000000 + 50(숫자) : 예) #00000050;
	* __rgb__: rgb(255, 0, 0); 예) color: rgb(255, 2, 0);
		* 투명도 설정 => rgb(255, 255, 0, .5(실수))






## 텍스트와 관련된 프로퍼티

#### 폰트
* __font-size__
* __font-family__: 폰트의 종류를 정의, 폰트를 여러개 정의(앞에서 부터 실행, 마지막에는 항상 일반 폰트 작성)
	* 폰트 파일, 웹 폰트로도 적용 가능(링크태그 이용)
	* 한 폰트만 정의할 때는 따옴표 필요 없지만, 여러 폰트를 정의하는 경우 따옴표 필요
* __font-style__: Italic체 또는 BOLD
	* normal: 기본 폰트
	* italic: Italic체가 디자인이 되어있는 경우 Italic체로 표현
	* oblique: 글자를 기울여서 표현
	* 예) font-style:oblique;
* __font-weight__: 폰트 굵기를 지정
	* bold
	* 100 ~ 900까지의 수: 100 ... 400(normal)...700(bold)...900


* __font__ 로 한 번에 모두 적용 가능
	* 예)
	```
	<style>
		#main { 
			font: oblique 900 35px '고딕', sans-se
		}
	</style>
	```
	
	
#### 텍스트 정렬과 관련된 속성
* __text-align__: 텍스트를 좌,우,중앙 정렬함
	* left / center / right
	* 각 요소(자기자신, 웹 브라우저(X))를 기준으로 정렬됨
* __line-height__: 문장 사이의 간결을 조정함
	* 단위 / 숫자 등으로 표현
	<img src="C:\Users\xzba1\Desktop\likelion\HTML_CSS\line-height.png">
* __letter-spacing__: 글자와 글자 사이의 간격을 조정함, 자간
* __text-indent__: 문단의 시작부에 들여쓰기를 함





## 박스 모델
#### 박스 모델 개념
* 박스 형태의 크기를 조정하여 브라우저 상에 올바르게 배치할 수 있음
* __Box Model__
	* Content(내용): 실제 내용
	* Border(경계선): content를 감싸고 있는 테두리
		* border-style: dashed / solid / dotted / double 등등 
			* 1개 => 4면이 적용
			* 2개 => 상하/좌우 적용
			* 3개 => 상/좌우/하 적용
			* 4개 => 상/하/좌/우 적용
		* border-width: 경계선 두께
		* border-color: 경계선 색상
		* __border__ 만으로 모두 표현 가능
		* 예) border: 4px solid blue;
		* border-radius: 경계선을 둥글게 표현 가능
			* 예) border-radius: 12px;은 모서리의 반지름이 12px
			* border-top-left-radius / border-top-right-radius / border-bottom-left-radius / border-bottom-right-radius의 네 방향을 적용 가능
			* border-top-left-radius: 10px 30px 과 같이 타원형으로도 적용 가능
	* Padding(패딩): content와 Border사이의 여백
	* Margin(마진): Border밖의 여백
		* Margin과 Padding 모두 네 방향(상하좌우)을 따로 적용 가능
		* 주의> 위 아래 다른 요소에서 Margin을 적용하면 두 Margin이 공존하지 않고,
		* CSS의 __마진 상쇄(Margin Collapse)__에 의해 마진이 작은 쪽은 상쇄되고 마진이 큰 쪽을 따라가게 됨.
	* box-sizing: 박스의 크기 조정
		* 기본값: content-box;
			* box-sizing: content-box; => width(height) == content size
		* border-box; => border를 포함해 박스 사이즈 정함
			* box-sizing: border-box; => width(height) == content size + padding + border 





## 위치와 관련된 프로퍼티[1]
#### dispaly: 요소가 보여지는 방식을 지정하는 프로퍼티
* HTML요소를 dispaly:block의 block요소와 display:inline의 inline요소로 나눌 수 있음
* __block 요소__ 
* width를 기본 100%로 가짐 => 항상 새로운 줄에서 시작
=> <div>, <h1>~<h6>, <p>, <header>, <section> 등등
* __width, height, margin, padding__ 지정 가능
	
* __inline 요소__
* 필요한 만큼의 너비(width)만 가짐 => 요소의 content크기 만큼만 너비를 가짐
=> <a>, <span>, <img> 등등 
* __width, height, margin-top, margin-bottom__ 지정 불가능
	*__dispaly: inline-block;__: block요소와 inline요소의 특징을 모두 가지고 있음.
	* __width, height, margin-top, margin-bottom__지정 가능
* __dispaly:none;__: 브라우저에 해당 요소 출력 X

#### position: 요소의 위치를 정의
* __position:static;__: 기본값으로 좌표 프로퍼티를 쓸 수 없음
* __position:relative;__: 상대 위치로 기본 위치를 기준으로 좌표를 사용함
* __position:absolute;__: 부모나 조상 중 relative, absolute, fixed가  선언된 곳을 기준으로 좌표 프로퍼티 적용
* __position:fixed;__: fixed는 보이는 화면을 기준으로 좌표 프로퍼티를 이용하여 위치를 고정
	* 고정한 상태에서 스크롤을 이동해도 브라우저 화면에 고정됨
* __z-index__: 숫자로 우선 순위 지정

	



## 위치와 관련된 프로퍼티[2]
#### flexbox
* flex container(부모요소) + flex item(자식요소) 로 구성
	* 정렬하고자 하는 부모요소에 __display:flex;__를 추가 해줌 (이때 이를 추가한 요소가 flex container, 자식요소가 flex item이 됨. 또한 추가해주지 않으면 flexbox 사용할 수 없음)
* flexbox의 핵심 => "가로" or "세로"의 정해진 방향으로 프로퍼티 정렬

* __flex container(부모요소)__

  * __flex-direction__: flex 컨테이너 안의 item들의 방향을 정함
  	* flex-direction: row; => 기본값으로, 왼쪽에서 오른쪽(->)으로 정렬
  	* flex-direction: row-reverse; => 오른쪽에서 왼쪽으로(<-)으로 정렬
  	* flex-direction: column; => 위에서부터 아래로 정렬
  	* flex-direction: column-reverse; => 아래에서부터 위로 정렬
  * __flex-wrap__: flex 아이템이 flex 컨테이너를 벗어 났을 때 줄을 바꾸는 속성
  	* flex-wrap:nowrap; => 기본값으로, 줄을 바꿔주지 않음
  	* flex-wrap:wrap; => 컨테이너를 벗어 났을 때 줄을 바꿔줌
  * __flex-flow__: flex direction과 wrap을 동시에 지정 가능
  	* 예) flex-flow: row wrap; 
  * __justify-content__: flex-direction으로 정해진 방향을 기준으로 수평으로 item을 정렬하는 방법을 정함
  	* row일 때는, 좌우(<->)방향이 수평방향
  	* column일 때는, 상하방향이 수평방향 
  	* 그냥 정렬방향과 동일하다고 생각
  	* justify-content: space-around; => 아이템을 기준으로 아이템간의 간격을 동일한 간격으로 설정
  	* justify-content: space-between; => 양끝의 아이템을 가장자리로 정렬한 뒤 사이 아이템들의 간격을 동일하게 설정 
  * __align-items__: flex-direction으로 정해진 방향을 기준으로 수직으로 item을 정렬하는 방법을 정함
  	* row일 때는, 상하방향이 수직방향
  	* column일 때는, 좌우(<->)방향이 수직방향
  	* align-items: stretch;(기본값)
  	* align-items: flex-start; => 시작부분 부터
  	* align-items: flex-end; => 끝부분 부터
  	* align-items: center; => 중앙부분 부터
  	* __align-items: baseline;__ => 아이템의 글꼴의 기준선이 baseline부터 정렬
  * __ailgn-content__: flex-direction으로 정해진 방향을 기준으로 수직으로 여러 줄인 아이템을 정렬하는 방법을 정함


* __flex item(자식요소)__
	* __flex-grow__: flex 아이템의 확장과 관련된 속성, 기본 0
		* 값이 0이면 컨테이너의 크기가 커져도 아이템의 크기는 변경 X
	* __flex-shrink__: flex 아이템의 축소와 관련된 속성, 기본 1
		* 값이 0이면 컨테이너의 크기가 작아져도 아이템 크기 변경 X
		
		* 1이상이면 컨테이너크기 만큼 축소
		  *__flex-basis__: flex 아이템의 기본 크기를 결정함, 기본 auto
		
		* 단위를 같이 써줘야함 (10px, 10% 등등)
	* __felx__ => flex-grow, flex-shrink, felx-basis를 한 번에 적용






## 상속과 우선순위
#### 상속
* 상속은 부모나 조상요소에 적용된 CSS 프로퍼티가 자식이나 후손에 적용되는 것
* 모든 CSS 프로퍼티가 상속되는 것은 아님
	* margin: inherit; => 상속이 되진 않는 프로퍼티를 상속할 때 선언

#### 우선순위(Cascading)
* 규칙
	* __중요도__: CSS가 어디에 선언되었는 지에 따라 우선순위가 달라짐
		1. <head>태그 내의 <sytle>태그
		2. <head>태그 내의 <style>태그 내의 @import문
		3. <link>태그로 연결된 CSS
		4. <link>태그로 연결된 CSS 내의 @import
		5. 문브라우저 디폴트 스타일시트 
		
	* __명시도__
		1. !important => 프로퍼티와 값을 쓰고 세미콜론을 찍기전에 작성(가장 우선순위 높음)
		2. 인라인 스타일(inline sytle)
		3. 아이디 선택자(id selector)
		4. 클래스, 속성, 가상클래스 선택자
		5. 태그 선택자
		6. 전체 선택자
		7. 상속(inherit)
		
	* __선언순서__: 같은 우선순위를 가진 경우, 나중에 선언된 스타일이 우선 적용








## Bootstrap
* 중복된 코드를 줄이고 효과적으로 쉽고 빠르게 웹을 생성할 수 있는 오픈소스 프로그램
* 부트스트랩의 CSS(<head>태그에)와 JS(<body>태그에)의 코드 복사 붙여넣기
* 부트스트랩에서 정해둔 클래스이름을 적기만 하면 CSS 적용
* 그리드 시스템
	<img src = "\부트스트랩_그리드시스템.png">

	* 그리드 옵션을 이용해 반응형 웹 만들 수 있음
	* .col-lg-4
	=> lg: 기준이 되는 화면 사이즈
	=> 4: 12등분 중 차지할 비율
