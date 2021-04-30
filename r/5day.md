# 표준화&정규화 (apply)

표준화 = (각 열 data - 각 열 평균 ) / 각 열 표준편차

정규화 = (각 열 data - 각 열 최솟값 )/(최대-최소)

```
평균 각각 구하고,
tempIris<-t(iris[1:4])
tempIris<-c(각 평균 )
```

t :Matrix Transpose



```
data(iris)
scale(iris[,1]) # 행렬 유형 정규화 함수 
#표준화
head(iris[,1] - mean(iris[,1] / sd(iris[,1]))) #vector
```



```
cbind(iris, scale=scale(iris[,-5]))
```



```
#apply(데이터, 행(1)/열(2), 함수)
apply(iris[,-5],2, scale) #열단위라는 뜻
```



표준화

```
apply(iris[,-5],2, function(x){x-mean(x)/sd(x)})
```

na가 포함되어 있다면

```
apply(iris[,-5],2, function(x){x-mean(x)/sd(x, na.rm=T)})
```



정규화

```
apply(iris[,-5],2, function(x){x-min(x, na.rm=T)/max(x, na.rm=T)-min(x, na.rm=T)})
```





# 문자열

텍스트마이닝(text mining ) : 텍스트 캐내기 ⛏

-> 베이지안 필터 이메일분류기( 햄 or 스팸)



```
x<-"we have a dream"
nchar(x) #케릭터의 갯수 15
length(x) #문자열을 하나로 본다 1

length(c("we","have","a","dream"))
y<-c("we","have","a","dream")
length(y[4]) #1
nchar(y[4]) #5

> nchar(y)
[1] 2 4 1 5

> tolower(x)
[1] "we have a dream"
> toupper(x)
[1] "WE HAVE A DREAM"
```



# strsplit()

```
> strsplit(x,split=" ")
[[1]]
[1] "we"    "have"  "a"     "dream"
```

공백 문자로 구분된 각각의 단어들로 구성된 벡터가 리스트에 들어가있음 ! 



```
> strsplit(x,split="")
[[1]]
 [1] "w" "e" " " "h" "a" "v" "e" " " "a" " " "d" "r" "e" "a" "m"
```



```
> unlist(strsplit(x,split=" "))
[1] "we"    "have"  "a"     "dream"

> res<-strsplit(x, split=" ")[[1]]
> res[4]
[1] "dream"
```



```
x1<-"we have a dream"
x2<-"How are you"
x3<-"I am fine"
myword<-c(x1,x2,x3)

> length(myword)
[1] 3

> strsplit(myword," ")
[[1]]
[1] "we"    "have"  "a"     "dream"

[[2]]
[1] "How" "are" "you"

[[3]]
[1] "I"    "am"   "fine"
```



대소문자 구분됨

단어 통일 korea Korea KOREA 한국 대한민국 조선=> 우리나라

```
#unique() : 유일한 단어를 추출
unique(said.word)
unique(said.word[[1]])
unique(tolower(said.word[[1]])) #is 하나 걸러짐

```



# paste

: 분리된 벡터를 결합하는 함수, 벡터의 원소들을 분리한 다음 결합하지 않는다



```
> paste("Everybody","wants","to","fly")
[1] "Everybody wants to fly"

> paste(c("Everybody","wants","to","fly"))
[1] "Everybody" "wants"     "to"        "fly" 
```



```
said<-"WHAT IS ESSENTIAL is invisible to the Eye"
strsplit(said," ") #리스트
res<-strsplit(said," ")[[1]] #벡터
res
paste(res)
```

이건 붙지 않음



```
#기본값으로 공백문자
> paste("Everybody","wants","to","fly")
[1] "Everybody wants to fly"

> paste("Everybody","wants","to","fly", sep="-")
[1] "Everybody-wants-to-fly"
```

`sep=""`이면 따닥따닥 붙음

```
paste(pi,sqrt(pi))
[1] "3.14159265358979 1.77245385090552"
```



numeric도 텍스트로 변환한 다음 결합된다

```
paste("aaa",1+2,"bbb") #1+2결과 3이 문자열로 변경된 후 paste수행
[1] "aaa 3 bbb"
```



같은거 반복 늘리기

```
paste("type", 1)
> paste("type", 1:5)
[1] "type 1" "type 2" "type 3" "type 4" "type 5"

c(1,2,3,4,5)
c("type")#길이 1 -> 길이5로 변경됨 
```



```
heros<-c("Batman","Captain America","Hulk")

> paste(heros,"wants")
[1] "Batman wants"          "Captain America wants"
[3] "Hulk wants" 
> paste(heros,"wants","to")
[1] "Batman wants to"          "Captain America wants to"
[3] "Hulk wants to"  
```



paste함수 collapse옵션: 텍스트 결합을 통해 생성된 텍스들을 다시 하나로 연결하는 구분자 정의 

```
> paste(c("Everybody","wants","to","fly"), collapse=" ")
[1] "Everybody wants to fly"
```



```
> paste(heroes,"wants","to","fly", collapse=", and ")
[1] "Batman wants to fly, and Captain America wants to fly, and Hulk wants to fly"

> paste(heroes,"wants","to","fly", sep="-",collapse=";")
[1] "Batman-wants-to-fly;Captain America-wants-to-fly;Hulk-wants-to-fly"
```



# outer()

: 두 집합에 대해 가능한 모든 순서쌍의 곱을 수행한다 (카티전 곱: default)



```
> outer(c(1,2,3), c(3,2,1))
     [,1] [,2] [,3]
[1,]    3    2    1
[2,]    6    4    2
[3,]    9    6    3
```



outer+paste 함수를 결합해서 문자열 생성

outer함수의 3번째 자리에 인수자리에 함수를 작성하여 모든 순서쌍에 대해 카티전 곱이 아닌 다른 작업을 수행할 수 있게됨

```
asia.countries<-c("Korea","China","India")
info<-c("GDP","Population","Area")
outer(asia.countries, info, paste)

     [,1]        [,2]               [,3]        
[1,] "Korea GDP" "Korea Population" "Korea Area"
[2,] "China GDP" "China Population" "China Area"
[3,] "India GDP" "India Population" "India Area"
```

outer 3번째 인수자리에  `FUN = "*"` 처럼 함수



```
out<-outer(asia.countries, info,paste, sep="-")
#as.vector() : 행렬 -> 벡터 형식
> as.vector(out)

[1] "Korea-GDP"        "China-GDP"        "India-GDP"       
[4] "Korea-Population" "China-Population" "India-Population"
[7] "Korea-Area"       "China-Area"       "India-Area"  
```



```
res<-outer(asia.countries,asia.countries, FUN=paste, sep="-")
res
lower.tri(res)
> res[lower.tri(res)] #하 삼각만 추출
[1] "China-Korea" "India-Korea" "India-China"

res[!lower.tri(res)] #not도 가능
```



# substr

 : 텍스트의 특정 부분 문자열 추출

```
substr("Data Analytics", 1,4)
substr("Data Analytics", 6,14)
```
# substring 

:  텍스트의 특정 부분 문자열 추출, 끝위치 생략

```
substring("Data Analytics",6)

> myclass<-c("Data Analytics","Data Mining","Data Visualization")

> substr(myclass, 1,4)
[1] "Data" "Data" "Data"

> substr(myclass, nchar(myclass)-5,nchar(myclass))
[1] "lytics" "Mining" "zation"
```



# grep

특정 텍스트의 인덱스



```
islands #섬 + 개수
landmasses<-names(islands)
landmasses

#New단어가 포함된 단어의 인덱스를 추출
index<-grep(pattern="New", x=landmasses)
landmasses[index]

grep(pattern="New", x=landmasses, value=TRUE) #귀찮으면 한번에

```



# sub(), gsub()

 : 문자열 검색 -> 다른 문자열 변경

`sub()` : 처음 문자열 1개만 다른 문자열 변경

`gsub() ` : 일치하는 모든 문자열을 다른 문자열로 변경



```
> txt<-"Data Anal is useful. Data Anal is intersting."

> sub(pattern ="Data", replacement=" Business", txt)
[1] " Business Anal is useful. Data Anal is intersting."

> gsub(pattern ="Data", replacement=" Business", txt)
[1] " Business Anal is useful.  Business Anal is intersting."
```



# 주식차트📈



```
df<-read.csv("005930.KS.csv", header=TRUE, sep="," ) #defaul 설정 이라서 위아래 똑같은 결과이다.

df2<-read.csv("005930.KS.csv")
```

```
read.csv("005930.KS.csv", header=FALSE, sep="," ) #머릿말?? 안나옴
```















