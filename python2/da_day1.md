```python
import numpy as np 
```


```python
np.__version__ #버전 확인
```


    '1.19.2'



# 제목을 달아봅시다
## 제목을 달아봅시다2
### 제목을 달아봅시다3

[naver](http://www.naver.com/)
__중요__ 
**중요**
_중요_
*조금중요*
y=x+10
$y=x+10$
1. 첫번째
2.두번째

https://gist.github.com/ihoneymon/652be052a0727ad59601


```python
shape: 배열의 구조
    3차원 배열 행, 열 , 채널 방향 axis=0 행방향 1이면 열방향 2면 채널방향
    
    
```


```python
#파이썬 1차원 배열 (리스트) -> 넘파이 배열 생성
arr=[1,2,3]
```


```python
a=np.array(arr)
```


```python
a
```




    array([1, 2, 3])




```python
myarr=np.arange(1000000)
```


```python
myarr
```




    array([     0,      1,      2, ..., 999997, 999998, 999999])




```python
mylist=list(range(1000000))
```




```python
#모든 원소 *2
%time for _ in range(10):mylist2=[x*2 for x in mylist]
```

    Wall time: 1.6 s



```python
mylist2
```




    [0,
     2,
     4,
     6,
     8,
     ... (중략)
     1996,
     1998,
     ...]




```python
%time for _ in range(10):myarr2= myarr*2
    #넘파이 배열이 훨씬 빠르고 식도 간결함 
```

    Wall time: 30.9 ms



```python
myarr2
```




    array([      0,       2,       4, ..., 1999994, 1999996, 1999998])



# random.randn()


```python
#n차원 배열 객체 ?
#대량의 데이터 집합을 저장할 수 있는 구조
data=np.random.randn(2,3) #평균이 0 표준편차 1 난수 생성
```


```python
data
```




    array([[-1.33185778,  0.0754891 ,  1.34637105],
           [ 0.28338822,  0.64090601, -0.18891298]])




```python
data*10
```




    array([[-13.31857779,   0.75489099,  13.46371053],
           [  2.83388221,   6.40906009,  -1.88912983]])




```python
data+data #요소들끼리 덧셈
```




    array([[-2.66371556,  0.1509782 ,  2.69274211],
           [ 0.56677644,  1.28181202, -0.37782597]])




```python
data.shape
data.dtype
```




    dtype('float64')




```python
data1=[6,7.5,8,0,1]
```


```python
arr1=np.array(data1) #동일 타입으로 자동변환된다
arr1
```




    array([6. , 7.5, 8. , 0. , 1. ])



# np.zeros


```python
np.zeros(10)
```




    array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.])




```python
np.zeros((3,6))
```




    array([[0., 0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0., 0.]])

# np.ones


```python
np.ones((2,3))
```




    array([[1., 1., 1.],
           [1., 1., 1.]])




```python
np.arange(10)
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
 list(range(10)) #파이썬
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
arr=np.arange(10)
arr.dtype
```




    dtype('int32')




```python
farr=arr.astype(np.float64)
```


```python
farr
```




    array([0., 1., 2., 3., 4., 5., 6., 7., 8., 9.])




```python
arr=np.array([[1,2],[3,4]])
```


```python
arr*arr #요소간 곱셈 element-wise product
arr**2
arr**0.5 #
```




    array([[1.        , 1.41421356],
           [1.73205081, 2.        ]])




```python
arr2= np.ones((2,2))
arr2
```




    array([[1., 1.],
           [1., 1.]])




```python
arr>arr2
```




    array([[False,  True],
           [ True,  True]])




```python
arr=np.arange(10)*2
arr

```




    array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])




```python
arr[5:8] #5번 인덱스 부터 ~7번까지
```




    array([10, 12, 14])




```python
arr2=arr[4:8]
```
arr[:]=11 #일괄적으로 모든 값을 갱신
arr

```python
arr=22
```


```python
arr #안됨 arr이 array에서 정수변수로 변경
```




    22




```python
arr=np.arange(10,16)
```


```python
arr
```




    array([10, 11, 12, 13, 14, 15])




```python
arr.reshape(2,3) #1차원이 2차원으로 
```




    array([[10, 11, 12],
           [13, 14, 15]])




```python
arr2d=arr.reshape(2,3)
```


```python
arr2d
```




    array([[10, 11, 12],
           [13, 14, 15]])




```python
arr2d[0]
```




    array([10, 11, 12])




```python
arr=np.arange(0,4*2*4)
```


```python
arr.shape
```




    (32,)




```python
arr.reshape()
```


    ---------------------------------------------------------------------------
    
    TypeError                                 Traceback (most recent call last)
    
    <ipython-input-84-ffe506ee2427> in <module>
    ----> 1 arr.reshape()


    TypeError: reshape() takes exactly 1 argument (0 given)



```python
v.ndim #속성 , 3차원
v.sum() #함수, 모든 요소의 합
v.sum(axis=0)
```


    ---------------------------------------------------------------------------
    
    NameError                                 Traceback (most recent call last)
    
    <ipython-input-85-860721723004> in <module>
    ----> 1 v.ndim #속성 , 3차원
          2 v.sum() #함수, 모든 요소의 합


    NameError: name 'v' is not defined



```python
axis=None, 모든 요소의 합 -> 1개의 스칼라값
axis=0, x축 기준으로 여러개의 row를 한개로 합침
axis=1, y축 기준으로 row 별로 column 값들을 한개로 합침
axis=2, z축 기준으로 column의 depth 값들을 한개로 합침 
```


```python
arr[0]
```




    0




```python
arr=np.arange(0,31)
```


```python
arr
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30])




```python
np.full((2,2),5) #자리만들고 초기화
```




    array([[5, 5],
           [5, 5]])




```python
np.eye(3)  #대각요소 1인 행렬
```




    array([[1., 0., 0.],
           [0., 1., 0.],
           [0., 0., 1.]])




```python
np.empty((3,2)) #3행2열 쓰레기값으로 초기화 .. 뭔가 이상
```




    array([[1., 1.],
           [1., 1.],
           [1., 1.]])




```python
a=np.array([[1,2,3],[4,5,6]])
```


```python
b=np.ones_like(a) #a 배열과 같은 구조(2,3)를 1로 초기화한 값으로 생성
b
```




    array([[1, 1, 1],
           [1, 1, 1]])




```python
np.show_config()
```

    blas_mkl_info:
        libraries = ['mkl_rt']
        library_dirs = ['C:/Users/akrnr/anaconda3\\Library\\lib']
        define_macros = [('SCIPY_MKL_H', None), ('HAVE_CBLAS', None)]
        include_dirs = ['C:/Users/akrnr/anaconda3\\Library\\include']
    blas_opt_info:
        libraries = ['mkl_rt']
        library_dirs = ['C:/Users/akrnr/anaconda3\\Library\\lib']
        define_macros = [('SCIPY_MKL_H', None), ('HAVE_CBLAS', None)]
        include_dirs = ['C:/Users/akrnr/anaconda3\\Library\\include']
    lapack_mkl_info:
        libraries = ['mkl_rt']
        library_dirs = ['C:/Users/akrnr/anaconda3\\Library\\lib']
        define_macros = [('SCIPY_MKL_H', None), ('HAVE_CBLAS', None)]
        include_dirs = ['C:/Users/akrnr/anaconda3\\Library\\include']
    lapack_opt_info:
        libraries = ['mkl_rt']
        library_dirs = ['C:/Users/akrnr/anaconda3\\Library\\lib']
        define_macros = [('SCIPY_MKL_H', None), ('HAVE_CBLAS', None)]
        include_dirs = ['C:/Users/akrnr/anaconda3\\Library\\include']



```python
Z=np.zeros(10)
Z
```




    array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.])




```python
Z.itemsize
Z.size
print("%d bytes" % (Z.size * Z.itemsize))
```

    80 bytes



```python
#크기가 10인 Z배열을 0으로 초기화 -> 5번째 데이터를 1로 변경 &출력

Z=np.zeros(10)
```


```python
Z
```




    array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.])




```python
Z[4]=1
```


```python
Z
```




    array([0., 0., 0., 0., 1., 0., 0., 0., 0., 0.])




```python
Z=np.arange(10,50)
Z
```




    array([10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26,
           27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43,
           44, 45, 46, 47, 48, 49])




```python
Z[:] #순방향
Z[::] #순방향
Z[::-1] #역방향

```




    array([49, 48, 47, 46, 45, 44, 43, 42, 41, 40, 39, 38, 37, 36, 35, 34, 33,
           32, 31, 30, 29, 28, 27, 26, 25, 24, 23, 22, 21, 20, 19, 18, 17, 16,
           15, 14, 13, 12, 11, 10])




```python
np.arange(9)
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8])




```python
z=np.random.random((2,3)) #난수발생 범위 0이상 1미만
z
```




    array([[0.06453473, 0.10600265, 0.19332899],
           [0.1373335 , 0.72191498, 0.53175906]])




```python
z.min()
z.max()
```




    0.7219149765098254




```python
z=np.random.random(20)
m=z.mean
```


```python
print(m)
```

    <built-in method mean of numpy.ndarray object at 0x000001568A3AE760>



```python
#10행 10열
a=np.ones((10,10))
```


```python
a[1:9,1:9] =0
```


```python
a
```




    array([[1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 1., 1., 1., 1., 1., 1., 1., 1., 1.]])




```python
a=np.ones((10,10))
a[1:9,1:9] =0
a
```




    array([[1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 1., 1., 1., 1., 1., 1., 1., 1., 1.]])




```python
ㅛ#테두리만 지정하는 방법
Z=np.ones((10,10))
Z[1:-1,1:-1]=0 #-1은 맨 마지막 앞 까지 
```


```python
Z
```




    array([[1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 0., 0., 0., 0., 0., 0., 0., 0., 1.],
           [1., 1., 1., 1., 1., 1., 1., 1., 1., 1.]])



