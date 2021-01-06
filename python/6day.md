# day5 : 함수

## review

for i (줄 수)

j 공백갯수

k 별갯수



코드 최적화 관점)

소수구할때 제곱근 사용할 수 있음

12의 제곱근 : 3.xx

12의 약수 1 2 3 4 6 12

1,자기 자신 빼면 : 2 3 4 6

소수 판별을 위해 제곱근 미만만 나눠보기 

97은 2 to 9 만 연산하면 됨



random.sample(range(1,46),6) 

범위, 갯수 

random.random() #0<=~<1

randint(10,20) #  10<=~<=20

randrange(10,20) #  10<=~<20



중복확인

while num in nun_list: #num_list가 로또번호가 저장된 리스트에 방금 뽑은 수가 있다면 





## 함수

입력 (과일) -> 함수(믹서기)  -> 출력(과일쥬스) 

```
# 함수 정의 구문
def 함수명(매개변수): # 매개변수가 과일
    문장1
    문장2
```



함수 이름지을때 역할로 

```
def add(a,b):
	sum=a+b
	return sum #호출했던 곳으로 되돌아감 출력에 해당하는 부분
```



```
#함수 호출 구문
res = add(1,2) #parameter(인수)
#return sum 값이 res로 저장
```

돌아가는 순서

함수는 스스로 수행하지 않는다. 호출해야만 수행

(함수 정의 위에 있어도 실행안되고 내려감 호출하면 위로 가서 하는거!)



1)  add(1,2) 호출

2)  add함수 수행 -> sum이 리턴

3) sum이 res에 저장



### 입력값이 없는 함수

```
def say():
    return "안녕"
print(say())
```



### 출력값이 없는 함수 (return문이 없는 함수)

```
def add(a,b):
    print("두 수의 합은: ",a+b)
res = add(3,4)
print(res)
```

두 수의 합은:  7
None



#입/출력 없는 함수

```
def say():
    print("안녕")
say()
```



### 매개변수의 초기값을 설정하여 호출

```
def add(a,b):
    print(a)
    print(b)
    return a+b
res = add(b=2,a=3) #초기값 설정
print(res)
```



```
def add(a,b=3):
    print(a)
    print(b)
    return a+b
res = add(2)
print(res)
```

add(2) -> a 인수

b는 초기화 3으로



```
def add(a,b=3): #외부에서 전달되는 값이 있으면 그 값이 저장, 없으면 기본값 3이 저장된다.

    print(a)
    print(b)
    
    return a+b
res = add(2,5) # b=5
print(res)
```

2
5
7

2는 a로 갔는데,  b는 5. 외부에서 준게 우선



### 전달되는 인수의 개수가 정해져 있지 않은 경우

```
def add(a,b):
    res = a+b
    return res
r=add(1,2)  # 이 부분이 몇개일지 모르는 경우
print(r)
```

(살짝 코드 바꿔서)

```
def add(*arg):   #(*이름) 갯수에 상관없이 전달받을 수 있음 튜플로 인식함
    res=0
    for i in arg:
        res+=i
    return res
r=add(1,2,3)
print(r)
```



## quiz

```
def addmul(op, *arg):
    if op=="add":
        res=0
        for i in arg:
            res += i
        return res

    elif op=="mul":
        res=1
        for i in arg:
         res *=i
        return res
#addmul(연산종류(add/mul), 피연산자들 )
res=addmul("add",1,2,3,4)
print(res) #1+2+3+4

res=addmul("mul",1,2,3,4,5)
print(res) #1+2+3+4
```



### 결과 갯수

```
def am(a,b):
    return a+b, a*b #함수의 결과는 항상 1개
print(am(3,4))
```

(7, 12)

하나의 튜플로 묶여서 출력됨

오 어렵다

```
def am(a,b):
    return a+b, a*b
res=am(3,4)
r1 = res[0] #튜플 참조 가능
r2= res[1]
print(r1)
print(r2)
```

7
12

튜플은 참조 가능하니까 따로따로 출력

아니면 이렇게

```
r1,r2=am(3,4)
print(r1)
print(r2)
```



### return 용법

```
def am(a,b):
    return a+b #함수가 종료됨
    return a*b #이러면 안된다~
print(am(1,2))
```

한번만 쓸것.



```
def prn():
    print("안녕")
    return #생략가능
prn()
print("하세요")
```



함수 중간에 return이 있으면 그 밑의 문장은 수행하지 않게된다.

```
def prn(a):
    if a=="안녕":
        return
    print("반가워")
prn("잘있었니?")
```

반가워



## quiz 2

```python
def say(name,age,man=True):
    print('내 이름은 %s' %name)
    print('나이는 %d'  %age)
    if man == True:
        print('성별은 남')
    elif man == False:
        print('성별은 여')
  #  elif man is None:    안써두됨~~~
  #      print('성별은 남')

say('홍길동',25)
```

조건 : 3번째 인수 없을때 남자로 나오게 

있을수도 있고 없을수도 있으면 man=True 이런꼴로 쓰는거래

* 전달되는 값이 없는 경우에는 

  기본값을 갖는 매개변수를 함수의 맨 마지막에 (man=True를 마지막에 쓰라고)

  

```
a=1  # 함수밖에 있는 a
def mytest(a):   #매개변수 a는 함수 안에서만 사용되는 변수임. 함수밖에 있는 a가 아니다. 
				
    a=a+1
    
mytest(a)
print(a)
```

출력 1로 나옴

설령 이름이 같더라도 같은 변수가 아니다.



```
def mytest2(z):
    z=z+1
   
mytest2(3)
print(z)
```

print(z) 의 z랑 함수 속 z 다르니까 not defined error



### 안에서 밖에 있는 변수를 바꾸고싶을때

```
a=1
def mytest3(a):
    a=a+1 
mytest3(a)
print(a) #2가 출력됐으면
```

함수 안에서 밖에 있는 변수를 증가하고 싶다면 2가지 방법 존재

#1. return 사용

```

a=1
def mytest3_1(a):
    a=a+1 #함수 안안에서 밖에 있는 변수를 증가하고 싶다면 2가지 방법 존재
    return a
a=mytest3_1(a)
print(a) #2가 출력됐으면
```



#2. global 사용 : 함수 안에서 함수 밖의 변수를 직접 사용 가능

```
a=1
def mytest3_2():
    global a #바깥에 있는 a 쓸꺼야
    a=a+1
 # return 필요없음!
mytest3_2()
print(a)
```



## lambda 

def와 동일한 기능을 수행하는 예약어

함수 정의시 일반적으로 def를 사용하나 함수가 복잡하거나 def를 사용하지 못하는 경우 씀



```
def myadd(a,b):
    return a+b
res=myadd(2,3)
print(res)

#위 구문을 람다를 이용해보기

myadd2 = lambda a,b:a+b
res=myadd2(2,3)
print(res)
```

`함수이름 = lambda 매개변수1,매개변수2, ...: 매개변수를 이용한 계산식`



```
#일반함수형식
def pt(x):
    return x+10
print(pt(1))

#람다 함수 형식
pt=lambda  x:x+10
print(pt(1))
```



익명의 람다함수

```
#람다 자체를 바로 호출
print((lambda  x:x+10)(1))
```

11

`(lambda 매개변수들:수식)(인수들)`



```
print((lambda x,y :x+y)(1,2))
```

3



```
#람다 함수 내에서 변수 생성 못함
print((lambda x:y=2; x+y)(1)) #문법오류
```

```
#찢어서 할 것
y=2
print((lambda x:x+y)(1))
```



## 최댓값 함수 안쓰고 for문

```
m=0
    for i in range(len(arg)):
        if m<arg[i]:
            m=arg[i]
    return m
print("최대값:",mymax(5,1,3,2))
print("최대값:",mymax(2,7,9))
```



## 함수의 인수 부분에 간단한 함수를 적용하고자 하는 경우



```
def pt(x):
    return x+10
print(list(map(pt,[1,2,3])))
```

[11, 12, 13]

map은 list로 묶어서 확인할 것

`map(함수,데이터)`

* lambda로 쓰기

  ```
  print(list(map(lambda x:x+10,[1,2,3])))
  ```