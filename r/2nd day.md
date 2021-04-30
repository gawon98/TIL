# boolean 참조

> p
  [1]   2  13   5   7  11 100  17 200  NA  NA  NA
 [12]  NA  NA  NA  99

 에서

```
> p[p<10] #p<10 값만 참조
[1]  2  5  7 NA NA NA NA NA NA

> p[c(TRUE,TRUE,FALSE)]
 [1]   2  13   7  11  17 200  NA  NA  NA  NA
```



# which

`which()`:논리값 -> TRUE위치 인덱스 추출 함수

which.max() , min()함수도 있음

```
> data<-c(100,110)
> data
[1] 100 110
> which(data>105)
[1] 2
```



응용

```
> month.abb[which(data>105)]
[1] "Feb"
```



which.min(data) #data에 저장된 자료 중 최소값의 인덱스

which.max(data) #data에 저장된 자료 중 최대값의 인덱스



변수명 점, 대문자 구분



# names 

: 벡터에 이름을 정의하는 함수



```
> traffic.death<-c(100,90,80,70,120,150,200)
> #traffic.death[6] #인덱스로 부르는 방법 말고

> names(traffic.death)<-c("mon",'tue','wed',"thu","fri","sat","sun")

> names(traffic.death)
[1] "mon" "tue" "wed" "thu" "fri" "sat" "sun"

> traffic.death["sat"]
sat 
150 
```



# 🎇팩터 (factor)

:카테고리 구분하는 목적으로 사용되는 데이터를 범주형 데이터



레벨(level) : 범주형(팩터)에 포함된 범주값



factor() 함수: 범주형 데이터로 사용하고자 하는 문자or숫자 벡터를 팩터로 변환

```
> review<-c("good","good","bad","indifferent","bad","good")
> review
[1] "good"        "good"        "bad"        
[4] "indifferent" "bad"         "good"  

> review.factor<-factor(review)
> review.factor
[1] good        good        bad         indifferent
[5] bad         good       
Levels: bad good indifferent
```

곁 따옴표가 없네



```
> str(review.factor)
 Factor w/ 3 levels "bad","good","indifferent": 2 2 1 3 1 2
> str(review)
 chr [1:6] "good" "good" "bad" "indifferent" "bad" "good"
```



as.numeric(review.factor) #팩터형 -> 숫자벡터로 변환



```
> everyday<-c("mon","mon","fri","tue","tue")
> everyday.factor <-factor(everyday)
> everyday.factor
[1] mon mon fri tue tue
Levels: fri mon tue
```



levels 순서 지정

```
everyday.factor<-factor(everyday, levels= c("mon",'tue','wed',"thu","fri","sat","sun"))
everyday.factor

[1] mon mon fri tue tue
Levels: mon tue wed thu fri sat sun
```



서열팩터 : 순서가 있는 범주형 데이터, 부등호 기호로 서열 표시



```
> eval<-c("medium","low","high","medium","high")
> eval.factor<-factor(eval)
> eval.factor
[1] medium low    high   medium high  
Levels: high low medium

> eval.ordered<-factor(eval,levels=c("low","medium","high"), ordered=TRUE)

> eval.ordered
[1] medium low    high   medium high  
Levels: low < medium < high
```



table



# 🎈행렬

: 각 레벨별 빈도

행렬: 2차원 벡터, 벡터에 차원을 부여 (dim 함수)

행렬은 벡터로 구성, 벡터는 타입이 모두 동일

matrix 함수로 행렬 생성 



```
> v<-1:12
> dim(v)<-c(3,4) #3행 4열
> v
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
> dim(v)
[1] 3 4
> matrix(data=v, nrow=3, ncol=4)
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
```

열방향으로 채워준다.



행기준은 `bytow=TRUE`

```
> matrix(data=v, nrow=3, ncol=4, byrow=TRUE)
     [,1] [,2] [,3] [,4]
[1,]    1    2    3    4
[2,]    5    6    7    8
[3,]    9   10   11   12

```

간단하게

```
> matrix(v,3,4, byrow=TRUE)
     [,1] [,2] [,3] [,4]
[1,]    1    2    3    4
[2,]    5    6    7    8
[3,]    9   10   11   12
```



dimnames로 행, 열에 이름 붙이기!

```
> rnames<-c("r1","r2","r3")
> cnames<-c("c1","c2","c3","c4")
> matrix(v,3,4,byrow=TRUE ,dimnames = list(rnames,cnames))
   c1 c2 c3 c4
r1  1  2  3  4
r2  5  6  7  8
r3  9 10 11 12
```



0으로 초기화

```
> matrix(0,3,4) #모두 0으로 초기화화
     [,1] [,2] [,3] [,4]
[1,]    0    0    0    0
[2,]    0    0    0    0
[3,]    0    0    0    0
```

=> 비슷하게 `NA` 도 된다



```
> mat<-matrix(v,ncol=4)
> str(mat) #행렬의 구조 보고싶을때때
 int [1:3, 1:4] 1 2 3 4 5 6 7 8 9 10 ...
```

데이터가 커지면 앞에 [1:3, 1:4]만 보고 구조파악해야됨

or

```
> dim(mat)
[1] 3 4
```

여기서 또 

`dim(mat)[1]` 처럼 들어갈 수 있음  => 3

or  `nrow(mat)` =>3



```
> length(mat)
[1] 12
```



+행렬만들때 잘 안쓰는 방법

- 두 벡터를 결합하여 행렬을 생성

`bind`

```
> v1<-1:5
> v2<-6:10

> rbind(v1,v2)
   [,1] [,2] [,3] [,4] [,5]
v1    1    2    3    4    5
v2    6    7    8    9   10

> cbind(v1,v2) 
     v1 v2
[1,]  1  6
[2,]  2  7
[3,]  3  8
[4,]  4  9
[5,]  5 10
```

두개 말고도 가능

```
> cbind(1:3, 4:6 , matrix(7:12,3:2))
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
```



```
> v<-1:12
> mat<-matrix(v,3,4)
> mat[1,]
[1]  1  4  7 10
> mat[,3]
[1] 7 8 9
```

행렬에서 특정 행or열을 지정하면 벡터로 출력



```
> mat[1,,drop=FALSE]
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
```

이렇게 하면 행렬로 출력가능

`[,3,drop=FALSE]`



특정 행+열 추출

```
> mat[2:3,]
     [,1] [,2] [,3] [,4]
[1,]    2    5    8   11
[2,]    3    6    9   12

> mat[,3:4]
     [,1] [,2]
[1,]    7   10
[2,]    8   11
[3,]    9   12

#떨어져 있으면 c로 
> mat[c(1,3),]
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    3    6    9   12
```



```
> mat[c(1,3),]
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    3    6    9   12
> mat[,c(1,4)]
     [,1] [,2]
[1,]    1   10
[2,]    2   11
[3,]    3   12
> mat[,-c(2,3)]
     [,1] [,2]
[1,]    1   10
[2,]    2   11
[3,]    3   12
> mat
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
> mat[1,3]<-77
> mat
     [,1] [,2] [,3] [,4]
[1,]    1    4   77   10
[2,]    2    5    8   11
[3,]    3    6    9   12
> mat[2,]<-c(22,55,22,55)
> mat
     [,1] [,2] [,3] [,4]
[1,]    1    4   77   10
[2,]   22   55   22   55
[3,]    3    6    9   12
```



## 연산

행렬간 연산할때는 반드시 두 행렬의 차원이 같아야 함

```
matrix(1:6,2,3) * matrix(6:1,2,3) #요소 곱 매트랩 .
```

행렬의 곱 `%*%`

```
> matrix(1:6,2,3) %*% matrix(6:1,3,2)
     [,1] [,2]
[1,]   41   14
[2,]   56   20
```



```
mtx<-matrix(1:6,2,3)
t(mtx)
t(t(mtx))
mtx
rowSums(mtx)
colSums(mtx)
rowMeans(mtx)
colMeans(mtx)
```

```
> mtx<-matrix(1:6,2,3)
> mtx
     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6
> t(mtx)
     [,1] [,2]
[1,]    1    2
[2,]    3    4
[3,]    5    6
> t(t(mtx))
     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6
```















