# review

1은 python마지막 날에

b* b없어도 상관없다

## 모스부호 문제

```
dic = {
    '.-':'A','-...':'B','-.-.':'C','-..':'D','.':'E','..-.':'F',
    '--.':'G','....':'H','..':'I','.---':'J','-.-':'K','.-..':'L',
    '--':'M','-.':'N','---':'O','.--.':'P','--.-':'Q','.-.':'R',
    '...':'S','-':'T','..-':'U','...-':'V','.--':'W','-..-':'X',
    '-.--':'Y','--..':'Z'
}


def morse(src):
    res=[]
    for word in src.split("  "): #입력된 문장에 저장된 단어의 수는 3개
        for c in word.split(" "): #문자가 저장
            res.append(dic[c]) #dic[c]가 key

        res.append(" ") #단어 공백으로 구분
    return "".join(res)

print(morse('.... .  ... .-.. . . .--. ...  . .- .-. .-.. -.--'))
```



## ngram

함수에서 함수 호출 + set 안쓰고 list로 for문 돌려서 해보기



```
def 입력()
    return 저장변수
def 처리()
    return 결과
def 출력()

입력데이터 변수 = 입력(데이터1,데이터2,...)
결과 = 처리(입력데이터 변수)
출력(결과)
```



```
def ngram(s,num):
    res=[]
    slen = len(s)-num+1
    for i in range(slen):
        ss=s[i:i+num]
        #print(ss)
        res.append(ss)
    return res

def diff_ngram(sa, sb, num):
    a=ngram(sa, num)
    b=ngram(sb,num)
    # print(a)
    # print(b)
    cnt =0 #일치한 단어의 개수를 저장하기 위한 변수
    r=[] #일치한 단어를 저장하기 위한 변수
    for i in a:
        for j in b:
            if i==j:#두 단어 (i,j)가 일치한다면
                cnt+=1
                r.append(i)
    return cnt/len(a), r

a="오늘 멀티캠퍼스에서 너무 쉬운 프로그래밍을 공부했다."
b="멀티캠퍼스에서 공부했던 오늘의 프로그래밍은 너무 쉬웠다."

r2, word2 = diff_ngram(a,b,2)
print("2-gram", r2,word2) #유사도, bigram으로 묶인 단어셋

r3, word3 = diff_ngram(a,b,3)
print("3-gram", r3,word3) #유사도, bigram으로 묶인 단어셋
```

수정 사항

1) 중복 허용 안되도록

2) 두 문장에서 길이가 긴 문장의 단어 개수를 분모로

 

# 메타문자

* 복습

```
[a-zA-Z] #모든문자
[^0-9] : [not 0-9] 대괄호 안 꺽쇠

\d : 숫자([0-9]) 와 같은 의미
\D : not \d의 의미 , [^0-9] 과 같음.

\s : 공백문자, 탭문자, 엔터문자 등 
\S : NOT  공백문자, 탭문자, 엔터문자 등 

\w : 문자 + 숫자를 의미, [a-zA-Z0-9_]과 같다 (언더바까지 포함)
\W : NOT 문자 + 숫자를 의미 [^a-zA-Z0-9_] 
 * 꺽쇠 앞에 있으면 대괄호 안 전체에 영향

```



## ?   .

? 또는 .   : 문자가 1개만 있는지 판단
? 는 문자가 0개 또는 1개 있으면 매치 {0,1} =최소 0개 이상 최대 1개 있어도 되고 없어도 된다.

`ab?c` : a+b가 있어도 없어도 됨 +c

. 은 모든 문자가 1개를 의미함



```
print(re.match('h?', 'h')) # h뒤에 없든있든  없네? 매치
print(re.match('h?', 'he')) # 있든없든 있으니까 매치
print(re.match('h?', 'his'))
print(re.match('ab?c', 'ac')) #b가 없든없든 -> 없 ->매치
print(re.match('ab?c', 'abbc')) #none 매치안됨, 최대1개


print(re.match('h.', 'hello')) #e까지 매치
print(re.match('a.b','aab')) #a다음에 모든문자 => 매치
print(re.match('a.b','a0b')) #매치
print(re.match('a.b','ab'))#None 사이에 아무것도 없어서

print(re.match('a[.]b','abb')) #None 대괄호 안에 있는 문자가 반드시 한개는 나와야됨 이때 [.] 은 특수문자(마침표) .을 의미하는 것

```

[]는 문자 한개 맨앞만 본다.

`"[123]+" , "32321"`  끝까지 매치

`"[123]+" , "3235217"` 5앞까지 매치 323만



## * +

`*` 0개 이상

```
print(re.match('do*g','dg')) #o가 0번 이상 반복 매치
print(re.match('do*g','dog')) #m
print(re.match('do*g','dooooog')) #m
print(re.match('do*g','doooookg')) #none 

```

`+` 1개 이상

```
print(re.match('do+g','dg')) #none
print(re.match('do+g','dog'))
print(re.match('do+g','dooooog'))
print(re.match('do+g','doooookg')) #none
```



# 반복 match

{최소, 최대} : 최소 횟수 이상, 최대 횟수 이하 반복

{최소,    }: 최소 횟수 이상 반복

{   , 최대}: 최대 횟수d 이하 반복

{숫자} : 숫자만큼 반드시 반복



```
print(re.match("do{2}g","dog"))  #none o2개 없음
print(re.match("do{2}g","doog"))
print(re.match("do{2}g","dooooooooog")) #none 너무많이 반복
```



```
print(re.match("do{2,5}g","dog"))  #none o문자가 2번이상 5번 이하 반복
print(re.match("do{2,5}g","doog"))
print(re.match("do{2,5}g","dooooooooog")) #none 5번초과
```



```
print(re.match("do{2,}g","dog")) #none
print(re.match("do{,2}g","dog")) 
print(re.match("do{,2}g","dooooog")) #none
```



# findall 

:정규식과 매치되는 모든 문자열을 **리스트로** 리턴



```
#예시
print(re.match("[a-z]+", "python"))

#뒤에 한줄이 밑에 세문장

pat = re.compile("[a-z]+") #정의한 패턴을 pat에 저장
res=pat.match("python") #패턴객체가(pat)가 가지고 있는 match함수를 이용하여 주어진 문자열이 패턴에 매치되는지 확인
print(res)
```



```
print(re.match("[a-z]+", "7python")) #None
print(re.search("[a-z]+", "7python"))
```

search 결과는 1개의 매치 객체가 리턴

```
print(re.findall("[a-z]+", "7python8java9cpp"))
```

#['python', 'java', 'cpp']

search는 전체를 보되 맨처음 만나는 문자열만 출력

findall은 매치되는 모든 문자열을 다 찾아오고, 리스트로 출력함





# finditer

:정규식과 매치되는 모든 문자열을 **반복가능한 객체** 형태로 리턴

(안중요)

```
res=re.finditer("[a-z]+", "7python8java9cpp") #반복 가능한 객체로 리턴

for i in res: #반복가능하니까 됨
    print(i)
```

<re.Match object; span=(1, 7), match='python'>
<re.Match object; span=(8, 12), match='java'>
<re.Match object; span=(13, 16), match='cpp'>



# 정규표현식 심화?

```
for i in res:
    print(i)
    print(i.start()) #매치 시작 위치 1
    print(i.end()) #매치 끝 위치:7
```



점(.) 예외 : \n

`.` 메타 문자는 줄바꿈 문자(`\n`)를 제외한 모든 문자와 매치되는 규칙이 있다. 만약 `\n` 문자도 포함하여 매치하고 싶다면 `re.DOTALL` 또는 `re.S` 옵션을 사용해 정규식을 컴파일하면 된다.

```
pat=re.compile("a.b",re.DOTALL) #\n문자도 포함
print(pat.match("a\nb"))
```

<re.Match object; span=(0, 3), match='a\nb'>v



```
pat=re.compile("[a-z]")
print(pat.match("python"))
print(pat.match("Python")) #NONE
print(pat.match("PYTHON"))#NONE
```



```
pat=re.compile("[a-z]", re.I) #I : ignorecase
print(pat.match("python"))
print(pat.match("Python"))
print(pat.match("PYTHON"))
```

ignore로 대소문자 구분안하고 매치!



-----



```
print(re.search("\section","kldsk sdf \section")) #\s는 엔터,공백 문자로 인식
print(re.search("\\\section","kldsk sdf \section")) #\s는 엔터,공백 문자
#역슬래쉬 세개?
print(re.search(r"\\section","kldsk sdf \section")) #\s는 엔터,공백 문자
#앞에 r하나 + 역슬래쉬 2개
```



```
# hi가 3번 반복되는지 보고싶으면???

print(re.match("(hi){3}","hihihihelloworld"))
```

hi{3}이면 hiii 니까 소괄호( hi )로 묶어주기!



돌고돌아 다시 전화번호

```
print(re.match("[0-9]{2,3}-[0-9]{3,4}-[0-9]{4}","02-1234-5678"))
```

자릿수 좀더 넓게



```
print(re.match("[ㄱ-ㅎ]+", "ㅋㅋㅋㅋ캬캬캬캬ㅋㅋㅋㅎㅎㅎ")) #캬부터 매치 x
```

```
print(re.match("[ㄱ-ㅎ가-힣]+", "ㅋㅋㅋㅋ캬캬캬캬ㅋㅋㅋㅎㅎㅎ")) #한글전체! 
```



```
print(re.findall("[ㄱ-ㅎ가-힣]", "ㅋㅋㅋㅋ캬캬캬캬ㅋㅋㅋㅎㅎㅎ")) #한글만 추출
print(re.findall("[^ㄱ-ㅎ가-힣]", "ㅋㅋㅋㅋ캬캬캬캬ㅋㅋㅋㅎㅎㅎ"))# 한글을 제외한 모든 문자 추출
```



## 뉴스에서 한글 뽑기

```
print(re.findall("[ㄱ-ㅎ가-힣]", news))
```

뒤에+ 붙이면 한글자 이상인 것 (단어단위)로 추출 



```
print(re.findall("[0-9]+[ㄱ-ㅎ가-힣]+",news))
```

3차, 1천명 처럼 숫자+한글



`[0-9]+[명]+ `: ~명

`[0-9]+[명|천]+ `: or 가능!



```
print(re.match("[0-9]+", 'hello119')) #none

print(re.search("[0-9]+$", 'hello119'))#match
```

달러 : `$`는 문자열의 마지막을 의미한다 `python$`이라면 문자열의 마지막은 항상 python으로 끝나야 매치된다는 의미이다.

```
print(re.search("\*",'3*5')) #특수문자는 앞에 역슬래쉬
print(re.search("[*]+",'3**5'))
print(re.search("\**", '3****5'))
```



```
특문 괄호 전체출력?

print(re.search("\$\([a-z]+\)", "$(document)"))
print(re.search("[$()a-z]+", "$(document)")) #대괄호가 편하다

```

## group

: 매치된 문자열을 돌려준다

```
res=re.search("\w+\s+\d+[-]\d+[-]\d+", "kim 010-1234-1234")
print(res.group())
print(res.group().split()[0]) #일케안씀
```



```
res=re.search("(\w+)\s+(\d+[-]\d+[-]\d+)", "kim 010-1234-1234")
#print(res)
#print(res.group().split()[0])
print(res.group(0))
print(res.group(1))
```

소괄호가 그룹하나! `(\w)`으로 묶고 뽑기

kim 010-1234-1234
kim



```
res=re.search("(?P<name>\w+)\s+(\d+[-]\d+[-]\d+)", "kim 010-1234-1234")
print(res.group('name'))
```



#작성형식 : (?P<그룹명>...)







