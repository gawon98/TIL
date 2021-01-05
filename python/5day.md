# 제목

## 연습문제 review

```
num=[5,1,4,3,2]
print(max(num)) #최대값
print(min(num)) #최소값
print(sum(num))
print(len(num))
avg =sum(num)/len(num) #평균
print(avg)
```



split 각각 리스트로 나옴 <--> join 하나의 문자열로 묶음

sort는 한번에 print로 안묶이지만

sorted는 묶임 -> 그리고 분류된채로 저장안됨.



홀짝구분은 x%2 나머지로



내림차수

``` 
a.sort()
a.reverse()
```



list에서 pop은 마지막 요소부터 추출하지만

딕셔너리는 추출하고자 하는 데이터의 키를 인수로 지정



키와 밸류의 기본적인 형태.

* 딕셔너리의 키는 변하지 않는 값을 사용

```
a['name'] = 'python' #이 문법만 알면됨

a[250] = 'python' #숫자 키도 안씀
a[('a',)]='python' #거의 안쓰는 문법
a[[1]] = 'python' #오류! [1]은 리스트이므로 변하는 값 -> 딕셔너리의 키로 x
```



## 딕셔너리

### clear

```
dic.clear() #모든 요소들을 제거, 거의 쓸일은 없다.
print(dic)
```



### get

```
dic={'아이디':'홍길동', '레벨':10, '체력':100, '마나':20, '공격력':200, '방어력':50}

print(dic['아이디'])
print(dic.get('체력')) #키에 연결된 값을 추출
```

#딕셔너리.get('키') == 딕셔너리['키']

#### 차이점

없는것을 찾을때

```
print(dic.get('민첩')) #none
#print(dic['민첩']) #error

print(dic.get(('민첩',0))) #민첩키가 존재하지 않으면 디폴트값으로 0을 출력
```



"", None, 0은 거짓으로 분류된다.



## 집합(set)

set 별로 쓸일 없음



```
#집합(set) :{} 중괄호
s1 = set([1,2,2,3]) #리스트 자료를 기초로 집합(중복 제외)을 생성
print(s1)
```

{1, 2, 3}

```
s2=set("hihello")
print(s2)
```

{'i', 'l', 'o', 'e', 'h'} #바뀜



빈 셋

```
s3=set()
print(s3)
```



* set은 시퀀스 자료형이 아님

  ```
  s1=set([1,2,2,3])
  print(s1)
  print(s1[2]) #에러 발생 : 리스트나 튜플은 순서가 있음 
  -> 인덱싱을 통해 데이터 접근 가능 
  ```

반면에 셋(set)은 순서가 없음 -> 인덱싱을 할 수 없음 -> 인덱싱으로 접근하고 싶으면 리스트로

```
print(list(s1))

s11=list(s1)
print(s11[2]) #참조도 가능
```

튜플도 상관없음



### 교집합 합집합 차집합

```
s1 = set([1,2,3,4,5,6])
s2 = set([4,5,6,7,8,9])

#교집합
print(s1&s2)
print(s1.intersection(s2))

#합집합
print(s1|s2)
print(s1.union(s2))

#차집합
print(s1-s2)  #순서
print(s1.difference(s2))
```



### 데이터 추가

.add() 함수 이용

add는 요소 한개만 추가가능, list 사용 안됨

```
s3=set()
s3.add(3)
print(s3)
```



#여러개 추가할때 update

```
s3=set()
s3.update([1,2,3,5,6])
print(s3)
```

{1, 2, 3, 5, 6}

```
s3.update([1,2,3,15,16])
print(s3)
```

{1, 2, 3, 5, 6, 15, 16}

있던건 또 추가안된다. 



### 데이터 제거

```
s3.remove(2)
```

{1, 3, 5, 6, 15, 16}



## 불 자료형

참 : "test" , [1,2] ,1 ... 값이 존재

거짓 : "", None, 0, [], (), {}





## 반복문 조건문 (간략)



```
while 조건:  #조건이 참인 동안에 문장수행을 반복하세요
	문장1
	문장2
	...
```

true : a 리스트에 pop 대상 데이터가 남아있는 경우

```
a= [1,2,3]
while a:
    print(a.pop())
print("반복문을 종료합니다")
```



### if

```
if 조건 : 
    문장1
    문장2
else 
	문장1
	문장2	
```

```
if []:
    print("참")
else:
    print(("거짓"))
```

거짓.



참거짓 헷갈리때

`bool()` 안에 넣어보기



#변수 = 리스트? 리스트(객체)는 메모리에 생성되고, 변수 a는 리스트가 저장된 메모리의 주소를 가지게 된다



```
x=1
if x==1:
    print("x는 1이다")
```

pass #코드를 수행하지 않고 넘어감

* 들여쓰기 항상 주의하기

```
x=5
if x>=1:
    print("1이상")
    if x>=5:
        print("5이상")
    if x==10:
        print("10")
print("출력")
```

if 문 순서대로



```
money =True
if money:
    print("버스")
    print("택시")
else:
    print("도보")
```

불린값 ㄱㄴ



#or, and, not : 여러 조건을 표현



```
money=1000
card=True
if money>=5000 and card: #or:또는
    print("택시")
else:
    print("버스")
```

버스



```
if 조건:
    문장
elif 조건:
    문장
elif 조건:
    문장
else:
    문장
```



```
money=1000
card=True
if money >3000:
    print("택시")
elif card:
    print("버스")
else:
    print(("도보"))
```

버스



```
s=60
if s>=60:
    msg="pass"
else:
    msg="fail"
print(msg)
```



😁궁극의 코드😁 

```
s=60

msg="pass" if s>=60 else "fail"
#만약 s가 60이상이면 "pass"를 msg에 대입하고, 아니면 "fail"을 msg에 대입

print(msg)
```



### while

 반복문: for, while

```
i=0
while i<10:
    i=i+1
    print(i,"번째 반복 수행")
```

무한루프 빠지면 빨강 ▢

```
if i>10:
	break #반복문을 빠져나가라
```



```
prompt="""
1.추가
2.삭제
3.종료
번호 입력:"""
print(prompt)

num=0
while num !=3:
    print(prompt)
    num=int(input())
```



#### continue

```
a=0
while a<10:
    a=a+1
    if a%2==0: continue #continue는 while의 시작위치로 이동시킴
    print(a)
```

밑으로 안내려가고 위로 올라감

1
3
5
7
9

#### break

```
a=0
while a<10:
    a=a+1
    if a%2==0: break # break는 반목문을 벗어나게 됨
    print(a)
```

break는 while문 통째로 빠져나옴

1



#### 쪽지문제

while문을 이용하여 1~100사이의 자연수 중 4의 배수의 합을 출력

내꺼

```
x=0
tmp =0
while x<=100:
    x=x+1
    if x%4==0:
        temp = int(x)
        tmp=tmp+temp
print(tmp)
```



선생님

```
i=0
sum=0
while i<100:
	i=i+1
	if i%4 ==0:
		sum=sum+i
print(sum)
```



### for문

`for 변수 in 리스트(튜플,문자열):`

```
mylist=[1,2,3]
for i in mylist:
    print(i)
```



```
for i in "bigdata":
    print(i)
```

문자열은 문자 하나하나로 나옴

b
i
g
d
a
t
a



```
for i in [(1,2),(3,4),(5,6)]:
    print(i)
```

튜플단위로 읽어옴

(1, 2)
(3, 4)
(5, 6)



```
for i,j in [(1,2),(3,4),(5,6)]:
    print(i)
    print(j)
    print("="*50)
```



```
for i in range(5):
    print(i)
```

0
1
2
3
4



```
for i in range(3,10):
    print(i)
```

3
4
5
6
7
8
9



```
a=[5,6,7,8]
for i in range(len(a)):
    print(i)
```

0
1
2
3

#### 구구단을 외자

```
for dan in range(2,10): #dan=2 to 9
    for i in range(1,10): #i =1 to 9
        print(dan*i, end=" ")
    print("") #줄바꿈
```

2 4 6 8 10 12 14 16 18 
3 6 9 12 15 18 21 24 27 
4 8 12 16 20 24 28 32 36 
5 10 15 20 25 30 35 40 45 
6 12 18 24 30 36 42 48 54 
7 14 21 28 35 42 49 56 63 
8 16 24 32 40 48 56 64 72 
9 18 27 36 45 54 63 72 81 





## 메모리의 주소



`print(id(a))`

실제 메모리상의 물리 주소

실행할때마다 바뀜

```
b=a #a가 가지고 있는 값은 엄밀히 얘기하자면 [1,2,3]이 저장되어 있는 "주소값"
```



```
a=[1,2,3]
b=a 
#a가 가지고 있는 값은 엄밀히 얘기하자면 [1,2,3]이 저장되어 있는 "주소값"

print(id(a))
print(id(b))

a[1]=5
print(a)
print(b)
```

[1, 5, 3]
[1, 5, 3]

b=a는 주소를 복사하는거라 a 바꿔도 b도 바뀜

### is

```
# is : 두변수가 가르키는 메모리상의 대상이 동일한지 확인 (주소)
print(a is b)
```

True -> 주소가 같기 때문



```
a=[1,2]
b=[1,2]
print(id(a))
print(id(b))
print(a is b) #결과적으로 주소가 같은지 확인하는 것
```

False

a==b 는 값이 같은지 확인



#b 변수를 만들때, a 변수의 값은 가져오면서 a와 다른 주소를 가르키도록 하고 싶다면

(1)  [:] 이용

```
a=[1,2,3]
b=a[:] #b=a은 동일한 대상(데이터)를 가르킴
print(id(a))
print(id(b))
print(a)
print(b)
a[1]=10
print(a)
print(b)
```

1714925090368
1714925423616
[1, 2, 3]
[1, 2, 3]
[1, 10, 3]
[1, 2, 3]

주소 다르고 a만 바뀌는거 확인 가능



(2) copy 모듈에 있는 copy 함수를 이용

패키지(폴더) : 모듈(파일) 또는 패키지의 묶음

모듈 : 관련 함수들의 묶음

`from 모듈명 import 함수명` 모듈로부터 함수를 가져와라

```
from copy import copy
a=[1,2]
b=copy(a) #b=a[:] 와 같음
print(id(a))
print(id(b))
print(a is b)
```

주소 다르고 False 나옴



## rand

```
import random
print(random.random()) #0~1
print(random.randrange(1,7))

print(random.randint(1,46))
print(random.randrange(1,46,2)) #1~45까지 2씩 증가시킨 수 중에서 난수 발생
```







