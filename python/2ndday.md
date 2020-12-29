# 파이썬 2일차



리스트 : [] , 튜플 : () ,딕셔너리,셋 :{}

리스트는 자료를 순서대로 저장하는데 콤마로써 자료를 구분함

```
languages = ['python', 'perl', 'c', 'java']
#리스트, 자료 4개
#변수 = 데이터 => 데이터를 변수에 저장해라

for lang in languages:  #빈복 ,갯수만큼 4번 반복
    if lang in ['python', 'perl']:
        print("%6s need interpreter" % lang)
    elif lang in ['c', 'java']: #선행 if의 조건이 아니면
        print("%6s need compiler" % lang)
    else:  # 위 조건 둘다 아니면
        print("should not reach here")
```



## 기본적인 문법

한줄에 두문장 쓰고 싶으면 세미콜론 쓰기

`print('hello,world');print('bye')`



` a=1  # assign (할당, 왼쪽 <- 오른쪽)`

` a=1+2 `  # a에 3이 저장됨 더해라



* 주석은 반드시 필요한 부분에만 달 것

* 전체 주석 Ctrl + /

  

### 들여쓰기

파이썬에서 들여쓰기(tab)는 중요

if 문 들여쓰기 지우면 뜨는 에러

IndentationError: expected an indented block

shift+tab : 한탭뒤로



### 코드블록

코드가 모여있는 상태를 의미, 들여쓰기가 동일한 코드 집합

하나라도 들여쓰기 다르면 if 조건에 안엮이고 코드블럭 바깥의 것으로 출력된다.

```
a = 3

if a==3:
	print('3')
	print('three')
	print("3과 같아요")
```

```
if a==3:
	print('3')
	print('three')
print("3과 같아요")    <- 독립이라 조건 바껴도 출력
```



### 연산기능

```
print(1-1)
print(1/2)
```

연산자 다 가능

```
print(5//3)  # 몫 , 소수이하 버림
print ( % 4) #나머지, 3
```



```
print(6//3)		#2
print(6//3.0)   #2.0
```

정수형 실수형



```
print(2 ** 2) # 거듭제곱 연산자 
```

* 파이썬은 자릿수 제한 없어서 메모리가 가능한한 다 계산가능
* 

```
print(int(3.3))
print(int(5/2))
print(int('10')) # 숫자 말고 문자됨 일영이라고 읽음
```

```
print(int('10'+2)) 문자라서 연산불가능
print(int('10')+2) #문자열 일영 -> 숫자 10변환 =>12
```



```
print(type(10))    # class int 정수형
print(type('123')) # class str
```



### divmod 함수

`divmod(9,4)` 9를 4로 나눈 몫과 나머지 (피제수,제수)

출력 : (2,1) 



### 요소출력하기

인수 : 함수 안에 들어가는 수 

```
res = divmod(9,4)  #res = (2,1) 튜플 1개, 2개 요소(몫, 나머지)

print("결과:", res)
```

출력 : 결과: (2, 1)



```
print("1번재 요소 :",res[0]) # 그대로 인쇄, 곧바로 이어서 출력, res튜플에 저장된 1번째 요소값을 출력
print ("2번재 요소 :",res[1])

```

튜플(리스트)에서 데이터의 위치는 0번부터 시작한다.

index 잘못줘서 범위 벗어나면 IndexError 



```
res1 , res2 = divmod(9,4)
print ("1번재 요소 :",res1)
print ("2번재 요소 :",res2)
```

한방에 뽑기



```
a,b,c = 1,2,3
print(a,b,c)
```

한방에 넣기 가능

```
a=b=c=d=1
print(a,b,c,d)
```

초기화도 한번에 



### 진수표현

```

print(11) #10진수
print(0b11)# 3
print(0o10) #8

```

0b 2진수

0o 8진수



### 실수형 float 

```
print(5)
print(float(5))
print(float(1+2))
print(float('3.14')) # 문자 -> 실수형
print(float('3.14')*2) 
```

5

5.0



### 따옴표 주의 

```
print("Kim's computer")
```

```
print('he said. "how are you?"')
```



### 줄 관리

```
print ("안\t녕!\n반가워요\n\n잘있어요")
#\t 는 탭 , \n은 new line
```

안	녕!
반가워요
잘있어요



```
print("안녕")
print("하세요")
```

--> 줄 띄어서 출력됨

```
print("안녕",end="")
print("하세요")
```

--> 줄 연결 출력됨

end 따옴표 사이에 넣고싶은거 넣어도 가능

#### 따옴표 3개

```
x ="""
인생은 
짧다
그래서 파이썬이
필요하다
"""
print(x)
```

가독성 좋아짐 



### 구분자 넣기

```
print ("naver","kakao","samsung") #공백으로 연결되어 출력
print ("naver","kakao","samsung", sep = "$")
```

naver kakao samsung
naver$kakao$samsung



### 순서바꾸기

```
x,y=1,2
x,y = y,x
print(x,y)
```

유연 

### 변수제거

`del x`

-----



변수만 만들고 값을 저장하고 싶지 않은 경우

`b=None`

### 축약형 연산자

```
x=10
x+=10 #x=x+10 같은말 연산속도 빠름
print(x)

x-=5
x*=5
x/=5
```

### 입력

input()

입력을 받은 뒤 엔터키를 누르면 다음문장으로 이동

```
x = input("출력하고 싶은 값을 입력해주세요 : ")
print("당신이 입력한 값은 : ",x)
```

출력하고 싶은 값을 입력해주세요 : 50
당신이 입력한 값은 :  50

Process finished with exit code 0



input 함수로 입력받은 모든 데이터는 문자로 간주한다.

```
x =int(input("첫번째 수 : "))
y= int(input("두번째 수 : "))
print("덧셈 결과는 ",x+y)
```



```
x =float(input("첫번째 수 : "))
y= float(input("두번째 수 : "))
print("덧셈 결과는 ",x+y)
```



#### 여러개 입력

```
a,b = input("두 수를 입력하세요 : ").split()# 3 2
print(a)
print(b)
```

.split( ) 공백 단위로 스플릿. 

3은 a에 2는 b에 



```
a,b = input("숫자 두개 입력 : ").split()
print(int(a)+int(b))
```

윗줄에 int 전체에 씌우는건 에러.

숫자가 2개라서 int (1,2)는 문법적으로 잘못됨

#### map함수

```
함수출력 = map(함수, 함수입력)
```

x -> f -> y

```
x1,x2 = map(int, ['3','4'])
print(x1+x2)
```

`x1, x2 = map(int, input("숫자 두개 입력 : ").split())`



` x1, x2 = map(int, input("숫자 두개 입력 : ").split(","))` 

입력값 콤마로 구분  1,2



### 반복출력

```
a='python'
print(a*3) #a변수에 저장된 값을 3번 반복
```

pythonpythonpython



```
print("="*50)
```

==========

구분선 긋기

### len(x) , Index

```
x="life is too short"
print(len(x))
print(x[0]) #l, 위치(인덱스) 는 0부터 시작
print(x[-1]) #t, -기호는 뒤에서부터 참조
```

* 공백문자 포함해서 센다

#인덱싱 : 변수에 저장된 문자열에 대해 위치를 지정하여 참조하는 행위

```
x="life is too short"
print(x[5]+x[6]) #is , 이렇게 잘 안씀
print(x[5:7]) #is , 범위 지정 슬라이싱 [시작위치: 끝위치+1]
```

7번은 포함안하고 6번까지함

```
print(x[12:])
```

끝위치를 지정하지 않으면, 문자열의 마지막까지 참조

```
print(x[:4]) #life, 맨 앞에서부터 4-1=3번 인덱스까지 추출
print(x[:]) #전체 
print(x[8:-3]) # too sh, -3위치는 안하고 그 앞까지
```



### 문자열 에러

```
x =  'pithon'
print(x[1])
x([1]) = "y"  #에러
```

문자열의 요소값은 변경 안됨 (원래 안됨)



### 문자열 포매팅

```
print("I eat %d eggs" %3)
-----------------------
x =5
print("I eat %d eggs" %x)
```

변화가 있는 부분을 %d 처리 , d(decimal , 십진수) 



```
x = "two"
print("i eat %s eggs" %x)
```

%s (string) , %f : 실수 



```
x = "two"
d=3
print("i eat %s eggs. so i was sick for %d days." %(x, d))
```

여러개면 뒤에 () 묶어주기



```
x = "two"
d=3
per = 30
print("i eat %s eggs. so i was sick for %d days. %d%%" %(x, d, per))
```

퍼센트 직접 출력일때 두번쓰기

i eat two eggs. so i was sick for 3 days. 30%

## 문제풀기

1. 첫번째와 세번째 문자를 출력하세요.
letters = 'python'
2. 뒤에 4자리만 출력하세요.
   cn="24가 2210"
3. 문자열에서 '파' 만 출력하세요.
  s = "파이썬파이썬파이썬"
4. 문자열 '720'를 정수형으로 변환해보세요.
  num_str = "720"

5. 문자열 "15.79"를 실수(float) 타입으로 변환해보세요.
data = "15.79"

6. 에어컨이 월 48,584원에 무이자 36개월의 조건으로 홈쇼핑에서 판매되고 있습니다. 총 금액은 계산한 후 이를 화면에 출력해보세요.

```
#1.
letters = 'python'
print(letters[0])
print(letters[2])

#2.
cn = "24가 2210"
print(cn[4:])

#3.
s = "파이썬파이썬파이썬"
print(s[0],s[3],s[6])

#4.
num_str = "720"
num_str =int(num_str)
print(type(num_str))

#5.
data = "15.79"
data = float(data)
print(type(data))

#6.
total = 48584 * 36
print(total,'원')
```