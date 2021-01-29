

# Review

중앙값

```
import statistics
list=[100,200,50,90,300]
print(statistics.median(list))
```



----

클래스는 실체가 없다

함수 명명법 : 속성의 값 가져올때 get~ ,인지 아닌지는 is~ , 속성을 설정하는 함수 set~

처리 연산 proc ~

this로 넘겨주면 self로 받는다!

body 태그를 찾아서 

(졸려서 못들음)

----------

# 객체

객체 -> 딕셔너리로 표현 (순서x) , 중괄호 사용

객체생성 객체명은 coworkers

```
<script>
var coworkers={
"programmer":"kim",
"designer":"Lee"
}
document.write("개발자명:"+coworkers.programmer);
</script>
```

속성명(딕셔너리 키) : 값 

접근 .

새로운 속성 추가 -아마 공백가능

```
coworkers["datascientist"]="park";
document.write("데이터과학자:"+coworkers.datascientist+"<br>");
```

 속성 추가 (2) - 아마 불가능

```
coworkers.datascientist="park";
document.write("데이터과학자:"+coworkers.datascientist+"<br>");
```



속성 키:밸류 출력하기

```
for(var k in coworkers){ //k는 key가 저장됨
document.write(k+":" +coworkers[k]+"<br>");
```



```
<h2> 객체에 메서드(함수) 정의</h2>
coworkers.showAll = function(){
//객체명.함수명
}
```







```
<script>
coworkers.showAll = function(){
    for(var k in coworkers){
    document.write(k+":" +coworkers[k]+"<br>");

    }
}
coworkers.showAll();

</script>
```

coworkers로 고정하지말고 메서드 안에서

this 대상으로 받아야됨

--> 수정

```


```





```
var Body = {
    setBackgroundColor:function(color){
    }
}
```

객체가 갖는 속성,메서드 정의

하고 부를때 

```
Body.setBackgroundColor('black');
```

쩜으로 그럼 위의 메서드 호출된다





```
<script>
    var person={
        name:"kim",
        hello:function(msg){
        document.write("say hello"+msg);
        }
    }

    //person.hello();
    //document.write(person.name)
    person.hello("world");


</script>
```



# 정규표현식

표현방법 두가지

1)

```
<script>
    var re=/ab+c/; //정규표현식을 슬래쉬로 감싸는 방법으로 표현
```

2)RegExp객체 생성 방법으로 표현 

```
var re=RegExp("ab+c")
```



예시

```
/Chapter(\d+) / //숫자가 하나이상 온다
```

챕터3, 챕터4 요런식

```
/Chapter(\d+)\.\d* / //예 챕터3.숫자많이 
```



```
/abc/
```

이순서 그대로 abc 포함하면 매치



```
/ab*c/   //cbbabbbbc --> 'abbbbc'
```



```
var myRe=/cdb{2}d*/;
var myArray = myRe.exec("cdbbdddddbsbz");
document.write(myArray);
```

출력>> cdbbddddd



```
document.write(/abc/.exec("this is abc")+"<br>");
document.write(/abc/.exec("this is ab c")+"<br>");

document.write(/a\d/.exec("ab")+"<br>");
document.write(/a\d/.exec("a1b")+"<br>");
```

abc
null
null
a1




// 특수문자 앞에 역슬래쉬(\) : 특수문자를 단순문자로 해석

```
document.write(/a\*/.exec("aaaaa")+"<br>");
document.write(/a\*/.exec("a*aaaa")+"<br>");
```

출력 >>

 null
a*

^ : 그 문자로 시작

```
document.write(/^A/.exec("an E")+"<br>");
document.write(/^A/.exec("An E")+"<br>");
```

null
A



[^A] : 대괄호 --> 대문자 A가 아니면 매치

```
document.write(/[^0-9]+/.exec("An E")+"<br>");
```

An E



끝에 오는 문자랑 매치 `$`

```
document.write(/t$/.exec("eat")+"<br>");
```



파이썬이랑 다른

소괄호안에 -> 패턴을 내부적으로 저장했다가 매치 

```
  document.write(/(zoo)(bar)/.exec("zoo test bar")+"<br>");
    document.write(/(zoo) (bar)/.exec("zoo bar test")+"<br>");
    document.write(/(zoo) (bar)/.exec("zoo test bar")+"<br>");

```

null

zoo bar,zoo,bar // 전체 나오고 ,zoo 따로, bar 따로 출력
null