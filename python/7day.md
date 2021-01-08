
# review

구글입사문제 8번

```
sum=0
for i in range(10001):
    sum+=str(i).count('8')
print(sum)
```



```
str(range(1,10001)) #이거 안됨
```

```
print(str(list(range(1,10001)))) #이건 됨
```



```
a =[1,2,3]
print(a[0]+10)
print(str(a[0]).count('1')) 
```

각각을 문자열로 바꾸는건 됨

a리스트를 한번에 통으로 str로 바꾸는건

```
a= str(a)
print(a[0]+str(10)) # 문자열 결합
```



# 파일 입출력

입출력 종류 : 표준, 파일, 네트워크

파일 입출력

-open() : 파일 열기 -> 파일 입(read)/출력 (write)  -> 파일닫기 (close)

 

```
f=open("hello.txt", )
#open(파일명, 모드)
```

모드 : 파일을 여는 목적 "w" : 파일을 쓰기 용도로 열기

프로그램 상에서는 쓰기 모드로 열려잇는 hello.txt.파일이 f라는 이름으로 사용됨

```
f.write('hello wolrd')
f.close() #메모리 때문에 닫아주기
```

```
s=f.read()
print(s)
f.close()
```



#with ~ as 구문은 파일을 사용한 뒤에 자동으로 파일을 닫아준다.

`with open('파일이름' , 모드) as 파일변수: `

​	코드



```
with open("hello.txt", "r") as f:
    s = f.read()
    print(s)
```

​	 

# 내용변경 

```
with open("hello.txt","w") as f:
    f.write("hello world 1")
```

w모드로 열게되면 기존에 작성되어 있던 내용은 사라짐

덮어쓰기가 되버린다.

```
with open("hello.txt","w") as f:
    for i in range(10):
        f.write("hello world {0}\n".format(i+1))
```



## writelines

```
lines=['안녕','반가워','잘지내']
with open("hello.txt","w") as f:
    f.writelines(lines)
```

리스트 쓸때 문자열 에러남 writelines 쓸것.

writelines : 한꺼번에 모든 줄 쓰기.



```
with open("hello.txt","r") as f:
    s=f.read() #read 함수는 1글자씩 읽어들임
    print(s)
```



```
with open("hello.txt","r") as f:
    
    s=f.readline() #readline 함수는 1줄씩 읽어들임(for 또는 while문과 함께 사용)
    
    print(s)
```



# readline()

```
with open("hello.txt","r") as f:
    line=None
    while line !="":
        line=f.readline() #readline 함수는 1줄씩 읽어들임(for 또는 while문과 함께 사용)
 
        print(line.strip("\n")) #\n을 삭제
```

줄단위로 읽어서 속도가 빠르다

strip() : 문자 지우기



# readlines()

```
with open("hello.txt","r") as f:
    print(f.readlines())
```

['hello\n', 'nice to meet you\n', 'bye\n']

리스트로 출력됨

readlines : 텍스트를 한꺼번에 모두 읽어옴



```
with open("hello.txt","r") as f:
    line = f.readlines()
    for i in line :
        print(i.strip("\n"))   #2줄씩 출력되서 빈 줄 지우기
```

hello
nice to meet you
bye



# 피클(pickle) 

: 파이썬 객체를 파일로 저장하고자 하는 경우에 사용되는 모듈

피클링 : 객체 -> 파일

언피클링 : 파일 -> 객체

```
import pickle

내용물 ="단팥"
색상="파랑"
너비="20센티"
높이="10센티"
가족명단={"잉어":30, "꽃게":10, "상어:40"}

#객체 저장할때는 wb 모드로 파일 열기
with open("myfish.p", "wb") as f:
    pickle.dump(내용물, f)
    pickle.dump(색상, f)
    pickle.dump(너비, f)
    pickle.dump(높이, f)
    pickle.dump(가족명단, f)
```

엑셀 쓸때도 저장할때 객체로 했음(xls, binary) 그래야 여니까



#읽는건 rb

```
with open("myfish.p", "rb") as f:
    내용물=pickle.load(f)
    색상=pickle.load(f)
    너비=pickle.load(f)
    높이=pickle.load(f)
    가족명단=pickle.load(f)

    print(내용물)
    print(색상)
    print(너비)
    print(높이)
    print(가족명단)
```

단팥
파랑
20센티
10센티

{'잉어': 30, '꽃게': 10, '상어': 40}



#순서 고대로여야 한다



```
f=open("hello.txt","a")
for i in range(3):
    f.write("%d번째 줄 추가\n" % (i+1))
f.close()
```

"a" : 계속계속 이어서 써짐!!  



# 클래스

클래스? 붕어빵기계

객체? 붕어빵

메서드(동작)? 굽는다, ... 뒤집는다, ...

attribute(속성)? 내용물, 크기, 모양, ... 너비, 높이

```

res=0
def add(n):
    #n에 전달된 값을 res에 저장
    global res
    res+=n
add(3)
print(res)
add(4)
print(res)

```

3

4



```

# #1번째 계산대
# res1=0 #전역변수
# res2=0
# def add1(n): #지역변수
#     global res1
#     res1+=n
#     #res=res*0.9
#     return res1
# print(add1(3000))
# print(add1(5000))
#
#
# #2번째 계산대
#
# def add2(n): #지역변수
#     global res2
#     res2+=n
#     return res2
# print(add2(1500))
# print(add2(2000))
```

3000

8000

1500

3500

여기까지가 클래스가 왜 필요한지 예시

-----



#클래스 : 각각의 계산대를 객체로 간주하고, 일반화된 계산대의 특성 또는 동작등을 일반화시켜 놓은 틀  



## 문법

```
class Calculator: #클래스명은 대문자로 시작
    def __init__(self):
        self.res =0
    def add(self, n): #3000원이 n으로 들어가쥬 self일단 무시
        self.res+=n
        return self.res

cal1=Calculator() #class로부터 객체를 생성하는 문장. 계산대(클래스)로부터 계산대1(객체)을 생성
cal2=Calculator()

print(cal1.add(3000))
print(cal1.add(5000))

print(cal2.add(1500))
print(cal2.add(2000))
```

3000
8000
1500
3500

계산기가 1000대로 생각해보면 class가 훨씬 간단함



```
class Calculator: #클래스명은 대문자로 시작
    def __init__(self):
        self.res =0
        print("init함수가 호출됐네?")
    def add(self, n):
        self.res+=n
        return self.res

cal1=Calculator()
cal2=Calculator()
print(cal1.add(3000))
print(cal1.add(5000))

print(cal2.add(1500))
print(cal2.add(2000))
```



init함수가 호출됐네?
init함수가 호출됐네?

부른적도 업는데 호출됨 --> 클래스로부터 객체를 생성할때 init 함수를 자동으로 호출함

cal1=Calculator()   <-- 얘네가 호출되는 순간!
cal2=Calculator() 



#Calculator() : 붕어빵기계에서 붕어빵을 제작 --> `__init__`자동호출 -> res(내용물) = msg



# 모듈

변수, 함수, 클래스 등을 모아 놓은 파이썬 파일. 다른 프로그램에서 모듈을 불러올 수 있음



```
#mod1.py

def madd(a,b):
    return a+b

def msub(a,b):
    return a-b
```



```
#day.py

import mod1 #모듈 다르면 불러와야함
print(mod1.madd(1,2))
```

3

```
import mod1 as m #as : 모듈(패키지)명이 길때 축약해서 표현
print(m.madd(1,2))
```

3



폴더안에 파일/서브폴더 있으니까 `import 폴더.하위폴더 as 이름` 요런식으로 쓴다



`import 모듈이름 ` 확장자는 안쓴다!!



 

```
from mod1 import msub
#mod1 모듈에 정의되어 있는 msub 메서드만 가져와라
print(msub(2,1))
```

from 사용

`from mod1 import madd,msub` 도 된다~

`from mod1 import *`: 모든 함수 다 가져옴





```
#mod1.py
def madd(a,b):
    return a+b

def msub(a,b):
    return a-b

if __name__=="__main__":
    print(madd(3,2)) #5
    print(msub(10,3)) #7
```

5

7

mod1.py를 실행시키면 `__name__`이라는 특별한 속성 값으로 `__main__`이 저장됨.

따라서 `if __name__=="__main__":`  조건식이 참이됨

그래서 아래꺼 실행해서 5,7 나옴



```
#modtest.py
import mod1
#import를 하는 순간 mod1이 실행됨됨

print(mod1.madd(3,5))
```

8

```
else:
    print("__name__값 : ",__name__)
```

else추가해 놓고 test 파일 돌리면

__name__값 :  mod1

 











