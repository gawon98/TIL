# 세번째 날

파이썬은 day2.



```
s ="파이썬파이썬파이썬"
print(s[::3]) #offset x칸씩 건너뜀 
```

출력 파파파

양수(좌->우), 음수(우->좌)

```
print(s[::-1])
```

문자열 뒤집기 가능



## replace

문자열 치환

`tel.` 목록창 ctrl + space

```
tep.replace(from,to)
```

~을 ~으로 인수꼴

```
tel.replace("-","")
```

뒤에꺼 : 없애라. 공백문자도 없이



```
s ="Life is too short"
print(s.replace("Life", "your leg"))
```

출력 : your leg is too short



```
print(1,2,3, sep="&") #1&2&3
```

구분자



## is



```
a=1
b=1
print(a == b) # ==는 두 값이 같은지 비교
print(a is b) # is는 두 객체(주소가 동일한지) 비교

print(1==1.0)
print(1 is 1.0) #is는 두 객체가 같은지 비교. 1은 정수객체, 1.0은 실수객체
```



## 논리연산자

```
print(True and False)
print(False or False)
print(not False) 

print(1==1 and 2!=1) #T
print(3>1 or 1<2) #T
print(not 1>2) #T
```



### 불 대수

```
print(bool(1)) #T
print(bool(0))#F
print(bool(0.5)) #T
print(bool('test')) #문자열도 True
print(bool('')) # 빈문자열은 F

print(bool(0 or 'test')) # T

```

0 : false , 1: true , 0이 아닌 모든 수가 True



## 정렬

### 공간확보

```
print("%10s" % "hi") #전체10자리 확보, 앞에8자리 공란
```

​        hi

```
print("hello%10s" % "hi") 
```

hello        hi



```
print("%-10shello" % "hi")
```

-붙어서 왼쪽 정렬 

hi        hello



```
print("%.4f" % 3.141592)#3.1416
```

.4f : 소수이하 5째 자리에서 반올림 -> 4째 자리까지 표현

```
print("%10.4f" % 3.141592) #    3.1416
```

10자리 확보한 다음 출력 (우측 맞춤)



```
print("{0}".format("hi"))
print("{0:<10}".format("hi")) #10자리 확보 후 왼쪽정렬
print("{0:>10}".format("hi")) #10자리 확보 후 오른쪽정렬
print("{0:^10}".format("hi")) #10자리 확보 후 가운데정렬
```

hi
hi        
        hi
    hi    

```
print("{0}".format("hi"))
print("{0:-<10}".format("hi")) #10자리 확보 후 왼쪽정렬
print("{0:->10}".format("hi")) #10자리 확보 후 오른쪽정렬
print("{0:-^10}".format("hi")) #10자리 확보 후 가운데정렬
```

문자 넣으면 채워줌

hi
hi--------
--------hi
----hi----

```
print('python'.ljust(10)) #10자리 확보 후 좌측정렬
print('python'.rjust(10))#10자리 확보 후 우측정렬
print('python'.center(10))#10자리 확보 후 가운데정렬
```

## format

```
num=3
print("i eat %d apples" % num)
print("i eat {0} apples".format(num))
```

위아래 같은 방법 , 문자도 됨

```
s="two"
print("i eat %s apples" % s)
print("i eat {0} apples".format(s))
```

장점 자료형 신경 안써도 됨

출력하고자 하는 값이 한개면 0 ,+...

```
s="two"
day = "three"

print("i ate {0} eggs. so i was sick for {1} days.".format(s,day))
```

i ate two eggs. so i was sick for three days.

1이 먼저와도 상관없음

```
print("i ate {num} eggs. so i was sick for {day} days.".format(num=5 , day=3))
```

직접 대입 가능

* 일반적으로 많이 쓰는 표현이 아님

  

## 함수



* 내장함수 : 프로그램에 기본적으로 내장되는 함수(print)

* 외장함수 : 별도로 적재해야하는 함수 random()

```
import random
print(random.random()) #모듈명,함수명()
```



### count - 문자열함수

```
a="hello"
print(a.count('l'))
```

count : a에서 l 문제 갯수?

### find

```
print(a.find('l')) #위치 :2 , 여러개 있는 경우 맨 앞
print(a.find('x')) #없을때 -1
```



```
print("apple pineapple".find('p'))
print("apple pineapple".find('pp'))

print("apple pineapple".rfind('p'))
print("apple pineapple".rfind('pp'))
```

1
1
12
11

rfind는 뒤에서부터 찾는데 index숫자는 앞에서부터 세는 것 기준



### index

```
print(a.index('l')) #2 , 위치
print(a.index('x')) #없을때 error 출력
```

### join

```
print(",".join("abcd")) #문자열 삽입
print(",".join(['a','b','c','d'])) # a,b,c,d
print("".join(['a','b','c','d'])) #abcd
```

리스트에 저장되어 있는 각각의 문자들이 컴마와 결합하여 하나의 문자열("a,b,c,d")이 된다.

### 대문자 소문자

```
a ="hi"
print(a.upper()) #대문자
print(a.lower())
```

바뀐거 저장`a=a.upper()`

자동완성은 Tab

### strip

```
n1 = "  대한민국"
n2 ="대한민국   "
print(n1.lstrip()) #왼
print(n2.rstrip()) #오

n3 ="  대한민국  "
print(n3.strip()) # 양쪽
```

공백 지우기

### split

```
s ="Life is too short"
print(s.split()) #공백문자로 분리
```

['Life', 'is', 'too', 'short']  <-리스트 형태로 분리



+ 함수 앞에 m은 method(=function) c는 class

### maketrans & translate

```
t=str.maketrans('aeiou','12345')
print('apple'.translate(t)) # 1ppl2 , apple 문자열을 t변환 테이블을 참조하여 변환하세요
```

str.maketrans('바꿀문자','새문자') 작성하여 변환테이블(t) 생성 



### string (외장)

```
str = ", python,."
print(str.lstrip(","))
print(str.lstrip(" "))
print(str.lstrip(" ,")) #2개 이상에 해당되면 , 로 쭉
print(str.lstrip(", "))# 큰따옴표 안에 제거대상 문자를 나열
print(str.lstrip(" ,.")) #2개 이상에 해당되면 , 로 쭉
print(str.rstrip(" ,.")) #2개 이상에 해당되면 , 로 쭉
#[l|r]strip("삭제대상문자들나열")
print(str.strip(" ,."))
```

```
import string # 스트링 라이브러리 불러옴
print(string.punctuation) #구두점

print(str.strip(string.punctuation)) #구두점 날리기
print(str.strip(string.punctuation+" ")) #구두점+공백날리기
```

구두점 : !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~



### 메서드 체이닝

메서드(함수)  체이닝(chaining)  -> 코드가 간결해진다.

```
s ='python'.rjust(10)
print(s.upper())

print('python'.rjust(10).upper())
```

한줄 표현 가능!

    PYTHON
    PYTHON



### 패딩

#패딩(padding:특정 값으로 빈자리를 채우는 것)

```
print("hello".zfill(10)) #zero fill
```

00000hello

## 리스트

`x=[10,20,30]`

x 리스트의 0번 index 요소값 :10

```
z=[1,2,'life','is','too','short',True]
print(z[2])
print(z[6])
```

리스트에 다양한 자료형(정수형,실수형,불린)을 저장할 수 있다.

life
True

`a=[1,2,['Life','is']]` a변수의 요소는 3개.

리스트는 리스트를 요소값으로 할 수 있음 

```
a=[1,2,['Life','is']]
print(a[2])
print(a[2][1]) #'is'
```

['Life', 'is']
is

```
a=[1,2,['Life','is',['too','short']]]

print(a[2])
print(a[-1])
print(a[-1][2])
print(a[-1][-1])
```

['Life', 'is', ['too', 'short']]
['Life', 'is', ['too', 'short']]

['too', 'short']
['too', 'short']

참조할때 마이너스 가능



### 빈리스트 생성

```
b=[] 
b =list() 
```



### 리스트 slicing

```
x=[10,20,30,40,50]
print(x[1:4]
```

[20, 30, 40]

x(시작위치:끝나는거+1)

```
print(x[::-1]) #옵셋
print(x[::-2])
```

[50, 40, 30, 20, 10]
[50, 30, 10]



### range 활용

```
print(range(5)) #0~5-1까지 숫자를 생성
print(list(range(5)))
print(list(range(3,10))) 
print(list(range(3,10,2)))
print(list(range(10,0,-1)))
```

range(0, 5)
[0, 1, 2, 3, 4]
[3, 4, 5, 6, 7, 8, 9]
[3, 5, 7, 9]

[10, 9, 8, 7, 6, 5, 4, 3, 2, 1]



### 리스트 연산

```
a=[1,2]
b=[3,4]

print(a+b)
print("ab"+"cd")
```

[1, 2, 3, 4]
abcd

```
print(a*3) #[1,2] 리스트가 3번 반복
print("ab"*3)
print(len(a))
```

[1, 2, 1, 2, 1, 2]
ababab
2



* 주의할점

```
print(a[0]+"hi") #1hi가 될까? error
```

정수과 문자열은 더할 수 없다.

```
print(str(a[0])+"hi") #숫자 1 -> 문자열 "1"
```

str 함수 : 정수나 실수를 문자열로 변환해주는 함수



### 리스트 요소 값 변경

```
a=[1,2,3]
a[2]=4
print(a)
```

```
#삭제
del a[2]
print(a)

a=list(range(1,10))
print(a)
del a[:5]
print(a)
```

#삭제

[1, 2, 3, 4, 5, 6, 7, 8, 9]
[6, 7, 8, 9]

```
a=[1,2,3]
print(a)
#print(a+4) #error
print(a+[4])

a.append(4) #위랑 같음
print(a)

a.append([5,6,7]) #리스트가 추가 요소말고
print(a)

a.extend([5,6,7]) #확장개념
```



```
#del : 특정 위치에 저장된 값을 제거
a=[10,20,30]
del a[1]
print(a)

#remove : 특정 값을 제거
a=[10,20,30,10,20,30]
a.remove(30) #첫번째 30만 제거
print(a)

#뒤에 30도 지우고싶으면 한번 더 하기
a.remove(30) 
print(a)

#pop
a=[10,20,30]
a.pop() #가장 마지막 위치에 있는 데이터를 제거
print(a)

```

[10, 30]
[10, 20, 10, 20, 30]
[10, 20, 10, 20]

#pop : 뒤에서부터 꺼내는거

[10, 20]

### 정렬 

정해진 순서(내림/오름차순)로 데이터를 나열 

```
a=[3,7,5,1]
a.sort() #a에 저장된 자료를 정렬(오름)하고 결과를 a에 저장
print(a)
print(a.sort()) #이건 안됨 none 뜸 
```

```
a=['b','k','d'] #문자 가능
a.sort()
print(a)
```

```
a=[3,7,5,1]
a.sort() 
a.reverse() #내림차순
print(a)
```



### insert

```
a=[7,8,9]
a.insert(1,4) #7과 8사이 : 1 
print(a)
```

[7, 4, 8, 9]

insert(자리, 바꾸고 싶은 값)







