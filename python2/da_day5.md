```python
import numpy as np
import pandas as pd
```


```python
df1 = pd.DataFrame({
    '고객번호': [1001, 1002, 1003, 1004, 1005, 1006, 1007],
    '이름': ['둘리', '도우너', '또치', '길동', '희동', '마이콜', '영희']
}, columns=['고객번호', '이름'])
df1
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
      <th>고객번호</th>
      <th>이름</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>둘리</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1002</td>
      <td>도우너</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1003</td>
      <td>또치</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1004</td>
      <td>길동</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1005</td>
      <td>희동</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1006</td>
      <td>마이콜</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1007</td>
      <td>영희</td>
    </tr>
  </tbody>
</table>
</div>



# 열 기준으로 join
:  merge


```python
df2 = pd.DataFrame({
    '고객번호': [1001, 1001, 1005, 1006, 1008, 1001],
    '금액': [10000, 20000, 15000, 5000, 100000, 30000]
}, columns=['고객번호', '금액'])
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
      <th>고객번호</th>
      <th>금액</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>10000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1001</td>
      <td>20000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1005</td>
      <td>15000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1006</td>
      <td>5000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1008</td>
      <td>100000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1001</td>
      <td>30000</td>
    </tr>
  </tbody>
</table>
</div>



`merge` 함수로 위의 두 데이터프레임 df1, df2 를 합치면 공통 열인 `고객번호` 열을 기준으로 데이터를 찾아서 합친다. 이 때 기본적으로는 양쪽 데이터프레임에 모두 키가 존재하는 데이터만 보여주는 inner join 방식을 사용한다.




```python
pd.merge(df1, df2)
#내부조인 : 두개의 데이터 프레임에 공통으로 존재하는 키를 중심으로 합침
#merge: 데이터 프레임 합치기, 합치는 방법이 다양하게 존재 기본은 내부조인

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
      <th>고객번호</th>
      <th>이름</th>
      <th>금액</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>둘리</td>
      <td>10000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1001</td>
      <td>둘리</td>
      <td>20000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1001</td>
      <td>둘리</td>
      <td>30000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1005</td>
      <td>희동</td>
      <td>15000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1006</td>
      <td>마이콜</td>
      <td>5000</td>
    </tr>
  </tbody>
</table>
</div>

외부조인 (outer join): 키(공통 컬럼) 값이 어느 한쪽에만 있어도 병합이 됨


```python
pd.merge(df1,df2, how="outer")
```



left, right 방식은 각각 첫번째, 혹은 두번째 데이터프레임의 키 값을 모두 보여준다.


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
      <th>고객번호</th>
      <th>이름</th>
      <th>금액</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>둘리</td>
      <td>10000.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1001</td>
      <td>둘리</td>
      <td>20000.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1001</td>
      <td>둘리</td>
      <td>30000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1002</td>
      <td>도우너</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1003</td>
      <td>또치</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1004</td>
      <td>길동</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1005</td>
      <td>희동</td>
      <td>15000.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1006</td>
      <td>마이콜</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1007</td>
      <td>영희</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1008</td>
      <td>NaN</td>
      <td>100000.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#left join
print(df1)
print(df2)
pd.merge(df1, df2, how="left")
#df1(left)를 기준으로 df2와 merge
#df1에 있는 모든 데이터는 merge가 된다
```

       고객번호   이름
    0  1001   둘리
    1  1002  도우너
    2  1003   또치
    3  1004   길동
    4  1005   희동
    5  1006  마이콜
    6  1007   영희
       고객번호      금액
    0  1001   10000
    1  1001   20000
    2  1005   15000
    3  1006    5000
    4  1008  100000
    5  1001   30000



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
      <th>고객번호</th>
      <th>이름</th>
      <th>금액</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>둘리</td>
      <td>10000.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1001</td>
      <td>둘리</td>
      <td>20000.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1001</td>
      <td>둘리</td>
      <td>30000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1002</td>
      <td>도우너</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1003</td>
      <td>또치</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1004</td>
      <td>길동</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1005</td>
      <td>희동</td>
      <td>15000.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1006</td>
      <td>마이콜</td>
      <td>5000.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1007</td>
      <td>영희</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(df1, df2, how="right")
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
      <th>고객번호</th>
      <th>이름</th>
      <th>금액</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1001</td>
      <td>둘리</td>
      <td>10000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1001</td>
      <td>둘리</td>
      <td>20000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1001</td>
      <td>둘리</td>
      <td>30000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1005</td>
      <td>희동</td>
      <td>15000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1006</td>
      <td>마이콜</td>
      <td>5000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1008</td>
      <td>NaN</td>
      <td>100000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = pd.DataFrame({
    '품종': ['setosa', 'setosa', 'virginica', 'virginica'],
    '꽃잎길이': [1.4, 1.3, 1.5, 1.3]},
    columns=['품종', '꽃잎길이'])
df1
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
      <th>품종</th>
      <th>꽃잎길이</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>setosa</td>
      <td>1.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>setosa</td>
      <td>1.3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>virginica</td>
      <td>1.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>virginica</td>
      <td>1.3</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame({
'품종': ['setosa', 'virginica', 'virginica', 'versicolor'],
'꽃잎너비': [0.4, 0.3, 0.5, 0.3]},
columns=['품종', '꽃잎너비'])
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
      <th>품종</th>
      <th>꽃잎너비</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>setosa</td>
      <td>0.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>virginica</td>
      <td>0.3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>virginica</td>
      <td>0.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>versicolor</td>
      <td>0.3</td>
    </tr>
  </tbody>
</table>
</div>




```python
#키 값이 같은 데이터가 여러개 있는 경우에 모든 조합을 만들어서 병합
df1 = pd.DataFrame({
    '고객명': ['춘향', '춘향', '몽룡'],
    '날짜': ['2018-01-01', '2018-01-02', '2018-01-01'],
    '데이터': ['20000', '30000', '100000']})
df1
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
      <th>고객명</th>
      <th>날짜</th>
      <th>데이터</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>춘향</td>
      <td>2018-01-01</td>
      <td>20000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>춘향</td>
      <td>2018-01-02</td>
      <td>30000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>몽룡</td>
      <td>2018-01-01</td>
      <td>100000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame({
    '고객명': ['춘향', '몽룡'],
    '데이터': ['여자', '남자']})
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
      <th>고객명</th>
      <th>데이터</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>춘향</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>1</th>
      <td>몽룡</td>
      <td>남자</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(df1,df2) #머지된게 없다 공통된 키값이 없으므로

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
      <th>고객명</th>
      <th>날짜</th>
      <th>데이터</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
pd.merge(df1,df2,on="고객명") #고객명만 같다면 merge
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
      <th>고객명</th>
      <th>날짜</th>
      <th>데이터_x</th>
      <th>데이터_y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>춘향</td>
      <td>2018-01-01</td>
      <td>20000</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>1</th>
      <td>춘향</td>
      <td>2018-01-02</td>
      <td>30000</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>2</th>
      <td>몽룡</td>
      <td>2018-01-01</td>
      <td>100000</td>
      <td>남자</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = pd.DataFrame({
    '이름': ['영희', '철수', '철수'],
    '성적': [1, 2, 3]})
print(df1)
df2 = pd.DataFrame({
    '성명': ['영희', '영희', '철수'],
    '성적2': [4, 5, 6]})
df2

#df1의 이름과 df2의 성명을 기준으로 합치기 작업
```

       이름  성적
    0  영희   1
    1  철수   2
    2  철수   3





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
      <th>성명</th>
      <th>성적2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>영희</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>철수</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
mdf=pd.merge(df1,df2, left_on= '이름', right_on='성명') 
```


```python
mdf
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
      <th>이름</th>
      <th>성적</th>
      <th>성명</th>
      <th>성적2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>영희</td>
      <td>1</td>
      <td>영희</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>1</td>
      <td>영희</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>철수</td>
      <td>2</td>
      <td>철수</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>철수</td>
      <td>3</td>
      <td>철수</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 열 지우기
del mdf['이름']
```


```python
mdf
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
      <th>성적</th>
      <th>성명</th>
      <th>성적2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>영희</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>영희</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>철수</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>철수</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
mdf=pd.merge(df1,df2, left_on= '이름', right_on='성명') 
mdf=mdf.drop(['성명','성적2'], axis=1)
mdf
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
      <th>이름</th>
      <th>성적</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>영희</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>철수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>철수</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
mdf=pd.merge(df1,df2, left_on= '이름', right_on='성명') 
mdf.drop(['성명','성적2'], axis=1, inplace=True)
mdf
#drop은 대입이 필요한데 inplace=T면 바로 대입해준다.
#del은 삭제하고 그 상태가 반영됨 
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
      <th>이름</th>
      <th>성적</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>영희</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>영희</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>철수</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>철수</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = pd.DataFrame({
    '도시': ['서울', '서울', '서울', '부산', '부산'],
    '연도': [2000, 2005, 2010, 2000, 2005],
    '인구': [9853972, 9762546, 9631482, 3655437, 3512547]})
df1

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
      <th>도시</th>
      <th>연도</th>
      <th>인구</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>서울</td>
      <td>2000</td>
      <td>9853972</td>
    </tr>
    <tr>
      <th>1</th>
      <td>서울</td>
      <td>2005</td>
      <td>9762546</td>
    </tr>
    <tr>
      <th>2</th>
      <td>서울</td>
      <td>2010</td>
      <td>9631482</td>
    </tr>
    <tr>
      <th>3</th>
      <td>부산</td>
      <td>2000</td>
      <td>3655437</td>
    </tr>
    <tr>
      <th>4</th>
      <td>부산</td>
      <td>2005</td>
      <td>3512547</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame(
    np.arange(12).reshape((6, 2)),
    index=[['부산', '부산', '서울', '서울', '서울', '서울'],
           [2000, 2005, 2000, 2005, 2010, 2015]],
    columns=['데이터1', '데이터2'])
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
      <th></th>
      <th>데이터1</th>
      <th>데이터2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">부산</th>
      <th>2000</th>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2005</th>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th rowspan="4" valign="top">서울</th>
      <th>2000</th>
      <td>4</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2005</th>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2010</th>
      <td>8</td>
      <td>9</td>
    </tr>
    <tr>
      <th>2015</th>
      <td>10</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(df1,df2,left_on=['도시','연도'], right_index=True)
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
      <th>도시</th>
      <th>연도</th>
      <th>인구</th>
      <th>데이터1</th>
      <th>데이터2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>서울</td>
      <td>2000</td>
      <td>9853972</td>
      <td>4</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>서울</td>
      <td>2005</td>
      <td>9762546</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>서울</td>
      <td>2010</td>
      <td>9631482</td>
      <td>8</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>부산</td>
      <td>2000</td>
      <td>3655437</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>부산</td>
      <td>2005</td>
      <td>3512547</td>
      <td>2</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = pd.DataFrame(
    [[1., 2.], [3., 4.], [5., 6.]],
    index=['a', 'c', 'e'],
    columns=['서울', '부산'])
df1

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
      <th>서울</th>
      <th>부산</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>e</th>
      <td>5.0</td>
      <td>6.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame(
    [[7., 8.], [9., 10.], [11., 12.], [13, 14]],
    index=['b', 'c', 'd', 'e'],
    columns=['대구', '광주'])
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
      <th>대구</th>
      <th>광주</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>b</th>
      <td>7.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>c</th>
      <td>9.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>d</th>
      <td>11.0</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>e</th>
      <td>13.0</td>
      <td>14.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#공통으로 존재하는 인덱스가 있고 아닌것도 있을때
pd.merge(df1,df2,left_index=True , right_index=True) #디폴트가 inner인 걸 알 수 있다!

pd.merge(df1,df2,left_index=True , right_index=True, how="inner") 

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
      <th>서울</th>
      <th>부산</th>
      <th>대구</th>
      <th>광주</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>c</th>
      <td>3.0</td>
      <td>4.0</td>
      <td>9.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>e</th>
      <td>5.0</td>
      <td>6.0</td>
      <td>13.0</td>
      <td>14.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(df1,df2,left_index=True , right_index=True, how="outer") 
#전부 다 나옴
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
      <th>서울</th>
      <th>부산</th>
      <th>대구</th>
      <th>광주</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>b</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3.0</td>
      <td>4.0</td>
      <td>9.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>d</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>11.0</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>e</th>
      <td>5.0</td>
      <td>6.0</td>
      <td>13.0</td>
      <td>14.0</td>
    </tr>
  </tbody>
</table>
</div>



## join


```python
df1.join(df2)
#df1을 기준으로 df2와 병합

df1.join(df2, how ="inner") #df1과 df2를 이너조인 
df1.join(df2, how ="outer")

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
      <th>서울</th>
      <th>부산</th>
      <th>대구</th>
      <th>광주</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>1.0</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>b</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>c</th>
      <td>3.0</td>
      <td>4.0</td>
      <td>9.0</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>d</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>11.0</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>e</th>
      <td>5.0</td>
      <td>6.0</td>
      <td>13.0</td>
      <td>14.0</td>
    </tr>
  </tbody>
</table>
</div>



## concat
: 기준 열 없이 단순히 데이터 연결 위/아래로 연결


```python
s1 = pd.Series([0, 1], index=['A', 'B'])
s2 = pd.Series([2, 3, 4], index=['A', 'B', 'C'])

```


```python
s1
```




    A    0
    B    1
    dtype: int64




```python
s2
```




    A    2
    B    3
    C    4
    dtype: int64




```python
#시리즈 2개 합치기
s3=pd.concat([s1,s2]) #위 아래로 합해진다.
s3
```




    A    0
    B    1
    A    2
    B    3
    C    4
    dtype: int64




```python
s3.loc['A']
s3.loc['B']
s3.iloc[0]
s3.iloc[4]
s3.iloc[-2]
```




    3




```python
pd.concat([s1,s2],axis=1)
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>0.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>B</th>
      <td>1.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>C</th>
      <td>NaN</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = pd.DataFrame(
    np.arange(6).reshape(3, 2),
    index=['a', 'b', 'c'],
    columns=['데이터1', '데이터2'])
df1

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
      <th>데이터1</th>
      <th>데이터2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>c</th>
      <td>4</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame(
    5 + np.arange(4).reshape(2, 2),
    index=['a', 'c'],
    columns=['데이터3', '데이터4'])
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
      <th>데이터3</th>
      <th>데이터4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>c</th>
      <td>7</td>
      <td>8</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([df1,df2],axis=1) #concat의 기준은 행인덱스
#concatenate(연결)
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
      <th>데이터1</th>
      <th>데이터2</th>
      <th>데이터3</th>
      <th>데이터4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>0</td>
      <td>1</td>
      <td>5.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>b</th>
      <td>2</td>
      <td>3</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>c</th>
      <td>4</td>
      <td>5</td>
      <td>7.0</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
</div>



# 피봇테이블
:데이터 열 중에서 2개의 열을 선택하여 행/열 인덱스로 사용
나머지 열은 데이터가 된다
pivot(행 인덱스가 될 열이름, 열 인덱스가 될 열이름, 데이터가 될 열이름)


```python
data = {
    "도시": ["서울", "서울", "서울", "부산", "부산", "부산", "인천", "인천"],
    "연도": ["2015", "2010", "2005", "2015", "2010", "2005", "2015", "2010"],
    "인구": [9904312, 9631482, 9762546, 3448737, 3393191, 3512547, 2890451, 263203],
    "지역": ["수도권", "수도권", "수도권", "경상권", "경상권", "경상권", "수도권", "수도권"]
}
columns = ["도시", "연도", "인구", "지역"]
df1 = pd.DataFrame(data, columns=columns)
df1

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
      <th>도시</th>
      <th>연도</th>
      <th>인구</th>
      <th>지역</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>서울</td>
      <td>2015</td>
      <td>9904312</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>1</th>
      <td>서울</td>
      <td>2010</td>
      <td>9631482</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>2</th>
      <td>서울</td>
      <td>2005</td>
      <td>9762546</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>3</th>
      <td>부산</td>
      <td>2015</td>
      <td>3448737</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>4</th>
      <td>부산</td>
      <td>2010</td>
      <td>3393191</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>5</th>
      <td>부산</td>
      <td>2005</td>
      <td>3512547</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>6</th>
      <td>인천</td>
      <td>2015</td>
      <td>2890451</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>7</th>
      <td>인천</td>
      <td>2010</td>
      <td>263203</td>
      <td>수도권</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.pivot("도시","연도","인구")

#도시 ,연도는 다 나옴(중복제외)
#인구 
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
      <th>연도</th>
      <th>2005</th>
      <th>2010</th>
      <th>2015</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>부산</th>
      <td>3512547.0</td>
      <td>3393191.0</td>
      <td>3448737.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9762546.0</td>
      <td>9631482.0</td>
      <td>9904312.0</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>NaN</td>
      <td>263203.0</td>
      <td>2890451.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.set_index(["도시","연도"])[["인구"]]

#도시, 연도는 데이터 x 행인덱스임

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
      <th></th>
      <th>인구</th>
    </tr>
    <tr>
      <th>도시</th>
      <th>연도</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">서울</th>
      <th>2015</th>
      <td>9904312</td>
    </tr>
    <tr>
      <th>2010</th>
      <td>9631482</td>
    </tr>
    <tr>
      <th>2005</th>
      <td>9762546</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">부산</th>
      <th>2015</th>
      <td>3448737</td>
    </tr>
    <tr>
      <th>2010</th>
      <td>3393191</td>
    </tr>
    <tr>
      <th>2005</th>
      <td>3512547</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">인천</th>
      <th>2015</th>
      <td>2890451</td>
    </tr>
    <tr>
      <th>2010</th>
      <td>263203</td>
    </tr>
  </tbody>
</table>
</div>




```python
#피봇테이블은 다음과 같이 set_index 명령과 unstack 명령을 사용해서 만들 수도 있다.


df1.set_index(["도시","연도"])[["인구"]].unstack()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
    
    .dataframe thead tr th {
        text-align: left;
    }
    
    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="3" halign="left">인구</th>
    </tr>
    <tr>
      <th>연도</th>
      <th>2005</th>
      <th>2010</th>
      <th>2015</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>부산</th>
      <td>3512547.0</td>
      <td>3393191.0</td>
      <td>3448737.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9762546.0</td>
      <td>9631482.0</td>
      <td>9904312.0</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>NaN</td>
      <td>263203.0</td>
      <td>2890451.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.pivot("도시","연도","인구")
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
      <th>연도</th>
      <th>2005</th>
      <th>2010</th>
      <th>2015</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>부산</th>
      <td>3512547.0</td>
      <td>3393191.0</td>
      <td>3448737.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9762546.0</td>
      <td>9631482.0</td>
      <td>9904312.0</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>NaN</td>
      <td>263203.0</td>
      <td>2890451.0</td>
    </tr>
  </tbody>
</table>
</div>



# group_by
:시리즈나 데이터프레임에 대해 그룹화 -> 그룹객체
각각의 그룹 객체에 대해 그룹 연산 수행

그룹화 -> 그룹 단위 연산


```python
np.random.seed(0)
df2 = pd.DataFrame({
    'key1': ['A', 'A', 'B', 'B', 'A'],
    'key2': ['one', 'two', 'one', 'two', 'one'],
    'data1': [1, 2, 3, 4, 5],
    'data2': [10, 20, 30, 40, 50]
})
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
      <th>key1</th>
      <th>key2</th>
      <th>data1</th>
      <th>data2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>one</td>
      <td>1</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A</td>
      <td>two</td>
      <td>2</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>B</td>
      <td>one</td>
      <td>3</td>
      <td>30</td>
    </tr>
    <tr>
      <th>3</th>
      <td>B</td>
      <td>two</td>
      <td>4</td>
      <td>40</td>
    </tr>
    <tr>
      <th>4</th>
      <td>A</td>
      <td>one</td>
      <td>5</td>
      <td>50</td>
    </tr>
  </tbody>
</table>
</div>




```python
#그룹 A, 그룹 B 로 구분
groups = df2.groupby(df2.key1)
groups
```




    <pandas.core.groupby.generic.DataFrameGroupBy object at 0x000001455CE783A0>




```python
groups.groups #딕셔너리 형태
groups.sum()
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
      <th>data1</th>
      <th>data2</th>
    </tr>
    <tr>
      <th>key1</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>8</td>
      <td>80</td>
    </tr>
    <tr>
      <th>B</th>
      <td>7</td>
      <td>70</td>
    </tr>
  </tbody>
</table>
</div>




```python
group1= df2.data1.groupby(df2.key1)
group1
```




    <pandas.core.groupby.generic.SeriesGroupBy object at 0x000001455D2DEA30>




```python
group1.sum()
```




    key1
    A    8
    B    7
    Name: data1, dtype: int64




```python
df2.data1.groupby(df2.key1).sum()
```




    key1
    A    8
    B    7
    Name: data1, dtype: int64




```python
df2.groupby(df2.key1)['data1'].sum()
df2.groupby(df2.key1)[['data1']].sum()

df2.groupby(df2.key1).sum()['data1'] #다 같다? 
df2.groupby(df2.key1).sum()[['data1']]
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
      <th>data1</th>
    </tr>
    <tr>
      <th>key1</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>8</td>
    </tr>
    <tr>
      <th>B</th>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2
#key1과 key2를 기준으로 그룹화 -> 각 그룹별 data1에 대한 연산

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
      <th>key1</th>
      <th>key2</th>
      <th>data1</th>
      <th>data2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>one</td>
      <td>1</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A</td>
      <td>two</td>
      <td>2</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>B</td>
      <td>one</td>
      <td>3</td>
      <td>30</td>
    </tr>
    <tr>
      <th>3</th>
      <td>B</td>
      <td>two</td>
      <td>4</td>
      <td>40</td>
    </tr>
    <tr>
      <th>4</th>
      <td>A</td>
      <td>one</td>
      <td>5</td>
      <td>50</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.data1.groupby([df2.key1, df2.key2]).sum().unstack("key2")
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
      <th>key2</th>
      <th>one</th>
      <th>two</th>
    </tr>
    <tr>
      <th>key1</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>6</td>
      <td>2</td>
    </tr>
    <tr>
      <th>B</th>
      <td>3</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1
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
      <th>도시</th>
      <th>연도</th>
      <th>인구</th>
      <th>지역</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>서울</td>
      <td>2015</td>
      <td>9904312</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>1</th>
      <td>서울</td>
      <td>2010</td>
      <td>9631482</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>2</th>
      <td>서울</td>
      <td>2005</td>
      <td>9762546</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>3</th>
      <td>부산</td>
      <td>2015</td>
      <td>3448737</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>4</th>
      <td>부산</td>
      <td>2010</td>
      <td>3393191</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>5</th>
      <td>부산</td>
      <td>2005</td>
      <td>3512547</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>6</th>
      <td>인천</td>
      <td>2015</td>
      <td>2890451</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>7</th>
      <td>인천</td>
      <td>2010</td>
      <td>263203</td>
      <td>수도권</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1['인구'].groupby([df1.지역,df1.연도]).sum().unstack("연도")


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
      <th>연도</th>
      <th>2005</th>
      <th>2010</th>
      <th>2015</th>
    </tr>
    <tr>
      <th>지역</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>경상권</th>
      <td>3512547</td>
      <td>3393191</td>
      <td>3448737</td>
    </tr>
    <tr>
      <th>수도권</th>
      <td>9762546</td>
      <td>9894685</td>
      <td>12794763</td>
    </tr>
  </tbody>
</table>
</div>




```python
import seaborn as sns
```


```python
iris=sns.load_dataset("iris")
```


```python
iris.groupby(iris.species)
grp=iris.groupby(iris.species)
grp.groups
```




    {'setosa': [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49], 'versicolor': [50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99], 'virginica': [100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124, 125, 126, 127, 128, 129, 130, 131, 132, 133, 134, 135, 136, 137, 138, 139, 140, 141, 142, 143, 144, 145, 146, 147, 148, 149]}




```python
iris.groupby(iris.species).min()
iris.groupby(iris.species).max()
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
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
    </tr>
    <tr>
      <th>species</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>setosa</th>
      <td>5.8</td>
      <td>4.4</td>
      <td>1.9</td>
      <td>0.6</td>
    </tr>
    <tr>
      <th>versicolor</th>
      <td>7.0</td>
      <td>3.4</td>
      <td>5.1</td>
      <td>1.8</td>
    </tr>
    <tr>
      <th>virginica</th>
      <td>7.9</td>
      <td>3.8</td>
      <td>6.9</td>
      <td>2.5</td>
    </tr>
  </tbody>
</table>
</div>




```python
iris.groupby(iris.species).max()-iris.groupby(iris.species).min()

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
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
    </tr>
    <tr>
      <th>species</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>setosa</th>
      <td>1.5</td>
      <td>2.1</td>
      <td>0.9</td>
      <td>0.5</td>
    </tr>
    <tr>
      <th>versicolor</th>
      <td>2.1</td>
      <td>1.4</td>
      <td>2.1</td>
      <td>0.8</td>
    </tr>
    <tr>
      <th>virginica</th>
      <td>3.0</td>
      <td>1.6</td>
      <td>2.4</td>
      <td>1.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
def diff(x): #x메뉴 종별 그룹이 전달됨
    return x.max()-x.min() #그룹단위로 컬럼별 max, min연산 수행


```


```python
iris.groupby(iris.species).agg(diff)
# agg: aggregate 집계

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
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
    </tr>
    <tr>
      <th>species</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>setosa</th>
      <td>1.5</td>
      <td>2.1</td>
      <td>0.9</td>
      <td>0.5</td>
    </tr>
    <tr>
      <th>versicolor</th>
      <td>2.1</td>
      <td>1.4</td>
      <td>2.1</td>
      <td>0.8</td>
    </tr>
    <tr>
      <th>virginica</th>
      <td>3.0</td>
      <td>1.6</td>
      <td>2.4</td>
      <td>1.1</td>
    </tr>
  </tbody>
</table>
</div>



# describe()
기술 통계(descriptive statistics)값을 한 번에 구한다. 그룹별로 하나의 스칼라 값이 아니라 하나의 데이터프레임이 생성된다는 점에 주의하라.


```python
iris.groupby(iris.species).describe().T

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
      <th>species</th>
      <th>setosa</th>
      <th>versicolor</th>
      <th>virginica</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="8" valign="top">sepal_length</th>
      <th>count</th>
      <td>50.000000</td>
      <td>50.000000</td>
      <td>50.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.006000</td>
      <td>5.936000</td>
      <td>6.588000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.352490</td>
      <td>0.516171</td>
      <td>0.635880</td>
    </tr>
    <tr>
      <th>min</th>
      <td>4.300000</td>
      <td>4.900000</td>
      <td>4.900000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>4.800000</td>
      <td>5.600000</td>
      <td>6.225000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>5.000000</td>
      <td>5.900000</td>
      <td>6.500000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>5.200000</td>
      <td>6.300000</td>
      <td>6.900000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>5.800000</td>
      <td>7.000000</td>
      <td>7.900000</td>
    </tr>
    <tr>
      <th rowspan="8" valign="top">sepal_width</th>
      <th>count</th>
      <td>50.000000</td>
      <td>50.000000</td>
      <td>50.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>3.428000</td>
      <td>2.770000</td>
      <td>2.974000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.379064</td>
      <td>0.313798</td>
      <td>0.322497</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2.300000</td>
      <td>2.000000</td>
      <td>2.200000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.200000</td>
      <td>2.525000</td>
      <td>2.800000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3.400000</td>
      <td>2.800000</td>
      <td>3.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3.675000</td>
      <td>3.000000</td>
      <td>3.175000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>4.400000</td>
      <td>3.400000</td>
      <td>3.800000</td>
    </tr>
    <tr>
      <th rowspan="8" valign="top">petal_length</th>
      <th>count</th>
      <td>50.000000</td>
      <td>50.000000</td>
      <td>50.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1.462000</td>
      <td>4.260000</td>
      <td>5.552000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.173664</td>
      <td>0.469911</td>
      <td>0.551895</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>4.500000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.400000</td>
      <td>4.000000</td>
      <td>5.100000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.500000</td>
      <td>4.350000</td>
      <td>5.550000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1.575000</td>
      <td>4.600000</td>
      <td>5.875000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.900000</td>
      <td>5.100000</td>
      <td>6.900000</td>
    </tr>
    <tr>
      <th rowspan="8" valign="top">petal_width</th>
      <th>count</th>
      <td>50.000000</td>
      <td>50.000000</td>
      <td>50.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.246000</td>
      <td>1.326000</td>
      <td>2.026000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.105386</td>
      <td>0.197753</td>
      <td>0.274650</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.100000</td>
      <td>1.000000</td>
      <td>1.400000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.200000</td>
      <td>1.200000</td>
      <td>1.800000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.200000</td>
      <td>1.300000</td>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.300000</td>
      <td>1.500000</td>
      <td>2.300000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>0.600000</td>
      <td>1.800000</td>
      <td>2.500000</td>
    </tr>
  </tbody>
</table>
</div>




```python
#붓꽃 종류별로 길이 가장 긴 3개의 데이터

def leng(x): #x메뉴 종별 그룹이 전달됨
    return x.sort_values(by="petal_length",ascending=False)[:3]

iris.groupby(iris.species).apply(leng)


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
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
    <tr>
      <th>species</th>
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
      <th rowspan="3" valign="top">setosa</th>
      <th>24</th>
      <td>4.8</td>
      <td>3.4</td>
      <td>1.9</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>44</th>
      <td>5.1</td>
      <td>3.8</td>
      <td>1.9</td>
      <td>0.4</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>23</th>
      <td>5.1</td>
      <td>3.3</td>
      <td>1.7</td>
      <td>0.5</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">versicolor</th>
      <th>83</th>
      <td>6.0</td>
      <td>2.7</td>
      <td>5.1</td>
      <td>1.6</td>
      <td>versicolor</td>
    </tr>
    <tr>
      <th>77</th>
      <td>6.7</td>
      <td>3.0</td>
      <td>5.0</td>
      <td>1.7</td>
      <td>versicolor</td>
    </tr>
    <tr>
      <th>72</th>
      <td>6.3</td>
      <td>2.5</td>
      <td>4.9</td>
      <td>1.5</td>
      <td>versicolor</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">virginica</th>
      <th>118</th>
      <td>7.7</td>
      <td>2.6</td>
      <td>6.9</td>
      <td>2.3</td>
      <td>virginica</td>
    </tr>
    <tr>
      <th>117</th>
      <td>7.7</td>
      <td>3.8</td>
      <td>6.7</td>
      <td>2.2</td>
      <td>virginica</td>
    </tr>
    <tr>
      <th>122</th>
      <td>7.7</td>
      <td>2.8</td>
      <td>6.7</td>
      <td>2.0</td>
      <td>virginica</td>
    </tr>
  </tbody>
</table>
</div>



# 피봇 테이블
: 피봇과 그룹의 중간형태



```python
df1
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
      <th>도시</th>
      <th>연도</th>
      <th>인구</th>
      <th>지역</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>서울</td>
      <td>2015</td>
      <td>9904312</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>1</th>
      <td>서울</td>
      <td>2010</td>
      <td>9631482</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>2</th>
      <td>서울</td>
      <td>2005</td>
      <td>9762546</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>3</th>
      <td>부산</td>
      <td>2015</td>
      <td>3448737</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>4</th>
      <td>부산</td>
      <td>2010</td>
      <td>3393191</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>5</th>
      <td>부산</td>
      <td>2005</td>
      <td>3512547</td>
      <td>경상권</td>
    </tr>
    <tr>
      <th>6</th>
      <td>인천</td>
      <td>2015</td>
      <td>2890451</td>
      <td>수도권</td>
    </tr>
    <tr>
      <th>7</th>
      <td>인천</td>
      <td>2010</td>
      <td>263203</td>
      <td>수도권</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.pivot_table("인구", "도시", "연도") #인수 순서 다름 주의


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
      <th>연도</th>
      <th>2005</th>
      <th>2010</th>
      <th>2015</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>부산</th>
      <td>3512547.0</td>
      <td>3393191.0</td>
      <td>3448737.0</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9762546.0</td>
      <td>9631482.0</td>
      <td>9904312.0</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>NaN</td>
      <td>263203.0</td>
      <td>2890451.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.pivot_table("인구", "도시", "연도", margins=True) 
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
      <th>연도</th>
      <th>2005</th>
      <th>2010</th>
      <th>2015</th>
      <th>All</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>부산</th>
      <td>3512547.0</td>
      <td>3393191.0</td>
      <td>3448737.0</td>
      <td>3.451492e+06</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9762546.0</td>
      <td>9631482.0</td>
      <td>9904312.0</td>
      <td>9.766113e+06</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>NaN</td>
      <td>263203.0</td>
      <td>2890451.0</td>
      <td>1.576827e+06</td>
    </tr>
    <tr>
      <th>All</th>
      <td>6637546.5</td>
      <td>4429292.0</td>
      <td>5414500.0</td>
      <td>5.350809e+06</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.pivot_table("인구", "도시", "연도", margins=True,margins_name='최소값', aggfunc="min") 
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
      <th>연도</th>
      <th>2005</th>
      <th>2010</th>
      <th>2015</th>
      <th>최소값</th>
    </tr>
    <tr>
      <th>도시</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>부산</th>
      <td>3512547.0</td>
      <td>3393191.0</td>
      <td>3448737.0</td>
      <td>3393191</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9762546.0</td>
      <td>9631482.0</td>
      <td>9904312.0</td>
      <td>9631482</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>NaN</td>
      <td>263203.0</td>
      <td>2890451.0</td>
      <td>263203</td>
    </tr>
    <tr>
      <th>최소값</th>
      <td>3512547.0</td>
      <td>263203.0</td>
      <td>2890451.0</td>
      <td>263203</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.pivot_table("인구", index=["연도","도시"])
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
      <th></th>
      <th>인구</th>
    </tr>
    <tr>
      <th>연도</th>
      <th>도시</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">2005</th>
      <th>부산</th>
      <td>3512547</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9762546</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2010</th>
      <th>부산</th>
      <td>3393191</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9631482</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>263203</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">2015</th>
      <th>부산</th>
      <td>3448737</td>
    </tr>
    <tr>
      <th>서울</th>
      <td>9904312</td>
    </tr>
    <tr>
      <th>인천</th>
      <td>2890451</td>
    </tr>
  </tbody>
</table>
</div>


