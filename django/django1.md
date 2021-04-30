# 장고

개발시간 단축, 완성도 올라가는 장고서버



웹프레임워크 까다로움



접속자들은 DBMS를 통해 DB와 통신한다. 자료를 검색,추가,삭제,갱신 할 수 있다.



파이썬 설치되어있어야함

0.1파이썬 가상환경 설치

-가상 환경 : 프로젝트를 독립적으로 수행하기 위해 사용

ex) 개발 프로젝트가 2개 있는 경우 (2개가 버전이 다르면 버전이 둘다 깔려야있어야함) -> 개발하기 어려워진다. 

-> 파이썬 가상환경 사용시 하나으 컴퓨터에 2개 이상의 독립된 가상환경을 만들수 있음

프로젝트 A의 가상환경 P1, 프로젝트 b의 가상환경 P2 



설치

1. cmd 

2. `cd\`

3. `mkdir venvs` (가상 환경을 위한 디렉토리 생성)

4. `cd venvs`

5.  `python -m venv`

6. `cd my* `my로 시작하는 폴더로 이동

7. `cd Scr*`

8. `activate` 가상환경으로 들어가 <->deactivate

   프로젝트(웹사이트 단위) 디렉토리 생성



장고 웹 서버 구동
1. C:\venvs\mysite\Scripts\activate

   (밑으로 한칸한칸 기어나가서..)

2. (mysite) C:\project\mysite\config>cd..

3. (mysite) C:\project\mysite>python manage.py runserver



파일 등록해놔서 cmd 키고 mysite 치면 어디서든 가상환경으로 바로 이동

python manage.py runserver   // 웹서버 구동

Ctrl + c //서버 죽이기



## 게시판 만들기

(mysite) c:\project\mysite>django-admin startapp mybo

`mybo` 추가하고 싶은 app의 이름

 http://127.0.0.1:8000/가 mysite의 주소. mybo는 그안에 들어 가있음

http://127.0.0.1:8000/mybo 게시판 주소가 된다. 

페이지 요청 -> config 폴더 안에 있는 urls.py 를 열게된다

```
from mybo import views
```



views.py에서

```
def index(request):
    return HttpResponse("안녕하세요. 제가 만든 홈페이지에 오신것을 환영합니다")
```











