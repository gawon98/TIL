# map 함수

```
map(함수, 자료)
```

퀴즈1

```
def twoTimes(n):
    return [2*i for i in n]
res=twoTimes([1,2,3])
print(res)
```



```
def twoTimes(n):
    return n*2

res=list(map(twoTimes,[1,2,3]))
print(res)
```

맵안에 람다 써서 더 간략하게 가능



# pow 

```
print(pow(3,2)) #9
print(3**2) #9
```

지수

# zip

```
print(list(zip([1,2],[3,4],[5,6],[7,8])))
```

[(1, 3, 5, 7), (2, 4, 6, 8)]

같은 번호 요소끼리 묶여서 출력된다



# filter

```
filter() : 특정 조건으로 걸러진 요소들을 묶어서 리턴
```

map과의 차이점 함수의 결과가 참/거짓에 따라 요소를 포함한지 결정



```
t=list(range(1,11))
#print(t)
print(list(filter(lambda t: t%2==0,t)))
# 내가 짠 코드

print(list(filter(lambda x: x%2==0,t))) #함수 이름 x로 ㄱㄴㄱㄴ
```



# os 모듈

: 디렉토리, 파일의 경로 등 확인/제어 

```
import os
print(os.environ)
print(os.getcwd()) #current working directory 확인
os.mkdir() #디렉토리 생성 함수
os.rename("sample","test") #폴더명 변경
```

```
#특정 폴더 내에 있는 폴더 또는 파일 목록을 조사
import glob
print(glob.glob("C:/Hye won Kim/PycharmProjects/pythonBasic/day*"))
```



```
print(glob.glob("C:/Users/akrnr/PycharmProjects/pythonBasic/*"))

```

모든 파일 출력은 *



# 웹프로그래밍

정규표현식 : 복잡한 문자열 처리에서 유용하게 사용가능



#뒷부분을 * 으로 만들기

```
#정규표현식
jumin="""
park 850101-1234567
kim 950202-2345678
"""
print(jumin)

for line in jumin.split("\n"): #줄마다 찢고
    for word in line.split(" "): #공백마다 자르기
        if len(word)==14:
            word = word[:6]+"-"+"*******"
            print(word)
```

문자열 할당이

word[4]= "*" 이런식으로 되지 않아서

번거롭게 더해주는 중

## isdit()

: 문자열이 숫자인지 아닌지를 T,F로 리턴

#만약 주민등록번호에 영어 들어가있는 이상한 값 거르기 위해

```
for line in jumin.split("\n"): #줄마다 찢고
    for word in line.split(" "): #공백마다 자르기
        if len(word)==14 and word[:6].isdigit() and word[7:].isdigit():
            word = word[:6]+"-"+"*******"
            print(word)
```



## 정규표현식 

```
import re #regular expression (정규표현식 모듈)
p = re.compile("(\d{6})[-]\d{7}") #정규식 작성
print(p.sub("\g<1>-*******",jumin))
```

소괄호는 그룹을 의미, \d -> digit 십진수 자릿수



park 850101-*******
kim 950202-*******

정상적인 주민번호에 대한 일반적인 규칙을 정의 (숫자6자리-숫자7자리)



```
re.match("패턴","문자열") #문자열이 패턴에 부합되나요?
```

질문에 대한 답변이 나오게된다.

문자열은 주어지니까 패턴을 정의하는게 중요!



```
"hello, world" #이 문자열에서 hello가 있는지 없는지

print(re.match("hello","hello, world"))

print(re.match("hi","hello, world")) #None


```

매치됨(출력) : <re.Match object; span=(0, 5), match='hello'>

매치안됨(출력) : None 

none은 거짓. 매치됨은 참.

```
if re.match("hello","hello, world"):
    print("주어진 hello,world 문자열은 hello패턴에 매치가 됐습니다.")
else:
    print("매치되지 않았습니다.")
```

(0,5) 매치되는 위치 



## search 특정 문자열이 맨앞/뒤 
문자열 맨 앞에 ^을 붙이면 특정 문자열이 맨 앞에 오는지
				끝에 $를 붙이면 특정 문자열 맨 끝에 오는지

```
print(re.search("^hello", "hello,world"))
print(re.search("world$", "hello,world"))
```

<re.Match object; span=(0, 5), match='hello'>

<re.Match object; span=(6, 11), match='world'>



```
#hello 또는 world 문자열이 포함되어 있는지 확인
print(re.match("hello|world","hello")) #or 가능

```

<re.Match object; span=(0, 5), match='hello'>



## 정규표현식 메타문자

메타 : 정보의 정보, 데이터의 데이터, ...

| () {} [] \ ? + * $ ^ ...

[] 메타문자 : 대괄호 안에는 어떤 문자도 올 수 있음

ex ) [abcdef] 의미? a,b, ... ,f 중에서 어떤 한 개의 문자와 매치

'a' 문자는 정규표현식에 매치됨

```
print(re.match("[abcdef]","a")) #매치됨
print(re.match("[abcdef]","g"))#매치안됨
print(re.match("[abcdef]","abc"))#매치됨

```

<re.Match object; span=(0, 1), match='a'>
None

<re.Match object; span=(0, 1), match='a'>

match는 앞에만 보고

search는 나올때까지 쭉 본다



## [from-to]
[a-d] 정규식 의미: [abcd]


```
print(re.match("[0-9]","1234")) #1234는 0~9 숫자에 해당
print(re.match("[0-9]*","1234")) #1234는 0~9 숫자에 해당 # * :문자 또는 숫자가 0개 이상있는지 확인함

print(re.match("[0-9]*","a1234")) # none아니다.a는 [0-9]범위는 아님 *이 있으므로 0개도 매칭된걸로 출력

```

<re.Match object; span=(0, 1), match='1'>

<re.Match object; span=(0, 4), match='1234'>

<re.Match object; span=(0, 0), match=''>



```
print(re.match("[0-9]+","1234"))
print(re.match("[0-9]+","12a34"))
print("="*50)
print(re.match("[0-9]+","a12a34")) #처음부터 a 매치안됨 뒤엔 보지도 않음
print(re.match("[0-9]*","a12a34")) #0개
```



<re.Match object; span=(0, 4), match='1234'>

<re.Match object; span=(0, 2), match='12'>

-----

None
<re.Match object; span=(0, 0), match=''>



### 문자

[a-z], [A-Z], [a-zA-Z] 대소문자 구분

`[^0-9]:`0-9숫자를 제외한(NOT) 문자 *주의 : 대괄호 안!



```
print(re.search("^hi", "hello, hi")) #문자열이 hi로 시작해야함
print(re.search("hi", "hello, hi"))
print(re.match("hi", "hello, hi")) #none
```

None
<re.Match object; span=(7, 9), match='hi'>
None



```
print(re.match("hello|hi|good", "hi"))
```

<re.Match object; span=(0, 2), match='hi'>

#"goodhi" 여도 앞까지 매치되니까 됨



```
print(re.match("[0-9]", "12a3bcd"))
```

match 앞에만 봄

<re.Match object; span=(0, 1), match='1'>

```
print(re.match("[0-9]*", "12a3bcd")) #2까지, 숫자가 0개 이상 있는 판단
print(re.match("[0-9]+", "12a3bcd")) #숫자가 1개 이상잇는지 판단

```

<re.Match object; span=(0, 2), match='12'>

<re.Match object; span=(0, 2), match='12'>



```
print(re.match("[a-z]*", "12a3")) #알파벳 문자가 0개 이상 있는지 판단
```

<re.Match object; span=(0, 0), match=''>



```
print(re.match("a*", "b")) 
print(re.match("b*", "b"))
```

*은 *앞에 있는 문자가 0개 이상 나왔을때  매치

a문자가 0 개 이상 있으면 매치

<re.Match object; span=(0, 0), match=''>
<re.Match object; span=(0, 1), match='b'>



```
print(re.match("a*b", "b")) #a문자가 0개 이상있고 b가 나오면 매치
```

<re.Match object; span=(0, 1), match='b'>



```
print(re.match("a+b", "aaaabb")) #aaaab까지만 매치
print(re.match("a+b+", "aaaaaabbbbbb")) #갯수 상관없이 매치
 
```

<re.Match object; span=(0, 5), match='aaaab'>
<re.Match object; span=(0, 12), match='aaaaaabbbbbb'>



#패턴이 문자열에 있는지만 보면 된다.



# 갯수세기 꿀팁

```
lis=["오늘","오늘","가원"]
d1={}
for word in lis:
    d1[word] = d1.get(word,0)+1
print(d1)
```