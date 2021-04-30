코랩?
클라우드 기반 주피터 노트북 개발 환경 (무료)
gpu가 없거나 딥러닝 or 인공지능 할라면 성능 좋아야됨
협업가능
데이터, 코드는 구글 드라이브에 저장 (15기가)

시리즈, 데이터 프레임 많이사용
시리즈: 1차원 배열과 같은 자료구조, 다양한 자료를 저장, index를 가지고 있음, 배열로 부터 생성  
가나다라  
마바사


```python
import pandas as pd
```


```python
from pandas import Series, DataFrame
```


```python
import numpy as np
import matplotlib.pyplot as plt
```

# Series



```python
obj=Series([3,1,-5,2]) #시리즈
obj
```




    0    3
    1    1
    2   -5
    3    2
    dtype: int64




```python
obj.values
```




    array([ 3,  1, -5,  2], dtype=int64)




```python
obj.index
```




    RangeIndex(start=0, stop=4, step=1)



인덱스는 저장된 데이터의 이름(번호)  
인덱스는 행/열 인덱스가 있음
인덱스를 이용하여 자료를 참조 



```python
obj=pd.Series([3,1,-5,2], index=['d','a','b','c'])  
obj
obj.index
```




    Index(['d', 'a', 'b', 'c'], dtype='object')




```python
obj['b']
obj['c']=9
obj
```




    d    3
    a    1
    b   -5
    c    9
    dtype: int64




```python
#여러개를 참조할때 대괄호 무조건 2개
obj[['c','a']]
```




    c    9
    a    1
    dtype: int64




```python
obj
```




    d    3
    a    1
    b   -5
    c    9
    dtype: int64




```python
obj>0
```




    d     True
    a     True
    b    False
    c     True
    dtype: bool




```python
obj[obj>0]
obj*2 #모든 원소에 각각 곱해진다
np.exp(obj) #지수승
#k 라는 인덱스가 있나요?
'k' in obj #False
'a' in obj #T
```




    True



## 딕셔너리로 생성하는 시리즈


```python
sdata={'Seoul':1000, 'Incheon':200, 'Gwangju':100,'Busan':300}
obj2=pd.Series(sdata)
obj2
```




    Seoul      1000
    Incheon     200
    Gwangju     100
    Busan       300
    dtype: int64




```python
obj2['Gwangju']
```




    100




```python
cities=['Seoul','Incheon','Suwon','Daejeon']
obj4=pd.Series(sdata, index=cities)
obj4
```




    Seoul      1000.0
    Incheon     200.0
    Suwon         NaN
    Daejeon       NaN
    dtype: float64




```python
pd.isnull(obj4) 
pd.notnull(obj4)
obj4.isnull()

```




    Seoul      False
    Incheon    False
    Suwon       True
    Daejeon     True
    dtype: bool




```python
obj2
```




    Seoul      1000
    Incheon     200
    Gwangju     100
    Busan       300
    dtype: int64




```python
for k,v in obj2.items():
    print(k, v)
```

    Seoul 1000
    Incheon 200
    Gwangju 100
    Busan 300



```python
obj2['Jeju']=50
```


```python
obj2
```




    Seoul      1000
    Incheon     200
    Gwangju     100
    Busan       300
    Jeju         50
    dtype: int64




```python
del obj2['Incheon']
```

# 데이터프레임
1) 열이 되는 1차원 리스트 또는 array를 작성함  
2) 열에 대한 이름을 키로 갖는 딕셔너리를 작성   
3) 행 인덱스는 0부터 자동으로 붙는다. 이름을 직접 주고싶으면  index 옵션에 붙여주기




```python
data = {
    "2015": [9904312, 3448737, 2890451, 2466052],
    "2010": [9631482, 3393191, 2632035, 2431774],
    "2005": [9762546, 3512547, 2517680, 2456016],
    "2000": [9853972, 3655437, 2466338, 2473990],
    "지역": ["수도권", "경상권", "수도권", "경상권"],
    "2010-2015 증가율": [0.0283, 0.0163, 0.0982, 0.0141]
} #6개
cols = ["지역", "2015", "2010", "2005", "2000", "2010-2015 증가율"]
idx = ["서울", "부산", "인천", "대구"]

```


```python
#pd.Series(data)
df=pd.DataFrame(data, index= idx, columns=cols)
#col 안해줘도 맞아 떨어져서 상관없음
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>지역</th>
      <th>2015</th>
      <th>2010</th>
      <th>2005</th>
      <th>2000</th>
      <th>2010-2015 증가율</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>서울</th>
      <td>수도권</td>
      <td>9904312</td>
      <td>9631482</td>
      <td>9762546</td>
      <td>9853972</td>
      <td>0.0283</td>
    </tr>
    <tr>
      <th>부산</th>
      <td>경상권</td>
      <td>3448737</td>
      <td>3393191</td>
      <td>3512547</td>
      <td>3655437</td>
      <td>0.0163</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>수도권</td>
      <td>2890451</td>
      <td>2632035</td>
      <td>2517680</td>
      <td>2466338</td>
      <td>0.0982</td>
    </tr>
    <tr>
      <th>대구</th>
      <td>경상권</td>
      <td>2466052</td>
      <td>2431774</td>
      <td>2456016</td>
      <td>2473990</td>
      <td>0.0141</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.index.name="도시"
df.columns.name="특징"
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>특징</th>
      <th>지역</th>
      <th>2015</th>
      <th>2010</th>
      <th>2005</th>
      <th>2000</th>
      <th>2010-2015 증가율</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>서울</th>
      <td>수도권</td>
      <td>9904312</td>
      <td>9631482</td>
      <td>9762546</td>
      <td>9853972</td>
      <td>0.0283</td>
    </tr>
    <tr>
      <th>부산</th>
      <td>경상권</td>
      <td>3448737</td>
      <td>3393191</td>
      <td>3512547</td>
      <td>3655437</td>
      <td>0.0163</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>수도권</td>
      <td>2890451</td>
      <td>2632035</td>
      <td>2517680</td>
      <td>2466338</td>
      <td>0.0982</td>
    </tr>
    <tr>
      <th>대구</th>
      <td>경상권</td>
      <td>2466052</td>
      <td>2431774</td>
      <td>2456016</td>
      <td>2473990</td>
      <td>0.0141</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['2010-2015 증가율']

```




    도시
    서울    0.0283
    부산    0.0163
    인천    0.0982
    대구    0.0141
    Name: 2010-2015 증가율, dtype: float64






```python
#2005~2010 증가율 컬럼 추가 (2010-2005)/2005 *100
#특성 공학
df['2005-2010 증가율']=((df['2010']-df['2005'])/df['2005']*100).round(2)
type(df['지역']) #시리즈
type(df)
type(df[['지역']]) #dataframe 대괄호 2개

```




    pandas.core.series.Series




```python
type(df[['2010','2015']]) #데이터프레임 여러개니까
```




    pandas.core.frame.DataFrame




```python
df2=pd.DataFrame(np.arange(12).reshape(3,4)) #정수인덱스
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>



## 추출


```python
df2[2] #우왕 2열이 나온다! 시리즈 형식으로 출력됨
df2[[1,2]] #열 인덱스 1번,2번 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>




```python
#행 단위 추출 -> 슬라이싱으로 [시작인덱스:끝인덱스-1]
df[:1] #0번행 인덱스 추출 
df[1:2] #2-1=1행 까지 추출 ==> 1번행 추출된다.
df[1:3]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>특징</th>
      <th>지역</th>
      <th>2015</th>
      <th>2010</th>
      <th>2005</th>
      <th>2000</th>
      <th>2010-2015 증가율</th>
      <th>2005-2010 증가율</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>부산</th>
      <td>경상권</td>
      <td>3448737</td>
      <td>3393191</td>
      <td>3512547</td>
      <td>3655437</td>
      <td>0.0163</td>
      <td>-3.40</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>수도권</td>
      <td>2890451</td>
      <td>2632035</td>
      <td>2517680</td>
      <td>2466338</td>
      <td>0.0982</td>
      <td>4.54</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['서울':] #키로 찾으면 콜론: 
df['부산':'대구'] #부산 ~ 대구까지 모든 행 추출
df['부산':'인천']
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>특징</th>
      <th>지역</th>
      <th>2015</th>
      <th>2010</th>
      <th>2005</th>
      <th>2000</th>
      <th>2010-2015 증가율</th>
      <th>2005-2010 증가율</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>부산</th>
      <td>경상권</td>
      <td>3448737</td>
      <td>3393191</td>
      <td>3512547</td>
      <td>3655437</td>
      <td>0.0163</td>
      <td>-3.40</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>수도권</td>
      <td>2890451</td>
      <td>2632035</td>
      <td>2517680</td>
      <td>2466338</td>
      <td>0.0982</td>
      <td>4.54</td>
    </tr>
  </tbody>
</table>
</div>




```python
#df에서 2000년도 인천 인구 추출
df['2000']['인천']
```




    2466338





## 파일 작성




```python
%%writefile sample1.csv
c1,c2,c3
1, 1.11, one
2, 2.22, two
3, 3.33, three
```

    Writing sample1.csv



```python
pd.read_csv("sample1.csv")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c1</th>
      <th>c2</th>
      <th>c3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1.11</td>
      <td>one</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2.22</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>3.33</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python
#sample2를 놓침
#pd.read_csv("sample2.csv", names=['c','c2','c3']) 열 이름 지정

#데이터프레임의 특정열을 행 인덱스로 사용하고자 한다면...
pd.read_csv("sample1.csv", index_col='c1')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c2</th>
      <th>c3</th>
    </tr>
    <tr>
      <th>c1</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>1.11</td>
      <td>one</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2.22</td>
      <td>two</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3.33</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python
#여러개의 공백 문자로 구분
%%writefile sample3.txt
c1        c2        c3        c4
0.179181 -1.538472  1.347553  0.43381
1.024209  0.087307 -1.281997  0.49265
0.417899 -2.002308  0.255245 -1.10515

pd.read_table("sample3.txt", sep="\s+")
```


      File "<ipython-input-111-7493db362a9d>", line 3
        c1        c2        c3        c4
                  ^
    SyntaxError: invalid syntax




```python
%%writefile sample4.txt
파일 제목: sample4.txt
데이터 포맷의 설명:
c1, c2, c3
1, 1.11, one
2, 2.22, two
3, 3.33, three
```

    Writing sample4.txt



```python
pd.read_csv("sample4.txt", skiprows=[0,1]) #0번 1번 행 index에 해당되는 자료를 skip
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c1</th>
      <th>c2</th>
      <th>c3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1.11</td>
      <td>one</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2.22</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>3.33</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.read_csv("sample4.txt", skiprows=2) #2줄까지 무시됨 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c1</th>
      <th>c2</th>
      <th>c3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1.11</td>
      <td>one</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>2.22</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>3.33</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python
%%writefile sample5.csv
c1, c2, c3
1, 1.11,
2,없음, two
누락, 3.33, three

```

    Overwriting sample5.csv



```python
df=pd.read_csv("sample5.csv", na_values=['누락','없음',' ']) #특정값 NaN으로
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c1</th>
      <th>c2</th>
      <th>c3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>1.11</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>NaN</td>
      <td>two</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>3.33</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python
#to_csv : 데이터 프레임을 csv로 저장
df.to_csv('sample6.csv')
```


```python
!type sample6.csv
```

    ,c1, c2, c3
    0,1.0,1.11,
    1,2.0,, two
    2,,3.33, three



```python
df.to_csv('sample6.csv')
```


```python
df.to_csv('sample7.txt', sep="|")
```


```python
!type sample7.txt
```

    |c1| c2| c3
    0|1.0|1.11|
    1|2.0|| two
    2||3.33| three



```python
df.to_csv('sample8.csv', na_rep='누락', encoding='euc-kr')
```


```python
!type sample8.csv
```

    ,c1, c2, c3
    0,1.0,1.11,누락
    1,2.0,누락, two
    2,누락,3.33, three



```python
df.index=['a','b','c'] #행인덱스 추가
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c1</th>
      <th>c2</th>
      <th>c3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.0</td>
      <td>1.11</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2.0</td>
      <td>NaN</td>
      <td>two</td>
    </tr>
    <tr>
      <th>c</th>
      <td>NaN</td>
      <td>3.33</td>
      <td>three</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.to_csv("sample9.csv", index=False, header=False) #행 인덱스 빼주기
#열 인덱스는 header로 false 하면 빠진다 
```


```python
df=pd.read_csv("https://gist.github.com/michhar/2dfd2de0d4f8727f873422c5d959fff5/raw/fa71405126017e6a37bea592440b4bee94bf7b9e/titanic.csv")
df

df=pd.read_csv("https://github.com/CSSEGISandData/COVID-19/raw/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv")
df

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Province/State</th>
      <th>Country/Region</th>
      <th>Lat</th>
      <th>Long</th>
      <th>1/22/20</th>
      <th>1/23/20</th>
      <th>1/24/20</th>
      <th>1/25/20</th>
      <th>1/26/20</th>
      <th>1/27/20</th>
      <th>...</th>
      <th>3/14/21</th>
      <th>3/15/21</th>
      <th>3/16/21</th>
      <th>3/17/21</th>
      <th>3/18/21</th>
      <th>3/19/21</th>
      <th>3/20/21</th>
      <th>3/21/21</th>
      <th>3/22/21</th>
      <th>3/23/21</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>Afghanistan</td>
      <td>33.939110</td>
      <td>67.709953</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>55985</td>
      <td>55985</td>
      <td>55995</td>
      <td>56016</td>
      <td>56044</td>
      <td>56069</td>
      <td>56093</td>
      <td>56103</td>
      <td>56153</td>
      <td>56177</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>Albania</td>
      <td>41.153300</td>
      <td>20.168300</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>117474</td>
      <td>118017</td>
      <td>118492</td>
      <td>118938</td>
      <td>119528</td>
      <td>120022</td>
      <td>120541</td>
      <td>121200</td>
      <td>121544</td>
      <td>121847</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>Algeria</td>
      <td>28.033900</td>
      <td>1.659600</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>115265</td>
      <td>115410</td>
      <td>115540</td>
      <td>115688</td>
      <td>115842</td>
      <td>115970</td>
      <td>116066</td>
      <td>116157</td>
      <td>116255</td>
      <td>116349</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>Andorra</td>
      <td>42.506300</td>
      <td>1.521800</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>11266</td>
      <td>11289</td>
      <td>11319</td>
      <td>11360</td>
      <td>11393</td>
      <td>11431</td>
      <td>11481</td>
      <td>11517</td>
      <td>11545</td>
      <td>11591</td>
    </tr>
    <tr>
      <th>4</th>
      <td>NaN</td>
      <td>Angola</td>
      <td>-11.202700</td>
      <td>17.873900</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>21380</td>
      <td>21407</td>
      <td>21446</td>
      <td>21489</td>
      <td>21558</td>
      <td>21642</td>
      <td>21696</td>
      <td>21733</td>
      <td>21757</td>
      <td>21774</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>269</th>
      <td>NaN</td>
      <td>Vietnam</td>
      <td>14.058324</td>
      <td>108.277199</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>...</td>
      <td>2554</td>
      <td>2557</td>
      <td>2560</td>
      <td>2567</td>
      <td>2570</td>
      <td>2571</td>
      <td>2572</td>
      <td>2572</td>
      <td>2575</td>
      <td>2575</td>
    </tr>
    <tr>
      <th>270</th>
      <td>NaN</td>
      <td>West Bank and Gaza</td>
      <td>31.952200</td>
      <td>35.233200</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>209304</td>
      <td>211602</td>
      <td>213791</td>
      <td>215984</td>
      <td>218061</td>
      <td>219912</td>
      <td>221391</td>
      <td>223638</td>
      <td>225976</td>
      <td>228044</td>
    </tr>
    <tr>
      <th>271</th>
      <td>NaN</td>
      <td>Yemen</td>
      <td>15.552727</td>
      <td>48.516388</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>2836</td>
      <td>2908</td>
      <td>2969</td>
      <td>3037</td>
      <td>3126</td>
      <td>3217</td>
      <td>3278</td>
      <td>3418</td>
      <td>3516</td>
      <td>3612</td>
    </tr>
    <tr>
      <th>272</th>
      <td>NaN</td>
      <td>Zambia</td>
      <td>-13.133897</td>
      <td>27.849332</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>84797</td>
      <td>84950</td>
      <td>85240</td>
      <td>85502</td>
      <td>85889</td>
      <td>86059</td>
      <td>86273</td>
      <td>86449</td>
      <td>86535</td>
      <td>86779</td>
    </tr>
    <tr>
      <th>273</th>
      <td>NaN</td>
      <td>Zimbabwe</td>
      <td>-19.015438</td>
      <td>29.154857</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>36484</td>
      <td>36504</td>
      <td>36535</td>
      <td>36552</td>
      <td>36611</td>
      <td>36652</td>
      <td>36662</td>
      <td>36665</td>
      <td>36684</td>
      <td>36717</td>
    </tr>
  </tbody>
</table>
<p>274 rows × 431 columns</p>
</div>



# 과제


```python
df=pd.read_csv("gapminder.tsv",sep="\t")
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>continent</th>
      <th>year</th>
      <th>lifeExp</th>
      <th>pop</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1952</td>
      <td>28.801</td>
      <td>8425333</td>
      <td>779.445314</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1957</td>
      <td>30.332</td>
      <td>9240934</td>
      <td>820.853030</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1962</td>
      <td>31.997</td>
      <td>10267083</td>
      <td>853.100710</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1967</td>
      <td>34.020</td>
      <td>11537966</td>
      <td>836.197138</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Afghanistan</td>
      <td>Asia</td>
      <td>1972</td>
      <td>36.088</td>
      <td>13079460</td>
      <td>739.981106</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1699</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>1987</td>
      <td>62.351</td>
      <td>9216418</td>
      <td>706.157306</td>
    </tr>
    <tr>
      <th>1700</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>1992</td>
      <td>60.377</td>
      <td>10704340</td>
      <td>693.420786</td>
    </tr>
    <tr>
      <th>1701</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>1997</td>
      <td>46.809</td>
      <td>11404948</td>
      <td>792.449960</td>
    </tr>
    <tr>
      <th>1702</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>2002</td>
      <td>39.989</td>
      <td>11926563</td>
      <td>672.038623</td>
    </tr>
    <tr>
      <th>1703</th>
      <td>Zimbabwe</td>
      <td>Africa</td>
      <td>2007</td>
      <td>43.487</td>
      <td>12311143</td>
      <td>469.709298</td>
    </tr>
  </tbody>
</table>
<p>1704 rows × 6 columns</p>
</div>




```python
# 1. gapminder.tsv파일을 읽고 다음 작업을 진행하시오
# (read_csv를 사용하되, sep=\t로 설정하여 읽을 것)

# -자료 크기, 차원, 컬럼, 타입 등 읽어들인 자료의 구조를 확인하시오
df=pd.read_csv("gapminder.tsv",sep="\t")
df.columns
df.shape #(1704, 6)
type(df) #pandas.core.frame.DataFrame

# -국가명, 대륙명, 연도 열을 추출하시오
df['country']
df['continent']
df['year']

# -lifeExp(기대수명),pop(인구),gdp(소득)의 최대/최소/평균/표준편차
df.describe()[['year','pop','gdpPercap']]


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>pop</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1704.00000</td>
      <td>1.704000e+03</td>
      <td>1704.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1979.50000</td>
      <td>2.960121e+07</td>
      <td>7215.327081</td>
    </tr>
    <tr>
      <th>std</th>
      <td>17.26533</td>
      <td>1.061579e+08</td>
      <td>9857.454543</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1952.00000</td>
      <td>6.001100e+04</td>
      <td>241.165877</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1965.75000</td>
      <td>2.793664e+06</td>
      <td>1202.060309</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1979.50000</td>
      <td>7.023596e+06</td>
      <td>3531.846989</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1993.25000</td>
      <td>1.958522e+07</td>
      <td>9325.462346</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2007.00000</td>
      <td>1.318683e+09</td>
      <td>113523.132900</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 2. 다음 조건을 만족하는 임의의 데이터프레임을 하나 만든다.
# (1) 열의 갯수와 행의 갯수가 각각 5개 이상이어야 한다.
# (2) 열에는 정수, 문자열, 실수 자료형 데이터가 각각 1개 이상씩 포함되어 있어야 한다.
# -> NaN, 컬럼/행 index지정 등 연습

data = {
    "a": [1, 2, 3, 4, 5],
    "b": ['ab', 'bc', 'cd', 'de','ef'],
    "c": [1.1,' ',1.3,1.4,1.5],
    "d": [9853972, 3655437, 2466338, 2473990,2473990],
    "e": ["삼겹살","곱창","피자","초밥","파스타"]
 } 
df=DataFrame(data)
#1행, 3행 추출
df.loc[[1,3],:]
#공백 -> nan처리
df=df.replace(' ',np.nan)
df

# 3열 4열 추출
df.loc[:,['d','e']]

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9853972</td>
      <td>삼겹살</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3655437</td>
      <td>곱창</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2466338</td>
      <td>피자</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2473990</td>
      <td>초밥</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2473990</td>
      <td>파스타</td>
    </tr>
  </tbody>
</table>
</div>




```python

# 3. 다음 데이터프레임에서 지정하는 데이터를 뽑아내거나 처리하라.

data = {
     "국어": [80, 90, 70, 30],
     "영어": [90, 70, 60, 40],
     "수학": [90, 60, 80, 70],
 }
columns = ["국어", "영어", "수학"]
index = ["춘향", "몽룡", "향단", "방자"]
df = pd.DataFrame(data, index=index, columns=columns)
# (1) 모든 학생의 수학 점수를 시리즈로 나타낸다.
type(data)
df[["수학"]]
# (2) 모든 학생의 국어와 영어 점수를 데이터 프레임으로 나타낸다.
df[["국어","영어"]]
# (3) 모든 학생의 각 과목 평균 점수를 새로운 열로 추가한다.
df['평균']=df.sum(axis=1)/3
df
# (4) 방자의 영어 점수를 80점으로 수정하고 평균 점수도 다시 계산한다.
df.loc[['방자'],'영어'] = 80
temp=DataFrame(df.iloc[:,0:3].sum(axis=1)/3)
df['평균']= temp
df
# (5) 춘향의 점수를 데이터프레임으로 나타낸다.
df.loc[['춘향']]

# (6) 향단의 점수를 시리즈로 나타낸다.
df.loc['향단'] #pandas.core.series.Series



```




    국어    70.0
    영어    60.0
    수학    80.0
    평균    70.0
    Name: 향단, dtype: float64




```python
# 4. 
# 제공된 파일중 scientists.csv 파일을 읽고, 다음 작업을 진행하시오
df=pd.read_csv("scientists.csv ")
# -나이 최대값
df['Age'].max()
# -나이 평균
df['Age'].mean()
# -나이 평균보다 큰 나이 값을 모두 출력
df[df['Age'] > df['Age'].mean()]
# -나이에 2를 곱한 값으로 'ages2' 열 추가
df['ages2']=pd.DataFrame(df['Age']*2)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Born</th>
      <th>Died</th>
      <th>Age</th>
      <th>Occupation</th>
      <th>ages2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Rosaline Franklin</td>
      <td>1920-07-25</td>
      <td>1958-04-16</td>
      <td>37</td>
      <td>Chemist</td>
      <td>74</td>
    </tr>
    <tr>
      <th>1</th>
      <td>William Gosset</td>
      <td>1876-06-13</td>
      <td>1937-10-16</td>
      <td>61</td>
      <td>Statistician</td>
      <td>122</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Florence Nightingale</td>
      <td>1820-05-12</td>
      <td>1910-08-13</td>
      <td>90</td>
      <td>Nurse</td>
      <td>180</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Marie Curie</td>
      <td>1867-11-07</td>
      <td>1934-07-04</td>
      <td>66</td>
      <td>Chemist</td>
      <td>132</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rachel Carson</td>
      <td>1907-05-27</td>
      <td>1964-04-14</td>
      <td>56</td>
      <td>Biologist</td>
      <td>112</td>
    </tr>
    <tr>
      <th>5</th>
      <td>John Snow</td>
      <td>1813-03-15</td>
      <td>1858-06-16</td>
      <td>45</td>
      <td>Physician</td>
      <td>90</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Alan Turing</td>
      <td>1912-06-23</td>
      <td>1954-06-07</td>
      <td>41</td>
      <td>Computer Scientist</td>
      <td>82</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Johann Gauss</td>
      <td>1777-04-30</td>
      <td>1855-02-23</td>
      <td>77</td>
      <td>Mathematician</td>
      <td>154</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
