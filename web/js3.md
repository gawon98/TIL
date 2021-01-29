# 버튼 클릭

버튼을 클릭했을때, 메시지가 출력

```
<body>
<h1>JavaScript</h1>
<script>

document.write("hello world");
document.write(2+3);

</script>
2+3

<input type="button" value="click me">
</body>
</html>
```

~했을 때에 해당되는 자바스크립트 이벤트를 지정하는 속성명은 접두어가 on으로 시작되는 함수를 정의하여 이벤트 처리

속성명 = on + "이벤트명"

ex) onclick = 클릭했을때 

```
<input type="button" value="click me" onclick="alert('why click me?')">
```



# text 상자

in body

```
<input type="text"/> 
```

```
<input type="text" onclick="alert('why click text?')" />
```

텍스트 상자 처음 한번 누를때면 하고싶지 않을까



```
<input type="text" onchange="alert('changed')"/>
```

입력하고 엔터하면 뜸



```
PW:<input type="text" onkeydown="alert('key down')"/>
```

key(보드)  키 눌리자마자 출력됨 

```
PW:<input type="text" onkeyup="alert('key down')"/>
```

눌렀다 떼는 순간 뜸 

```
PW:<input type="text" onkeypress="alert('key down')"/>
```

누르면 나옴! 다운과 같다



주로 키 다운을 쓴다 구분없이

------------

# 속성

```
//length, ... : 어트리뷰트 == 프로퍼티 ==속성
//alert() , ...: 함수 == 메서드
```



```
alert("hello world".toUpperCase());
```

대문자로 출력된다



```
alert("hello world".indexOf('o'));
```

"hello world"의 문자열에서'o' 의 인덱스는?

없는 문자라면 -1 이 출력된다. 

문자 찾을때 if 저 값이 -1이라면 ==> 없다. 

```
alert("hello world".indexOf('hello'));
```

출력 ==> 0

단어의 시작위치가 나온다.



```
document.write("&nbsp&nbsp&nbsphi&nbsp&nbsp&nbsphello   ");
```

&nbsp : 공백 





```
<html>
    <head>
        <title>WEB1 - JavaScript</title>
        <meta charset="utf-8">
    </head>
    <body>
        <h1><a href="index.html">WEB</a></h1>
    </body>
</html>
```

앵커태그로 연결



```
   #first{
        color:green;
        }
        span{
        color:blue;
        }



    </style>
</head>
<body>
<span id="first">my script</span>
```

id가 앞서서 녹색으로 적용된다

class는 여러번되는데 id는 중복 x



버튼클릭했을때 이벤트 (배경색 바꾸기)

```
<input type="button" value="black" onclick="document.querySelector('body').style.backgroundColor='black';">
```

document 현재 문서 대소문자 구분유의



글자색 배경색 모두 바꾸기

```
<input type="button" value="black" onclick="
document.querySelector('body').style.backgroundColor='black';
document.querySelector('body').style.color='white';">


<input type="button" value="white" onclick="
document.querySelector('body').style.backgroundColor='white';
document.querySelector('body').style.color='black';">
    
<h1>javascript<</h1>
<p>java script html css</p>
```



```
<h1>1==1</h1>
<script>

    document.write(1==1);
    document.write(1===1);

</script>
```

스크립트 안에만 논리형 true로 나옴 비교연산자로 사용된다는 뜻

= 2개, 3개 같은 의미 



&gt

&lt



```
//black버튼을 클릭했을 때, myblack이라는 아이디를 갖고있는 대상의 value가
  black과 같다면
  <input id="myblack" type="button" value="black" onclick="
  if (document.querySelector('#myblack').value=='black'){
      document.querySelector('#myblack').value = 'white'

  document.querySelector('body').style.backgroundColor='black';
  document.querySelector('body').style.color='white';
  }

  else{
  document.querySelector('body').style.backgroundColor='white';
  document.querySelector('body').style.color='black';
  }
  ">
```



```
    <input type="button" value="black" onclick="
var target=document.querySelector('body');
if(this.value=='black'){
target.style.backgroundColor='black';
target.style.color='white';
this.value='white';
} else {
target.style.backgroundColor='white';
target.style.color='black';
this.value='black';
}
">


    <h1>javascript</h1>
    <p>java script html css</p>
```

this의 의미는 이벤트의 주체 (여기선 클릭이벤트) 클릭을 버튼에서 했으니까 버튼이 this

