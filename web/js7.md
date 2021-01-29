# 마우스 클릭 이벤트

`click` : 클릭했을 때 발생하는 이벤트. 
`dblclick` : 더블클릭을 했을 때 발생하는 이벤트
`mousedown` :마 우스를 누를 때 발생
`mouseup` : 마우스버튼을 땔 때 발생
`mousemove` : 마우스를 움직일 때
`mouseover` :마우스가 엘리먼트에 진입할 때 발생
`mouseout` : 마우스가 엘리먼트에서 빠져나갈 때 발생
`contextmenu` : 컨텍스트 메뉴가 실행될 때 발생



실습 : 녹색박수 -> 이벤트 발생 ->이벤트 발생된 위치 정보를 출력

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
            body{
                background-color: black;
                color:white;
            }
            #target{
                width:200px;
                height:200px;
                background-color: green;
                margin:10px;
            }
            table{
                border-collapse: collapse;
                margin:10px;
                float: left;
                width:200px;
            }
            td, th{
                padding:10px;
                border:1px solid gray;
            }
        </style>

</head>

<body>
<div id="target">

        </div>
<table>
            <tr>
                <th>event type</th>
                <th>info</th>
            </tr>
<tr>
                <td>click</td>
                <td id="elmclick"></td>
            </tr>
            <tr>
                <td>dblclick</td>
                <td id="elmdblclick"></td>
            </tr>
            <tr>
                <td>mousedown</td>
                <td id="elmmousedown"></td>
            </tr>
            <tr>
                <td>mouseup</td>
                <td id="elmmouseup"></td>
            </tr>
            <tr>
                <td>mousemove</td>
                <td id="elmmousemove"></td>
            </tr>
            <tr>
                <td>mouseover</td>
                <td id="elmmouseover"></td>
            </tr>
            <tr>
                <td>mouseout</td>
                <td id="elmmouseout"></td>
            </tr>
            <tr>
                <td>contextmenu</td>
                <td id="elmcontextmenu"></td>
            </tr>
        </table>
<table>
            <tr>
                <th>key</th>
                <th>info</th>
            </tr>
            <tr>
                <td>event.altKey</td>
                <td id="elmaltkey"></td>
            </tr>
            <tr>
                <td>event.ctrlKey</td>
                <td id="elmctrlkey"></td>
            </tr>
            <tr>
                <td>event.shiftKey</td>
                <td id="elmshiftKey"></td>
            </tr>
        </table>
<table>
            <tr>
                <th>position</th>
                <th>info</th>
            </tr>
            <tr>
                <td>event.clientX</td>
                <td id="elemclientx"></td>
            </tr>
            <tr>
                <td>event.clientY</td>
                <td id="elemclienty"></td>
            </tr>
        </table>
<script>
    var t = document.getElementById('target'); //녹색박스
    //alert(t);

     //핸들러 함수는 등록된 이벤트 발생될 때마다 호출됨

    function handler(event){
    //alert("핸들러")
    //alert(event.type);

    var info = document.getElementById("elm"+event.type)//이벤트가 발생된 아이디
    var time=new Date(); //date객체 생성
    var timestr=time.getMilliseconds();
    info.innerHTML=(timestr);

    if (event.altKey){
    document.getElementById("elmaltkey").innerHTML = timestr
    }
    if (event.shiftKey){
    document.getElementById("elmshiftKey").innerHTML = timestr //얘 대문자
    }
    if (event.ctrlKey){
    document.getElementById("elmctrlkey").innerHTML = timestr
    }

   // document.getElementById("elemclientx").innerHTML = event.clientX; //브라우저가 기준축
   // document.getElementById("elemclienty").innerHTML = event.clientY;

    document.getElementById("elemclientx").innerHTML = event.offsetX; //박스 모서리가 기준축
    document.getElementById("elemclienty").innerHTML = event.offsetY;
    };

    t.addEventListener("click",handler); //t가 클릭이벤트를 인지할 수 있게 리스너를 추가->반응 handler
    t.addEventListener("dblclick",handler);
    t.addEventListener("mousedown",handler);
    t.addEventListener("mouseup",handler);
    t.addEventListener("mouseover",handler);
    t.addEventListener("mousemove",handler);
    t.addEventListener("mouseout",handler);
    t.addEventListener("contextmenu",handler);
    //Event는 외부의 입력(보여지는것, 전해지는 것... -> 입력),
    //Listener입력을 인식 할 수 있는것을 add t에게 추가


</script>

</body>

</html>
```



# 회원가입 

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>회원가입</title>
    <script>
    window.onload=function(){
    frm.id.focus();

}
    </script>
</head>
<body>
<form name="frm">
    <fieldset>
        <legend>회원가입</legend>
        <table>
        <tr>
            <td>ID</td>
            <td><input type="text" id="id" name="id"></td>
        </tr>
        <tr>
            <td>PW</td>
            <td><input type="password" id="pw1" name="pw1">
                    PW확인
            <input type="password" id="pw2" name="pw2">
            </td>
        </tr>
        <tr>
            <td>성별</td>
            <td>남<input type="radio" name="gender" value="male">
            여<input type="radio" name="gender" value="female"></td>
        </tr>

        <tr>
            <td>취미</td>
            <td>
            <input type="checkbox" name="hobby" value="soc">
               축구
           <input type="checkbox" name="hobby" value="bb">
                야구
           <input type="checkbox" name="hobby" value="sw">
                수영
           <input type="checkbox" name="hobby" value="ba">
                농구
           </td>
        </tr>

            <tr>
            <td>생년월일</td>
                <td><input type="date" name="birth" id="birth"></td>

        </tr>

        <tr>
            <td>현재나이</td>
            <td><input type="text" name="age" id="age"></td>
        </tr>


        <tr>
            <td>이메일</td>
           <td><input type="text" name="email" id="email">@
               <select id="url" >
                <option>naver.com</option>
                <option>daum.net</option>
                <option>google.com</option>
               </select></td>
        </tr>
        <tr>
            <td>자기소개</td>
            <td><textarea id="memo" rows="5" cols="50">
            </textarea>
            </td>
        </tr>

        <tr>
            <td colspan="2">
                <input type="button" id="signup" value="signup">
                <input type="button" id="reset" value="reset">
            </td>
        </tr>

        </table>

    </fieldset>

</form>
</body>
</html>
```







## 시간 뽑아내기

```
<script>
    var date1=new Date();
    //alert(date1);
    //alert(date1.getFullYear()-5);
    //alert(date1.getMonth()+1); //주의 0부터 시작함
    //alert(date1.getDate()); //
    //alert(date1.getDay());
    alert(date1.getHours());

</script>
```



## 문자 인덱싱 참조

```
var s="hello";
document.write(s.charAt(1)); //0부터 시작
```

```
s2="123";
document.write(s2+10+"<br>");
document.write(parseInt(s2)+10+"<br>");

s3="a123";
document.write(parseInt(s3)+10+"<br>");
```

12310
133
NaN