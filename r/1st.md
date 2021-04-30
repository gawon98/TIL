clear all : 컨트롤 +L

블럭 컨트롤+enter



`?apply` 처럼 앞에 `?` 붙여서 검색가능



`a<-3` a에다 3을 할당해라

데이터 분석에서 자료의 기본형은 벡터

스칼라 길이가 1인 벡터

```
c(1,2,3)
c("we","love","data")

odd<-c(1,3,5)
even<-c(2,4,6)
c(odd,even)
```

수열

`3:9`  3 4 5 6 7 8 9 

5:1  5 4 3 2 1

5:-1  5 4 3 2 1 0 -1

* 다양한 증감치를 이용한 수열 생성

  seq(from=3, to=9) #3:9

  seq(from=3, to=9, by=0.5)

  



```
> seq(from=9, to=3, by=-0.5)
 [1] 9.0 8.5 8.0 7.5 7.0 6.5 6.0 5.5 5.0 4.5 4.0
[12] 3.5 3.0
```

대괄호 인덱스 번호 



```
> seq(from=0, to=100, length.out=5)
[1]   0  25  50  75 100
```



```
> rep(1, times=3)
[1] 1 1 1
```

벡터 전체를 반복할때 times 를 사용한다



```
> rep(c(1,2,3), times=5)
 [1] 1 2 3 1 2 3 1 2 3 1 2 3 1 2 3
```



각 원소를 반복 할때 each 사용

```
> rep(c(1,2,3), each=5)
 [1] 1 1 1 1 1 2 2 2 2 2 3 3 3 3 3
 
> rep(1:3, length.out=8)
[1] 1 2 3 1 2 3 1 2
```

길이 반복



스칼라는 하나의 숫자로만 이루어진 데이터 

하나의 벡터를 이루는 데이터의 개수가 N개 이면 N차원 벡터라 부름

(250,255,0,0,...,210,255) => 10000개 -> 10000차원



문자열+숫자열 합치면

```
> num<-c(1,2,3) #concatenate
> cha<-c("x","y","z")
> c(num,cha)

[1] "1" "2" "3" "x" "y" "z"
```

문자열로 합해집니다





벡터의 유형 및 구조 확인

` str` 함수

```
> n<-c(1,2,3) #concatenate
> str(n)
 num [1:3] 1 2 3
```

num 으로 자료형 뜸



length :벡터의 길이만 확인



상수벡터

```
> LETTERS
 [1] "A" "B" "C" "D" "E" "F" "G" "H" "I" "J" "K"
[12] "L" "M" "N" "O" "P" "Q" "R" "S" "T" "U" "V"
[23] "W" "X" "Y" "Z"
```



```
> letters
 [1] "a" "b" "c" "d" "e" "f" "g" "h" "i" "j"
[11] "k" "l" "m" "n" "o" "p" "q" "r" "s" "t"
[21] "u" "v" "w" "x" "y" "z"
```



```
> month.abb
 [1] "Jan" "Feb" "Mar" "Apr" "May" "Jun" "Jul"
 [8] "Aug" "Sep" "Oct" "Nov" "Dec"
```



```
> month.name
 [1] "January"   "February"  "March"    
 [4] "April"     "May"       "June"     
 [7] "July"      "August"    "September"
[10] "October"   "November"  "December" 
```



두개 이상 추출하고 싶으면 하나의 벡터로 묶어서

```
month.name[c(1,2)]
[1] "January"  "February"
```



features, variable 라구 부른다

# 벡터화(vectorized) 연산 

=> 속도가 빠르다 

```
> 1+2
[1] 3
> 2^10
[1] 1024
> 10%%3 #나머지?
[1] 1
> 10%/%3
[1] 3
```



벡터 연산은 원소와 원소끼리 연산 수행 (그 매트랩 . 처럼)

```
> x<-c(1,2,3)
> x*c(4,5,6)
[1]  4 10 18
```



```
> x<-c(1:3)
> y<-c(4:9)
> x+y
[1]  5  7  9  8 10 12
```

길이를 자기맘대로 늘려버림



스칼라 계산

```
> c(1,3,5) + 10
[1] 11 13 15
```

길이 짧은쪽에 있는게 긴쪽과 동일하게 ~



그럼길이가 배수관계가 아닐때는?

```
> c(1,2,3) + c(4,5,6,7,8)
[1]  5  7  9  8 10
경고메시지(들): 
In c(1, 2, 3) + c(4, 5, 6, 7, 8) :
  두 객체의 길이가 서로 배수관계에 있지 않습니다
```

연산은 된다



# 논리연산자

```
> v<-pi
> w<-10/3

> v==w
[1] FALSE
> v!=w
[1] TRUE
> v>w
[1] FALSE
> !(v>w)
[1] TRUE
> (v==w)|(v<w)
[1] TRUE
> (v==w)&(v<w)
[1] FALSE
> isTRUE(v==w)
[1] FALSE
```



🎈자주씀

```
> x<-c(0,25,50,75,100)
> x>50
[1] FALSE FALSE FALSE  TRUE  TRUE
```

전부 다 고려



```
> sum(1:5)
[1] 15
> sum(TRUE,FALSE,TRUE)
[1] 2
```



any함수 : 논리값이 하나라도 TRUE 면 결과가 TRUE

all함수 : 논리값이 모두 TRUE면 결과가 TRUE

```
> a<--3:3
> any(a>0)
[1] TRUE
> all(a>0)
[1] FALSE
```



2의 제곱근의 제곱 => 2지만, r에서는 정확히 2가 아님(부동소수점수 연산)

수치 비교시 정밀도 문제를 피하기 위해서는 all.equal() 함수를 이용

```
> sqrt(2)^2==2
[1] FALSE
> all.equal(sqrt(2)^2,2)
[1] TRUE
```

약간의 오차를 무시하므로 두 값이 같다고 출력한다.

🎷🥁🎺🎸🪕🎻🎹📯🎼🔔



# paste

: 문자 벡터끼리 결합 



```
> fruits<-c("Apple","Banana","Strawberry")
> food <-c("Pie", "Juice","Cake")
> paste(fruits, food)
[1] "Apple Pie"       "Banana Juice"   
[3] "Strawberry Cake"
```



```
> paste(fruits, "Juice")
[1] "Apple Juice"      "Banana Juice"    
[3] "Strawberry Juice"
```

길이 다르니까 Juice로 쭉



# abs(x)

: 절대값



# log()

: log 함수는 디폴트 밑수 e인 자연로그

`log(1:5, base=3)` #밑수가 3인 로그

```
> log(1:5, base=3)
[1] 0.0000000 0.6309298 1.0000000 1.2618595 1.4649735

> log(1:5, base=2)
[1] 0.000000 1.000000 1.584963 2.000000 2.321928
```

 아니면 이렇게 써도된다

```
> log10(1:10)
 [1] 0.0000000 0.3010300 0.4771213 0.6020600
 [5] 0.6989700 0.7781513 0.8450980 0.9030900
 [9] 0.9542425 1.0000000
 
> log2(1:10)
 [1] 0.000000 1.000000 1.584963 2.000000 2.321928
 [6] 2.584963 2.807355 3.000000 3.169925 3.321928
```



# exp

: 밑수가 e인 지수값

```
> exp(1:5)
[1]   2.718282   7.389056  20.085537  54.598150
[5] 148.413159
```



```
> y<-exp(1:5)
> log(y)
[1] 1 2 3 4 5
```



# factorial

```
> factorial(1:5)
[1]   1   2   6  24 120
```



5C2

```
choose(5,2) #5개 중에서 2개를 선택하는 경우의 수
```

nCr  = n! / (r!(n-r)!) => 120/(6*2) = 10



# sqrt

sqrt(1:5) # 유효자릿수 7자리 

#유효자릿수 확인

```
options("digits")
```



# round

반올림

```
> round(456.789, digits=1)
[1] 456.8
> round(456.789, digits=2)
[1] 456.79
```



반올림 숫자가 5인 경우에 **가까운 짝수**로 반올림

```
> round(11.5)
[1] 12
> round(12.5)
[1] 12
```



floor : 작은 가까운 정수로 반올림

ceiling : 큰 가까운 정수로 반올림

trunc : 0에 가까운 정수로 반올림

```

> floor(456.78)
[1] 456
> floor(-456.78)
[1] -457
> 
> ceiling(456.78)
[1] 457
> ceiling(-456.78)
[1] -456
> 
> trunc(456.78)
[1] 456
> trunc(-456.78)
[1] -456
```



# signif

유효숫자

```
> signif(-123.456,digits=4) 
[1] -123.5 
> signif(-123.456,digits=5) 
[1] -123.46 

```



---



1~10까지 수에 대한 각각의 제곱근을 구한다음 소수이하 2자리까지 출력

`rount(sqrt(1:10),digits=2)` 반복문 없이 해결가능!



# Inf

```
> 3/0
[1] Inf
> 5-Inf
[1] -Inf
> Inf*Inf
[1] Inf
> Inf*(-Inf)
[1] -Inf
```

r에서는 1.8*10 의 308승 까지 표현가능

```
> is.infinite(10^306)
[1] FALSE
> is.infinite(10^307)
[1] FALSE
> is.infinite(10^309)
[1] TRUE
```



NaN (Not a number) : 숫자가 아님, 결과를 정의할 수 없다

Inf/Inf

Inf*0

log(-2)

NaN+3



NA(Not Available, 결측값)



```
z<-1:5
> sum(z)
[1] 15
> prod(z)
[1] 120
> min(z)
[1] 1
> max(z)
[1] 5
> mean(z)
[1] 3
> median(z) #중앙값
[1] 3
> var(z) #분산
[1] 2.5
> sd(z) #표준편차
[1] 1.581139
> range(z) 
[1] 1 5
```



z<-(c,NA) 하고 위 연산 수행하면 NA만 나옴

결측값 처리

```
z<-(2,NA)
sum(z, na.rm=TRUE)
sum(na.omit(z))
```

결측값을 통계 분석 시 제외(미포함): na.rm = TRUE

결측값이 들어있는 행 전체를 데이터 셋에서 제거: na.omit()



# cumsum

: 누적합

```
> traffic.death<-c(10,20,30,20)
> cumsum(traffic.death)
[1] 10 30 60 80
```



```
> traffic.death<-c(10,20,NA,30,20)
> cumsum(traffic.death)
[1] 10 30 NA NA NA
```



# diff

```
> traffic.death<-c(10,20,30,20)
> diff(traffic.death)
[1]  10  10 -10
```

뒤 - 앞



```
> diff(1:10 , lag=3) #3칸 떨어진 원소간의 차를 구함
[1] 3 3 3 3 3 3 3
```



# 집합

합집합 `union`

```
> p<-1:10
> q<-6:15
> union(p,q)
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15
```



교집합 `intersect`

```
> intersect(p,q)
[1]  6  7  8  9 10
```



차집합` setdiff `

```
> setdiff(p,q)
[1] 1 2 3 4 5
```

p-q



집합이 동일한지 확인 

```
> setequal(p,q)
[1] FALSE
```



# is element()

:첫번째 인수에 오는 값이 두번째 벡터의 원소인지 테스트

```
> is.element(3, 1:5)
[1] TRUE
> is.element(6, 1:5)
[1] FALSE
> is.element(4:7, 1:5)
[1]  TRUE  TRUE FALSE FALSE
```



--------

# 인덱싱 관련



```
> num<-0:30
> num
 [1]  0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15
[17] 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30
> num[5]
[1] 4
> num[5:10]
[1] 4 5 6 7 8 9
```

인덱싱이 1부터



```
> prime <- c(2,3,5,7,11,13)
> idx<-c(1,3,5)
> prime[idx]
[1]  2  5 11
```



```
> prime[3:5]
[1]  5  7 11
> prime[-3] #제외됨! 
[1]  2  3  7 11 13

> prime[-2:-4]
[1]  2 11 13

```

-는 제외되는 영역 

or `prime[-(2:4)]`



직접대입가능

```
> prime[2]<-30
> prime
[1]  2 30  5  7 11 13
> prime[c(3,4)]<-c(30,40)
> prime
[1]  2 30 30 40 11 13
```











