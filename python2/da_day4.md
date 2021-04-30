# day 4

# loc
`loc` : 라벨색인(index)을 가지고 데이터를 추출
데이터프레임 loc(행인덱스)
데이터 프레임 loc(행인덱스, 열인덱스)


```python
import pandas as pd
import numpy as np
df = pd.DataFrame(np.arange(10, 22).reshape(3, 4),
                  index=["a", "b", "c"],
                  columns=["A", "B", "C", "D"])
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
    <tr>
      <th>c</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc['a'] #라벨 인덱스 이용해서 추출
```




    A    10
    B    11
    C    12
    D    13
    Name: a, dtype: int32




```python
df['a':'b']
df.loc['a':'b']
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[['a','c']] #떨어져 있는 두개 이상 행 대괄호 두개!
#df[['a','c']] #에러
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>c</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.A
df['A']
```




    a    10
    b    14
    c    18
    Name: A, dtype: int32




```python
df.A>15
```




    a    False
    b    False
    c     True
    Name: A, dtype: bool




```python
df.loc[df.A>15]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>c</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
def select_rows(df):
    return df.A>15
```


```python
select_rows(df)
```




    a    False
    b    False
    c     True
    Name: A, dtype: bool




```python
df.loc[select_rows(df)] #15이상인 값으로 이뤄진 행 출력
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>c</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame(np.arange(10, 26).reshape(4, 4), columns=["A", "B", "C", "D"])
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>1</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
    <tr>
      <th>3</th>
      <td>22</td>
      <td>23</td>
      <td>24</td>
      <td>25</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.loc[1:2]
#열을 추출할때는 loc를 빼고 써야한다
df2['A']
df2.A
```




    0    10
    1    14
    2    18
    3    22
    Name: A, dtype: int32




```python
df.loc['a'].loc['A'] #지저분 이렇게 안씀
```




    10




```python
df.loc['a','A'] #행 a, 열 A인 위치 추출
```




    10




```python
df.loc['a':]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
    <tr>
      <th>c</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
    <tr>
      <th>c</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc['a':'b',['B','D']]
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
      <th>B</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>11</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>15</td>
      <td>17</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[df.A>10]
df.loc[df.A>10, ['C','D']]
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
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>b</th>
      <td>16</td>
      <td>17</td>
    </tr>
    <tr>
      <th>c</th>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
    <tr>
      <th>c</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc['a','B']
df.iloc[0] #기본적으로 숫자 인덱스가 0번부터 부여되어있다고 가정
```




    A    10
    B    11
    C    12
    D    13
    Name: a, dtype: int32




```python
df.iloc[:2] #0번~1번 행 인덱스 해당되는 데이터가 추출
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[:'c'] #a행 인덱스~c행 인덱스에 해당되는 데이터가 추출
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
    <tr>
      <th>c</th>
      <td>18</td>
      <td>19</td>
      <td>20</td>
      <td>21</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[0,[2,3]]
df.iloc[2,[1,2]]
df.iloc[2]
```




    A    18
    B    19
    C    20
    D    21
    Name: c, dtype: int32




```python
df.iloc[0,-2:]
df.iloc[-1]= df.iloc[-1]*2
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>10</td>
      <td>11</td>
      <td>12</td>
      <td>13</td>
    </tr>
    <tr>
      <th>b</th>
      <td>14</td>
      <td>15</td>
      <td>16</td>
      <td>17</td>
    </tr>
    <tr>
      <th>c</th>
      <td>72</td>
      <td>76</td>
      <td>80</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>




```python
df= pd.read_csv('gapminder.tsv',sep='\t')
```


```python
df.head()
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
  </tbody>
</table>
</div>




```python
df.loc[0] #0은 라벨
df.iloc[0] #0은 숫자 인덱스 , 표에 보이는 왼쪽 굵은 긁자 굵은 긁자
df.loc[99]
#df.info()
df.loc[1703]
df.iloc[1703]
df.iloc[-1] #뒤에서 부터 1번째 데이터 추출
#df.loc[-1] 에러!  라벨이 없으니까 
```




    country      Zimbabwe
    continent      Africa
    year             2007
    lifeExp        43.487
    pop          12311143
    gdpPercap     469.709
    Name: 1703, dtype: object




```python
df.loc[df.shape[0]-1]
df.loc[[0,99,999]]
```




    pandas.core.frame.DataFrame




```python
type(df.loc[df.shape[0]-1]) #series
df.tail(1)
df.loc[[0,99,999],['country','lifeExp','gdpPercap']]
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
      <th>lifeExp</th>
      <th>gdpPercap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>28.801</td>
      <td>779.445314</td>
    </tr>
    <tr>
      <th>99</th>
      <td>Bangladesh</td>
      <td>43.453</td>
      <td>721.186086</td>
    </tr>
    <tr>
      <th>999</th>
      <td>Mongolia</td>
      <td>51.253</td>
      <td>1226.041130</td>
    </tr>
  </tbody>
</table>
</div>



## count 
: 열방향으로 세준다
숫자보고 누락인걸 확인할 수 있음


```python
np.random.seed(2)
df = pd.DataFrame(np.random.randint(5, size=(4, 4)), dtype=float)
df.iloc[2,3]=np.nan
```


```python
#df.info
df.count()
```




    0    4
    1    4
    2    4
    3    3
    dtype: int64




```python
import seaborn as sns # 시각화 패키지
```


```python
t=sns.load_dataset("titanic")
t.head()
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
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
np.random.seed(1)
s2 = pd.Series(np.random.randint(6, size=100))
s2
#시리즈에 저장되는 값이 정수, 문자, 카테고리 값인 경우에는 value_counts 함수로 
```




    0     5
    1     3
    2     4
    3     0
    4     1
         ..
    95    4
    96    5
    97    2
    98    4
    99    3
    Length: 100, dtype: int32




```python
s2.value_counts()
```




    1    22
    0    18
    4    17
    5    16
    3    14
    2    13
    dtype: int64




```python
df.value_counts()
```




    0    1    2    3  
    4.0  3.0  4.0  2.0    1
    3.0  0.0  2.0  1.0    1
    0.0  0.0  3.0  2.0    1
    dtype: int64




```python
df[0]
df[0].value.counts()
```


    ---------------------------------------------------------------------------
    
    AttributeError                            Traceback (most recent call last)
    
    <ipython-input-87-a7a1f88d41f9> in <module>
          1 df[0]
    ----> 2 df[0].value.counts()


    ~\anaconda3\lib\site-packages\pandas\core\generic.py in __getattr__(self, name)
       5137             if self._info_axis._can_hold_identifiers_and_holds_name(name):
       5138                 return self[name]
    -> 5139             return object.__getattribute__(self, name)
       5140 
       5141     def __setattr__(self, name: str, value) -> None:


    AttributeError: 'Series' object has no attribute 'value'



```python
s2.value_counts #기준은 '값' 내림차순 
```




    1    22
    0    18
    4    17
    5    16
    3    14
    2    13
    dtype: int64




```python
s2.value_counts().sort_index() #index 기준 정렬
```




    0    18
    1    22
    2    13
    3    14
    4    17
    5    16
    dtype: int64




```python
s2.sort_values() #오름차순 
s2.sort_values(ascending=False)
```




    0     5
    11    5
    46    5
    40    5
    71    5
         ..
    28    0
    85    0
    39    0
    38    0
    57    0
    Length: 100, dtype: int32




```python
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>4.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>2.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#df.sort_values() 에러! by가 빠졌대
df.sort_values(by=3) #3 열 정렬 NaN 은 마지막으로
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
      <th>1</th>
      <td>3.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>0</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>4.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
#여러개의 기준을 써야할때
df.sort_values(by=[3,1]) #3번열을 기준으로 근데 동일한 값은 1번열 값을 기준으로
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
      <th>1</th>
      <td>3.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>0</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2.0</td>
      <td>4.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
np.random.seed(1)
df2 = pd.DataFrame(np.random.randint(10, size=(4, 8)))
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
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5</td>
      <td>8</td>
      <td>9</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>7</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6</td>
      <td>9</td>
      <td>2</td>
      <td>4</td>
      <td>5</td>
      <td>2</td>
      <td>4</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>7</td>
      <td>7</td>
      <td>9</td>
      <td>1</td>
      <td>7</td>
      <td>0</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9</td>
      <td>9</td>
      <td>7</td>
      <td>6</td>
      <td>9</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.sum()
#df2.sum(axis=0) #행 방향으로 
df2['RowSum'] = df2.sum(axis=1) #열 벙항으로
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
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>RowSum</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5</td>
      <td>8</td>
      <td>9</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>7</td>
      <td>35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6</td>
      <td>9</td>
      <td>2</td>
      <td>4</td>
      <td>5</td>
      <td>2</td>
      <td>4</td>
      <td>2</td>
      <td>34</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>7</td>
      <td>7</td>
      <td>9</td>
      <td>1</td>
      <td>7</td>
      <td>0</td>
      <td>6</td>
      <td>41</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9</td>
      <td>9</td>
      <td>7</td>
      <td>6</td>
      <td>9</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>42</td>
    </tr>
  </tbody>
</table>
</div>




```python
#df2['ColSum'] = df2.sum(axis=0)  행을 추가하고 싶으므로 잘못된 결과
#df2
#del df2['ColSum']

df2.loc['ColSum']= df2.sum(axis=0) 
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
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>RowSum</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5</td>
      <td>8</td>
      <td>9</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>7</td>
      <td>35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6</td>
      <td>9</td>
      <td>2</td>
      <td>4</td>
      <td>5</td>
      <td>2</td>
      <td>4</td>
      <td>2</td>
      <td>34</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>7</td>
      <td>7</td>
      <td>9</td>
      <td>1</td>
      <td>7</td>
      <td>0</td>
      <td>6</td>
      <td>41</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9</td>
      <td>9</td>
      <td>7</td>
      <td>6</td>
      <td>9</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>42</td>
    </tr>
    <tr>
      <th>ColSum</th>
      <td>48</td>
      <td>66</td>
      <td>50</td>
      <td>48</td>
      <td>30</td>
      <td>20</td>
      <td>10</td>
      <td>32</td>
      <td>304</td>
    </tr>
  </tbody>
</table>
</div>




```python
df3 = pd.DataFrame({
    'A': [1, 3, 4, 3, 4],
    'B': [2, 3, 1, 2, 3],
    'C': [1, 5, 2, 4, 4]
})
df3
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>3</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>2</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>3</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>



## apply (함수)
df3.apply(함수) : df3에게 함수를 각각의 열 단위로 적용해라
lambda랑 섞어씀


```python
df3.apply(lambda x: x.max()) #x가 열 
df3.apply(lambda x: x.max()-x.min(), axis=0) #x가 열 
```




    A    3
    B    2
    C    4
    dtype: int64




```python
df3.apply(lambda x: x.max()-x.min(), axis=1) #axis=1 행단위 적용
```




    0    1
    1    2
    2    3
    3    2
    4    1
    dtype: int64




```python
#df3에 저장된 각각의 값들에 대해 개수를 세는 함수를 구현해보자 
#df3.apply(lambda x: x.value_counts()) 
df3['A'].value_counts()
df3['C'].value_counts()
```




    4    2
    5    1
    2    1
    1    1
    Name: C, dtype: int64




```python
df3.apply(pd.value_counts)

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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>2.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2.0</td>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2.0</td>
      <td>NaN</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#퀴즈3
#타이타닉에서 age 열 값이 20이상이면 adult 미만이면 child를 새로운 열 adult_child 에 저장

t['adult_child']=t['age'].apply(lambda x:'adult' if x>=20 else 'child')
t
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
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
      <th>adult_child</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
      <td>adult</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
      <td>adult</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
      <td>adult</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
      <td>adult</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
      <td>adult</td>
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
    </tr>
    <tr>
      <th>886</th>
      <td>0</td>
      <td>2</td>
      <td>male</td>
      <td>27.0</td>
      <td>0</td>
      <td>0</td>
      <td>13.0000</td>
      <td>S</td>
      <td>Second</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
      <td>adult</td>
    </tr>
    <tr>
      <th>887</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>19.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>B</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
      <td>child</td>
    </tr>
    <tr>
      <th>888</th>
      <td>0</td>
      <td>3</td>
      <td>female</td>
      <td>NaN</td>
      <td>1</td>
      <td>2</td>
      <td>23.4500</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
      <td>child</td>
    </tr>
    <tr>
      <th>889</th>
      <td>1</td>
      <td>1</td>
      <td>male</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>C</td>
      <td>First</td>
      <td>man</td>
      <td>True</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>True</td>
      <td>adult</td>
    </tr>
    <tr>
      <th>890</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>32.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.7500</td>
      <td>Q</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Queenstown</td>
      <td>no</td>
      <td>True</td>
      <td>adult</td>
    </tr>
  </tbody>
</table>
<p>891 rows × 16 columns</p>
</div>




```python
## fillna na 채우기
#astype type변환할때
df3.apply(pd.value_counts).fillna(0).astype(int)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
type(df3.apply(pd.value_counts).fillna(0)) #DataFrame
```




    pandas.core.frame.DataFrame



## cut
: 경계를 지정해서 데이터를 나눔
## qcut
: 똑같은 개수의 구간으로 나눔


```python
ages = [0, 2, 10, 21, 23, 37, 31, 61, 20, 41, 32, 101]
bins=[1,20,30,50,70,100] #5개의 구간으로 나누겠다.
#구간을 벗어난 데이터가 있다면?  nan
```


```python
pd.cut(ages, bins)
#구간 정보, 카테고리 5개
```




    [NaN, (1.0, 20.0], (1.0, 20.0], (20.0, 30.0], (20.0, 30.0], ..., (50.0, 70.0], (1.0, 20.0], (30.0, 50.0], (30.0, 50.0], NaN]
    Length: 12
    Categories (5, interval[int64]): [(1, 20] < (20, 30] < (30, 50] < (50, 70] < (70, 100]]




```python
lb=["미청년","청년","중년","장년","노년"]
```


```python
mycuts=pd.cut(ages, bins, labels=lb)

```


```python
mycuts.categories
```




    Index(['미청년', '청년', '중년', '장년', '노년'], dtype='object')




```python
mycuts.codes
```




    array([-1,  0,  0,  1,  1,  2,  2,  3,  0,  2,  2, -1], dtype=int8)




```python
ages
```




    [0, 2, 10, 21, 23, 37, 31, 61, 20, 41, 32, 101]




```python

pd.DataFrame(ages)
```


```python
pd.cut(df4,ages, bins, labels=lb)
#df4 놓침
df4['age_cut']=pd.cut(df4,ages, bins, labels=lb)

```


    ---------------------------------------------------------------------------
    
    ValueError                                Traceback (most recent call last)
    
    <ipython-input-170-ae57bf44edc3> in <module>
    ----> 1 pd.cut(df4,ages, bins, labels=lb)
          2 #df4 놓침
          3 df4['age_cut']=pd.cut(df4,ages, bins, labels=lb)


    ~\anaconda3\lib\site-packages\pandas\core\reshape\tile.py in cut(x, bins, right, labels, retbins, precision, include_lowest, duplicates, ordered)
        222 
        223     original = x
    --> 224     x = _preprocess_for_cut(x)
        225     x, dtype = _coerce_to_type(x)
        226 


    ~\anaconda3\lib\site-packages\pandas\core\reshape\tile.py in _preprocess_for_cut(x)
        578         x = np.asarray(x)
        579     if x.ndim != 1:
    --> 580         raise ValueError("Input array must be 1 dimensional")
        581 
        582     return x


    ValueError: Input array must be 1 dimensional



```python
#데이터 프레임 합치기?
df['age_ages']=df4['age_cut'].astype(str)+d['ages'].astype(str)

```


```python
data= tlqkf
mycuts2=pd.qcut(data, 4 ,labels=['q1','q2','q3','q4'])
pd.vaule_counts(mycuts2)
```


    ---------------------------------------------------------------------------
    
    NameError                                 Traceback (most recent call last)
    
    <ipython-input-172-8c7b67c9f7e5> in <module>
    ----> 1 mycuts2=pd.qcut(data,4 ,labels=['q1','q2','q3','q4'])


    NameError: name 'data' is not defined


# set_index, reset_index
: 행 / 열 인덱스 교환 😀


```python
np.random.seed(0)
df1 = pd.DataFrame(np.vstack([list('ABCDE'),
                              np.round(np.random.rand(3, 5), 2)]).T,
                   columns=["C1", "C2", "C3", "C4"])
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
      <th>C1</th>
      <th>C2</th>
      <th>C3</th>
      <th>C4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>0.55</td>
      <td>0.65</td>
      <td>0.79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>0.72</td>
      <td>0.44</td>
      <td>0.53</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C</td>
      <td>0.6</td>
      <td>0.89</td>
      <td>0.57</td>
    </tr>
    <tr>
      <th>3</th>
      <td>D</td>
      <td>0.54</td>
      <td>0.96</td>
      <td>0.93</td>
    </tr>
    <tr>
      <th>4</th>
      <td>E</td>
      <td>0.42</td>
      <td>0.38</td>
      <td>0.07</td>
    </tr>
  </tbody>
</table>
</div>




```python
np.round(np.random.rand(3,5),2)
```




    array([[0.09, 0.02, 0.83, 0.78, 0.87],
           [0.98, 0.8 , 0.46, 0.78, 0.12],
           [0.64, 0.14, 0.94, 0.52, 0.41]])




```python
pd.DataFrame(np.vstack([list('ABCDE'), np.round(np.random.rand(3, 5), 2)]).T,
            columns=["C1", "C2", "C3", "C4"])

np.random.seed(0)
df1 = pd.DataFrame(np.vstack([list('ABCDE'),
                              np.round(np.random.rand(3, 5), 2)]).T,
                   columns=["C1", "C2", "C3", "C4"])

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
      <th>C1</th>
      <th>C2</th>
      <th>C3</th>
      <th>C4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>0.55</td>
      <td>0.65</td>
      <td>0.79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>0.72</td>
      <td>0.44</td>
      <td>0.53</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C</td>
      <td>0.6</td>
      <td>0.89</td>
      <td>0.57</td>
    </tr>
    <tr>
      <th>3</th>
      <td>D</td>
      <td>0.54</td>
      <td>0.96</td>
      <td>0.93</td>
    </tr>
    <tr>
      <th>4</th>
      <td>E</td>
      <td>0.42</td>
      <td>0.38</td>
      <td>0.07</td>
    </tr>
  </tbody>
</table>
</div>




```python
#set_index: 특정 열을 인덱스로 설정 -> 기존의 인덱스는 제거된다
df2=df1.set_index('C1')
df2

df2=df1.set_index('C2')
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
      <th>C1</th>
      <th>C3</th>
      <th>C4</th>
    </tr>
    <tr>
      <th>C2</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0.55</th>
      <td>A</td>
      <td>0.65</td>
      <td>0.79</td>
    </tr>
    <tr>
      <th>0.72</th>
      <td>B</td>
      <td>0.44</td>
      <td>0.53</td>
    </tr>
    <tr>
      <th>0.6</th>
      <td>C</td>
      <td>0.89</td>
      <td>0.57</td>
    </tr>
    <tr>
      <th>0.54</th>
      <td>D</td>
      <td>0.96</td>
      <td>0.93</td>
    </tr>
    <tr>
      <th>0.42</th>
      <td>E</td>
      <td>0.38</td>
      <td>0.07</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.reset_index()

#df2에서 index 열을 제거
df2.reset_index(drop=True)
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
      <th>C1</th>
      <th>C3</th>
      <th>C4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>0.65</td>
      <td>0.79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B</td>
      <td>0.44</td>
      <td>0.53</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C</td>
      <td>0.89</td>
      <td>0.57</td>
    </tr>
    <tr>
      <th>3</th>
      <td>D</td>
      <td>0.96</td>
      <td>0.93</td>
    </tr>
    <tr>
      <th>4</th>
      <td>E</td>
      <td>0.38</td>
      <td>0.07</td>
    </tr>
  </tbody>
</table>
</div>




```python
np.random.seed(0)
df3 = pd.DataFrame(np.round(np.random.randn(5, 4), 2),
                  columns=[['A','A','B','B'],['M','F','M','F']])
df3.columns.names=['Dept','Sex']
```


```python
df3
#0,1번열은 A부서 남,여
#2,3번열은 B부서 남,여

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
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th>Dept</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th>Sex</th>
      <th>M</th>
      <th>F</th>
      <th>M</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>999.00</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
  </tbody>
</table>
</div>




```python
np.random.seed(0)
df4 = pd.DataFrame(np.round(np.random.randn(6, 4), 2),
                   columns=[["A", "A", "B", "B"],
                            ["C", "D", "C", "D"]],
                   index=[["M", "M", "M", "F", "F", "F"],
                          ["id_" + str(i + 1) for i in range(3)] * 2])
df4.columns.names = ["Cidx1", "Cidx2"]
df4.index.names = ["Ridx1", "Ridx2"]
df4

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
      <th>Cidx1</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th></th>
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>Ridx1</th>
      <th>Ridx2</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">M</th>
      <th>id_1</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>id_1</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-2.55</td>
      <td>0.65</td>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
  </tbody>
</table>
</div>




```python
[1,2,3]*2
```




    [1, 2, 3, 1, 2, 3]



다중인덱스에서 stack함수 : 열-> 행 인덱스(열 인덱스가 90도 반시계 방향 회전
              unstack함수 : 행->열 인덱스


```python
df4.stack('Cidx1')
#df4.stack('Cidx2')
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
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>Ridx1</th>
      <th>Ridx2</th>
      <th>Cidx1</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="6" valign="top">M</th>
      <th rowspan="2" valign="top">id_1</th>
      <th>A</th>
      <td>1.76</td>
      <td>0.40</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">id_2</th>
      <th>A</th>
      <td>1.87</td>
      <td>-0.98</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">id_3</th>
      <th>A</th>
      <td>-0.10</td>
      <td>0.41</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th rowspan="6" valign="top">F</th>
      <th rowspan="2" valign="top">id_1</th>
      <th>A</th>
      <td>0.76</td>
      <td>0.12</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">id_2</th>
      <th>A</th>
      <td>1.49</td>
      <td>-0.21</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">id_3</th>
      <th>A</th>
      <td>-2.55</td>
      <td>0.65</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
  </tbody>
</table>
</div>




```python
df4
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
      <th>Cidx1</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th></th>
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>Ridx1</th>
      <th>Ridx2</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">M</th>
      <th>id_1</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>id_1</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-2.55</td>
      <td>0.65</td>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
  </tbody>
</table>
</div>




```python
df4.unstack('Ridx2')
df4.unstack(1)
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
      <th>Cidx1</th>
      <th colspan="6" halign="left">A</th>
      <th colspan="6" halign="left">B</th>
    </tr>
    <tr>
      <th>Cidx2</th>
      <th colspan="3" halign="left">C</th>
      <th colspan="3" halign="left">D</th>
      <th colspan="3" halign="left">C</th>
      <th colspan="3" halign="left">D</th>
    </tr>
    <tr>
      <th>Ridx2</th>
      <th>id_1</th>
      <th>id_2</th>
      <th>id_3</th>
      <th>id_1</th>
      <th>id_2</th>
      <th>id_3</th>
      <th>id_1</th>
      <th>id_2</th>
      <th>id_3</th>
      <th>id_1</th>
      <th>id_2</th>
      <th>id_3</th>
    </tr>
    <tr>
      <th>Ridx1</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
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
      <th>F</th>
      <td>0.76</td>
      <td>1.49</td>
      <td>-2.55</td>
      <td>0.12</td>
      <td>-0.21</td>
      <td>0.65</td>
      <td>0.44</td>
      <td>0.31</td>
      <td>0.86</td>
      <td>0.33</td>
      <td>-0.85</td>
      <td>-0.74</td>
    </tr>
    <tr>
      <th>M</th>
      <td>1.76</td>
      <td>1.87</td>
      <td>-0.10</td>
      <td>0.40</td>
      <td>-0.98</td>
      <td>0.41</td>
      <td>0.98</td>
      <td>0.95</td>
      <td>0.14</td>
      <td>2.24</td>
      <td>-0.15</td>
      <td>1.45</td>
    </tr>
  </tbody>
</table>
</div>




```python
df3
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
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th>Dept</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th>Sex</th>
      <th>M</th>
      <th>F</th>
      <th>M</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
  </tbody>
</table>
</div>




```python
df3["B"]
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
      <th>Sex</th>
      <th>M</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
  </tbody>
</table>
</div>

# iloc


```python
df3.loc[0,("B","M")] #0행 b,m열 출력

df3.loc[0,("B","M")] =999 # 값 변경
df3

#iloc는 튜플형식으로 들어가지 x 근데 주로 loc만 씀
df3.iloc[0,2]
```




    999.0




```python
df3.loc[(4), ("A","F")]
```




    -0.21




```python
df4.loc[("M","id_1"),("A","C")]
```




    1.76




```python
df4.loc[:,("A","C")]
```




    Ridx1  Ridx2
    M      id_1     1.76
           id_2     1.87
           id_3    -0.10
    F      id_1     0.76
           id_2     1.49
           id_3    -2.55
    Name: (A, C), dtype: float64




```python
df4.loc[("M","id_1"), :]
```




    Cidx1  Cidx2
    A      C        1.76
           D        0.40
    B      C        0.98
           D        2.24
    Name: (M, id_1), dtype: float64




```python
np.random.seed(0)
df4 = pd.DataFrame(np.round(np.random.randn(6, 4), 2),
                   columns=[["A", "A", "B", "B"],
                            ["C", "D", "C", "D"]],
                   index=[["M", "M", "M", "F", "F", "F"],
                          ["id_" + str(i + 1) for i in range(3)] * 2])
df4.columns.names = ["Cidx1", "Cidx2"]
df4.index.names = ["Ridx1", "Ridx2"]
df4
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
      <th>Cidx1</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th></th>
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>Ridx1</th>
      <th>Ridx2</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">M</th>
      <th>id_1</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>id_1</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-2.55</td>
      <td>0.65</td>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
  </tbody>
</table>
</div>




```python
df4.sum() #df4.sum(axis=0)
#df4.sum(axis=1)
df4.loc[("Tot", "Tot"),:]=df4.sum()
df4
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
      <th>Cidx1</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th></th>
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>Ridx1</th>
      <th>Ridx2</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">M</th>
      <th>id_1</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>id_1</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-2.55</td>
      <td>0.65</td>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
    <tr>
      <th>Tot</th>
      <th>Tot</th>
      <td>6.46</td>
      <td>0.78</td>
      <td>7.36</td>
      <td>4.56</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Ridx1와 Ridx2 순서 변경 swaplevel
df5=df4.swaplevel("Ridx1","Ridx2") #df4.swaplevel("Ridx1","Ridx2",0) 0이면 행, 1이면 열
df5
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
      <th>Cidx1</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th></th>
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>Ridx2</th>
      <th>Ridx1</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>id_1</th>
      <th>M</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>id_2</th>
      <th>M</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>id_3</th>
      <th>M</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th>id_1</th>
      <th>F</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>id_2</th>
      <th>F</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th>id_3</th>
      <th>F</th>
      <td>-2.55</td>
      <td>0.65</td>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
    <tr>
      <th>Tot</th>
      <th>Tot</th>
      <td>6.46</td>
      <td>0.78</td>
      <td>7.36</td>
      <td>4.56</td>
    </tr>
  </tbody>
</table>
</div>




```python
df6=df4.swaplevel("Cidx1","Cidx2",1) 
df6
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
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th></th>
      <th>Cidx1</th>
      <th>A</th>
      <th>A</th>
      <th>B</th>
      <th>B</th>
    </tr>
    <tr>
      <th>Ridx1</th>
      <th>Ridx2</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">M</th>
      <th>id_1</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">F</th>
      <th>id_1</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>id_2</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th>id_3</th>
      <td>-2.55</td>
      <td>0.65</td>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
    <tr>
      <th>Tot</th>
      <th>Tot</th>
      <td>6.46</td>
      <td>0.78</td>
      <td>7.36</td>
      <td>4.56</td>
    </tr>
  </tbody>
</table>
</div>




```python
df5
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
      <th>Cidx1</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th></th>
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>Ridx2</th>
      <th>Ridx1</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>id_1</th>
      <th>M</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>id_2</th>
      <th>M</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>id_3</th>
      <th>M</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th>id_1</th>
      <th>F</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>id_2</th>
      <th>F</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th>id_3</th>
      <th>F</th>
      <td>-2.55</td>
      <td>0.65</td>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
    <tr>
      <th>Tot</th>
      <th>Tot</th>
      <td>6.46</td>
      <td>0.78</td>
      <td>7.36</td>
      <td>4.56</td>
    </tr>
  </tbody>
</table>
</div>




```python
df5.sort_index(level=1)
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
      <th>Cidx1</th>
      <th colspan="2" halign="left">A</th>
      <th colspan="2" halign="left">B</th>
    </tr>
    <tr>
      <th></th>
      <th>Cidx2</th>
      <th>C</th>
      <th>D</th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>Ridx2</th>
      <th>Ridx1</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>id_1</th>
      <th>F</th>
      <td>0.76</td>
      <td>0.12</td>
      <td>0.44</td>
      <td>0.33</td>
    </tr>
    <tr>
      <th>id_2</th>
      <th>F</th>
      <td>1.49</td>
      <td>-0.21</td>
      <td>0.31</td>
      <td>-0.85</td>
    </tr>
    <tr>
      <th>id_3</th>
      <th>F</th>
      <td>-2.55</td>
      <td>0.65</td>
      <td>0.86</td>
      <td>-0.74</td>
    </tr>
    <tr>
      <th>id_1</th>
      <th>M</th>
      <td>1.76</td>
      <td>0.40</td>
      <td>0.98</td>
      <td>2.24</td>
    </tr>
    <tr>
      <th>id_2</th>
      <th>M</th>
      <td>1.87</td>
      <td>-0.98</td>
      <td>0.95</td>
      <td>-0.15</td>
    </tr>
    <tr>
      <th>id_3</th>
      <th>M</th>
      <td>-0.10</td>
      <td>0.41</td>
      <td>0.14</td>
      <td>1.45</td>
    </tr>
    <tr>
      <th>Tot</th>
      <th>Tot</th>
      <td>6.46</td>
      <td>0.78</td>
      <td>7.36</td>
      <td>4.56</td>
    </tr>
  </tbody>
</table>
</div>



# 과제


1.모든 행과 열에 라벨을 가지는 5 x 5 이상의 크기를 가지는 데이터프레임을 만든다.
최대한 다양한 방법으로 특정한 행과 열을 선택한다.



```python
df = pd.DataFrame(np.arange(0, 25).reshape(5, 5),
index = ['a','b','c','d','e'], columns = ['A', 'B', 'C', 'D','E'])
df

df.A
df.loc['a':'b']
df.loc['c',['C','E']] 
```




    C    12
    E    14
    Name: c, dtype: int32



2. 타이타닉호 승객 데이터의 데이터 개수를 각 열마다 구해본다.
결측값의 개수를 파악해본다


```python
t=sns.load_dataset("titanic")
t.count()
t.isnull().sum() #age 177, deck 688

```




    survived         0
    pclass           0
    sex              0
    age            177
    sibsp            0
    parch            0
    fare             0
    embarked         2
    class            0
    who              0
    adult_male       0
    deck           688
    embark_town      2
    alive            0
    alone            0
    dtype: int64



3. sort_values 메서드를 사용하여 타이타닉호 승객에 대해 
성별(sex) 인원수, 나이별(age) 인원수, 선실별(class) 인원수, 사망/생존(alive) 인원수를 구하라.



```python
t['sex'].value_counts()
t['age'].value_counts()
t['class'].value_counts()
t['alive'].value_counts()

#t['alive'].sort_values

```




    no     549
    yes    342
    Name: alive, dtype: int64



4.
타이타닉호 승객의 평균 나이를 구하라.
타이타닉호 승객중 여성 승객의 평균 나이를 구하라.
타이타닉호 승객중 1등실 선실의 여성 승객의 평균 나이를 구하라.


```python
t['age'].mean()
t.age[t.sex=='female'].mean()
t.age[t.pclass==1].mean()

```




    38.233440860215055



5. 타이타닉호의 승객에 대해 나이와 성별에 의한 카테고리 열인 category1 열을 만들어라. category1 카테고리는 다음과 같이 정의된다.
20살이 넘으면 성별을 그대로 사용한다.
20살 미만이면 성별에 관계없이 “child”라고 한다.


```python
t['category1'] = t.apply(lambda x: x.sex if x.age >= 20 else "child", axis=1)
t
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
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
      <th>category1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
      <td>female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
      <td>female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
      <td>female</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
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
    </tr>
    <tr>
      <th>886</th>
      <td>0</td>
      <td>2</td>
      <td>male</td>
      <td>27.0</td>
      <td>0</td>
      <td>0</td>
      <td>13.0000</td>
      <td>S</td>
      <td>Second</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
    </tr>
    <tr>
      <th>887</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>19.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>B</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
      <td>child</td>
    </tr>
    <tr>
      <th>888</th>
      <td>0</td>
      <td>3</td>
      <td>female</td>
      <td>NaN</td>
      <td>1</td>
      <td>2</td>
      <td>23.4500</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
      <td>child</td>
    </tr>
    <tr>
      <th>889</th>
      <td>1</td>
      <td>1</td>
      <td>male</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>C</td>
      <td>First</td>
      <td>man</td>
      <td>True</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>True</td>
      <td>male</td>
    </tr>
    <tr>
      <th>890</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>32.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.7500</td>
      <td>Q</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Queenstown</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
    </tr>
  </tbody>
</table>
<p>891 rows × 16 columns</p>
</div>



6.
타이타닉호의 승객 중 나이를 명시하지 않은 고객은 나이를 명시한 고객의 평균 나이 값이 되도록 titanic 데이터프레임을 고쳐라.




```python
mean_age= np.round(t.age.mean(),2)
t.age=t.age.fillna(mean_age)
t.age

```




    0      22.0
    1      38.0
    2      26.0
    3      35.0
    4      35.0
           ... 
    886    27.0
    887    19.0
    888    29.7
    889    26.0
    890    32.0
    Name: age, Length: 891, dtype: float64




7. 타이타닉호의 승객에 대해 나이와 성별에 의한 카테고리 열인 category2 열을 만들어라. category2 카테고리는 다음과 같이 정의된다.
성별을 나타내는 문자열 male 또는 female로 시작한다.
성별을 나타내는 문자열 뒤에 나이를 나타내는 문자열이 온다.
예를 들어 27살 남성은 male27 값이 된다.


```python
t['category2']=t['sex']+t['age'].astype(str)
t
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
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
      <th>category1</th>
      <th>category2</th>
      <th>cats</th>
      <th>category3</th>
      <th>tmp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
      <td>male</td>
      <td>male22.0</td>
      <td>청년</td>
      <td>청년남자</td>
      <td>남자</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
      <td>female</td>
      <td>female38.0</td>
      <td>중년</td>
      <td>중년여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
      <td>female</td>
      <td>female26.0</td>
      <td>청년</td>
      <td>청년여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
      <td>female</td>
      <td>female35.0</td>
      <td>중년</td>
      <td>중년여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
      <td>male35.0</td>
      <td>중년</td>
      <td>중년남자</td>
      <td>남자</td>
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
    </tr>
    <tr>
      <th>886</th>
      <td>0</td>
      <td>2</td>
      <td>male</td>
      <td>27.0</td>
      <td>0</td>
      <td>0</td>
      <td>13.0000</td>
      <td>S</td>
      <td>Second</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
      <td>male27.0</td>
      <td>청년</td>
      <td>청년남자</td>
      <td>남자</td>
    </tr>
    <tr>
      <th>887</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>19.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>B</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
      <td>child</td>
      <td>female19.0</td>
      <td>미성년자</td>
      <td>미성년자여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>888</th>
      <td>0</td>
      <td>3</td>
      <td>female</td>
      <td>29.7</td>
      <td>1</td>
      <td>2</td>
      <td>23.4500</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
      <td>child</td>
      <td>female29.7</td>
      <td>청년</td>
      <td>청년여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>889</th>
      <td>1</td>
      <td>1</td>
      <td>male</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>C</td>
      <td>First</td>
      <td>man</td>
      <td>True</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>True</td>
      <td>male</td>
      <td>male26.0</td>
      <td>청년</td>
      <td>청년남자</td>
      <td>남자</td>
    </tr>
    <tr>
      <th>890</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>32.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.7500</td>
      <td>Q</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Queenstown</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
      <td>male32.0</td>
      <td>중년</td>
      <td>중년남자</td>
      <td>남자</td>
    </tr>
  </tbody>
</table>
<p>891 rows × 20 columns</p>
</div>




8.타이타닉호 승객을 ‘미성년자’, ‘청년’, ‘중년’, ‘장년’, ‘노년’ 나이 그룹으로 나눈다.

bins = [1, 20, 30, 50, 70, 100]
labels = ["미성년자", "청년", "중년", "장년", "노년"]
그리고 각 나이 그룹의 승객 비율을 구한다. 비율의 전체 합은 1이 되어야 한다.



```python
bins = [1, 20, 30, 50, 70, 100]
labels = ["미성년자", "청년", "중년", "장년", "노년"]  
t['cats'] = pd.cut(t.age, bins, labels=labels)
cats2=t.groupby(cats).size()
cats2/t.age.count()
```




    age
    미성년자    0.185185
    청년      0.456790
    중년      0.270483
    장년      0.066218
    노년      0.005612
    dtype: float64



9. 타이타닉호의 승객에 대해 나이와 성별에 의한 카테고리 열인 category3 열을 만들어라. category3 카테고리는 다음과 같이 정의된다.
20살 미만이면 성별에 관계없이 “미성년자”라고 한다.
20살 이상이면 나이에 따라 “청년”, “중년”, “장년”, “노년”을 구분하고 그 뒤에 성별을 나타내는 “남성”, “여성”을 붙인다.


```python
t['tmp']=np.where(t.sex=='female',"여자","남자")

t['category3']= np.where(t.age>=20, cats ,"미성년자")
t['category3']=t['category3']+t.tmp.astype(str)
t

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
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
      <th>category1</th>
      <th>category2</th>
      <th>cats</th>
      <th>category3</th>
      <th>tmp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
      <td>male</td>
      <td>male22.0</td>
      <td>청년</td>
      <td>청년남자</td>
      <td>남자</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
      <td>female</td>
      <td>female38.0</td>
      <td>중년</td>
      <td>중년여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
      <td>female</td>
      <td>female26.0</td>
      <td>청년</td>
      <td>청년여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
      <td>female</td>
      <td>female35.0</td>
      <td>중년</td>
      <td>중년여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
      <td>male35.0</td>
      <td>중년</td>
      <td>중년남자</td>
      <td>남자</td>
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
    </tr>
    <tr>
      <th>886</th>
      <td>0</td>
      <td>2</td>
      <td>male</td>
      <td>27.0</td>
      <td>0</td>
      <td>0</td>
      <td>13.0000</td>
      <td>S</td>
      <td>Second</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
      <td>male27.0</td>
      <td>청년</td>
      <td>청년남자</td>
      <td>남자</td>
    </tr>
    <tr>
      <th>887</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>19.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>B</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
      <td>child</td>
      <td>female19.0</td>
      <td>미성년자</td>
      <td>미성년자여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>888</th>
      <td>0</td>
      <td>3</td>
      <td>female</td>
      <td>29.7</td>
      <td>1</td>
      <td>2</td>
      <td>23.4500</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
      <td>child</td>
      <td>female29.7</td>
      <td>청년</td>
      <td>청년여자</td>
      <td>여자</td>
    </tr>
    <tr>
      <th>889</th>
      <td>1</td>
      <td>1</td>
      <td>male</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>30.0000</td>
      <td>C</td>
      <td>First</td>
      <td>man</td>
      <td>True</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>True</td>
      <td>male</td>
      <td>male26.0</td>
      <td>청년</td>
      <td>청년남자</td>
      <td>남자</td>
    </tr>
    <tr>
      <th>890</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>32.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.7500</td>
      <td>Q</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Queenstown</td>
      <td>no</td>
      <td>True</td>
      <td>male</td>
      <td>male32.0</td>
      <td>중년</td>
      <td>중년남자</td>
      <td>남자</td>
    </tr>
  </tbody>
</table>
<p>891 rows × 20 columns</p>
</div>



10. (다중인덱스)
A 반 학생 5명과 B반 학생 5명의 국어, 영어, 수학 점수를 나타내는 데이터프레임을 다음과 같이 만든다.
“반”, “번호”, “국어”, “영어”, “수학” 을 열로 가지는 데이터프레임 df_score3을 만든다.

df_score3을 변형하여 1차 행 인덱스로 “반”을 2차 행 인덱스로 “번호”을 가지는 데이터프레임 df_score4을 만든다.

데이터 프레임 df_score4에 각 학생의 평균을 나타내는 행을 오른쪽에 추가한다.

df_score3을 변형하여 행 인덱스로 “번호”를, 1차 열 인덱스로 “국어”, “영어”, “수학”을, 

2차 열 인덱스로 “반”을 가지는 데이터프레임 df_score5을 만든다.
데이터 프레임 df_score5에 각 반별 각 과목의 평균을 나타내는 행을 아래에 추가한다.




```python
np.random.seed(2021)
df_score3=pd.DataFrame(np.vstack([['A']*5+['B']*5,
                                  list(range(1,6))*2,
                                  (np.random.rand(3,10)*100).astype(int)]).T,
                       columns=['반','번호','국어','영어','수학'])
df_score3
df_score4=df_score3.set_index(['반','번호']).astype(int)
df_score4
df_score4['mean']=np.round(df_score4.mean(axis=1),2)
df_score4

df_score5=df_score3.set_index(['반','번호'])
df_score5=df_score4.unstack(0)

df_score5.loc[("mean"),:]=np.round(df_score5.mean(),2)
df_score5
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
      <th colspan="2" halign="left">국어</th>
      <th colspan="2" halign="left">영어</th>
      <th colspan="2" halign="left">수학</th>
      <th colspan="2" halign="left">mean</th>
    </tr>
    <tr>
      <th>반</th>
      <th>A</th>
      <th>B</th>
      <th>A</th>
      <th>B</th>
      <th>A</th>
      <th>B</th>
      <th>A</th>
      <th>B</th>
    </tr>
    <tr>
      <th>번호</th>
      <th></th>
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
      <th>1</th>
      <td>60.0</td>
      <td>12.0</td>
      <td>9.0</td>
      <td>56.0</td>
      <td>45.0</td>
      <td>47.0</td>
      <td>38.00</td>
      <td>38.33</td>
    </tr>
    <tr>
      <th>2</th>
      <td>73.0</td>
      <td>17.0</td>
      <td>5.0</td>
      <td>61.0</td>
      <td>20.0</td>
      <td>51.0</td>
      <td>32.67</td>
      <td>43.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>13.0</td>
      <td>75.0</td>
      <td>96.0</td>
      <td>96.0</td>
      <td>56.0</td>
      <td>82.0</td>
      <td>55.00</td>
      <td>84.33</td>
    </tr>
    <tr>
      <th>4</th>
      <td>31.0</td>
      <td>66.0</td>
      <td>61.0</td>
      <td>57.0</td>
      <td>19.0</td>
      <td>73.0</td>
      <td>37.00</td>
      <td>65.33</td>
    </tr>
    <tr>
      <th>5</th>
      <td>99.0</td>
      <td>78.0</td>
      <td>8.0</td>
      <td>37.0</td>
      <td>58.0</td>
      <td>6.0</td>
      <td>55.00</td>
      <td>40.33</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>55.2</td>
      <td>49.6</td>
      <td>35.8</td>
      <td>61.4</td>
      <td>39.6</td>
      <td>51.8</td>
      <td>43.53</td>
      <td>54.26</td>
    </tr>
  </tbody>
</table>
</div>


