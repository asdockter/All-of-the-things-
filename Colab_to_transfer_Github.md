![rmotr](https://user-images.githubusercontent.com/7065401/52071918-bda15380-2562-11e9-828c-7f95297e4a82.png)
<hr style="margin-bottom: 40px;">

<img src="https://user-images.githubusercontent.com/7065401/39118381-910eb0c2-46e9-11e8-81f1-a5b897401c23.jpeg"
    style="width:300px; float: right; margin: 0 40px 40px 40px;"></img>

# Numpy: Numeric computing library

NumPy (Numerical Python) is one of the core packages for numerical computing in Python. Pandas, Matplotlib, Statmodels and many other Scientific libraries rely on NumPy.

NumPy major contributions are:

* Efficient numeric computation with C primitives
* Efficient collections with vectorized operations
* An integrated and natural Linear Algebra API
* A C API for connecting NumPy with libraries written in C, C++, or FORTRAN.

Let's develop on efficiency. In Python, **everything is an object**, which means that even simple ints are also objects, with all the required machinery to make object work. We call them "Boxed Ints". In contrast, NumPy uses primitive numeric types (floats, ints) which makes storing and computation efficient.

<img src="https://docs.google.com/drawings/d/e/2PACX-1vTkDtKYMUVdpfVb3TTpr_8rrVtpal2dOknUUEOu85wJ1RitzHHf5nsJqz1O0SnTt8BwgJjxXMYXyIqs/pub?w=726&h=396" />


![purple-divider](https://user-images.githubusercontent.com/7065401/52071927-c1cd7100-2562-11e9-908a-dde91ba14e59.png)

## Hands on! 


```python
import sys
import numpy as np
```

## Basic Numpy Arrays


```python
np.array([1, 2, 3, 4])
```




    array([1, 2, 3, 4])




```python
a = np.array([1, 2, 3, 4])
```


```python
b = np.array([0, .5, 1, 1.5, 2])
```


```python
a[0], a[1]
```




    (1, 2)




```python
a[0:]
```




    array([1, 2, 3, 4])




```python
a[1:3]
```




    array([2, 3])




```python
a[1:-1]
```




    array([2, 3])




```python
a[::2]
```




    array([1, 3])




```python
b
```




    array([0. , 0.5, 1. , 1.5, 2. ])




```python
b[0], b[2], b[-1]
```




    (0.0, 1.0, 2.0)




```python
b[[0, 2, -1]]
```




    array([0., 1., 2.])



![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Array Types


```python
a
```




    array([1, 2, 3, 4])




```python
a.dtype
```




    dtype('int64')




```python
b
```




    array([0. , 0.5, 1. , 1.5, 2. ])




```python
b.dtype
```




    dtype('float64')




```python
np.array([1, 2, 3, 4], dtype=np.float)
```




    array([1., 2., 3., 4.])




```python
np.array([1, 2, 3, 4], dtype=np.int8)
```




    array([1, 2, 3, 4], dtype=int8)




```python
c = np.array(['a', 'b', 'c'])
```


```python
c.dtype
```




    dtype('<U1')




```python
d = np.array([{'a': 1}, sys])
```


```python
d.dtype
```




    dtype('O')



![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Dimensions and shapes


```python
A = np.array([
    [1, 2, 3],
    [4, 5, 6]
])
```


```python
A.shape
```




    (2, 3)




```python
A.ndim
```




    2




```python
A.size
```




    6




```python
B = np.array([
    [
        [12, 11, 10],
        [9, 8, 7],
    ],
    [
        [6, 5, 4],
        [3, 2, 1]
    ]
])
```


```python
B
```




    array([[[12, 11, 10],
            [ 9,  8,  7]],
    
           [[ 6,  5,  4],
            [ 3,  2,  1]]])




```python
B.shape
```




    (2, 2, 3)




```python
B.ndim
```




    3




```python
B.size
```




    12



If the shape isn't consistent, it'll just fall back to regular Python objects:


```python
C = np.array([
    [
        [12, 11, 10],
        [9, 8, 7],
    ],
    [
        [6, 5, 4]
    ]
])
```


```python
C.dtype
```




    dtype('O')




```python
C.shape
```




    (2,)




```python
C.size
```




    2




```python
type(C[0])
```

![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Indexing and Slicing of Matrices


```python
# Square matrix
A = np.array([
#.   0. 1. 2
    [1, 2, 3], # 0
    [4, 5, 6], # 1
    [7, 8, 9]  # 2
])
```


```python
A[1]
```




    array([4, 5, 6])




```python
A[1][0]
```




    4




```python
# A[d1, d2, d3, d4]
```


```python
A[1, 0]
```




    4




```python
A[0:2]
```




    array([[1, 2, 3],
           [4, 5, 6]])




```python
A[:, :2]
```




    array([[1, 2],
           [4, 5],
           [7, 8]])




```python
A[:2, :2]
```




    array([[1, 2],
           [4, 5]])




```python
A[:2, 2:]
```




    array([[3],
           [6]])




```python
A
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])




```python
A[1] = np.array([10, 10, 10])
```


```python
A
```




    array([[ 1,  2,  3],
           [10, 10, 10],
           [ 7,  8,  9]])




```python
A[2] = 99
```


```python
A
```




    array([[ 1,  2,  3],
           [10, 10, 10],
           [99, 99, 99]])



![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Summary statistics


```python
a = np.array([1, 2, 3, 4])
```


```python
a.sum()
```




    10




```python
a.mean()
```




    2.5




```python
a.std()
```




    1.118033988749895




```python
a.var()
```




    1.25




```python
A = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])
```


```python
A.sum()
```




    45




```python
A.mean()
```




    5.0




```python
A.std()
```




    2.581988897471611




```python
A.sum(axis=0)
```




    array([12, 15, 18])




```python
A.sum(axis=1)
```




    array([ 6, 15, 24])




```python
A.mean(axis=0)
```




    array([4., 5., 6.])




```python
A.mean(axis=1)
```




    array([2., 5., 8.])




```python
A.std(axis=0)
```




    array([2.44948974, 2.44948974, 2.44948974])




```python
A.std(axis=1)
```




    array([0.81649658, 0.81649658, 0.81649658])



And [many more](https://docs.scipy.org/doc/numpy-1.13.0/reference/arrays.ndarray.html#array-methods)...

![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Broadcasting and Vectorized operations


```python
a = np.arange(4)
```


```python
a
```




    array([0, 1, 2, 3])




```python
a + 10
```




    array([10, 11, 12, 13])




```python
a * 10
```




    array([ 0, 10, 20, 30])




```python
a
```




    array([0, 1, 2, 3])




```python
a += 100
```


```python
a
```




    array([100, 101, 102, 103])




```python
l = [0, 1, 2, 3]
```


```python
[i * 10 for i in l]
```




    [0, 10, 20, 30]




```python
a = np.arange(4)
```


```python
a
```




    array([0, 1, 2, 3])




```python
b = np.array([10, 10, 10, 10])
```


```python
b
```




    array([10, 10, 10, 10])




```python
a + b
```




    array([10, 11, 12, 13])




```python
a * b
```




    array([ 0, 10, 20, 30])



![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Boolean arrays
_(Also called masks)_


```python
a = np.arange(4)
```


```python
a
```




    array([0, 1, 2, 3])




```python
a[0], a[-1]
```




    (0, 3)




```python
a[[0, -1]]
```




    array([0, 3])




```python
a[[True, False, False, True]]
```




    array([0, 3])




```python
a
```




    array([0, 1, 2, 3])




```python
a >= 2
```




    array([False, False,  True,  True])




```python
a[a >= 2]
```




    array([2, 3])




```python
a.mean()
```




    1.5




```python
a[a > a.mean()]
```




    array([2, 3])




```python
a[~(a > a.mean())]
```




    array([0, 1])




```python
a[(a == 0) | (a == 1)]
```




    array([0, 1])




```python
a[(a <= 2) & (a % 2 == 0)]
```




    array([0, 2])




```python
A = np.random.randint(100, size=(3, 3))
```


```python
A
```




    array([[71,  6, 42],
           [40, 94, 24],
           [ 2, 85, 36]])




```python
A[np.array([
    [True, False, True],
    [False, True, False],
    [True, False, True]
])]
```




    array([71, 42, 94,  2, 36])




```python
A > 30
```




    array([[ True, False,  True],
           [ True,  True, False],
           [False,  True,  True]])




```python
A[A > 30]
```




    array([71, 42, 40, 94, 85, 36])



![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Linear Algebra


```python
A = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])
```


```python
B = np.array([
    [6, 5],
    [4, 3],
    [2, 1]
])
```


```python
A.dot(B)
```




    array([[20, 14],
           [56, 41],
           [92, 68]])




```python
A @ B
```




    array([[20, 14],
           [56, 41],
           [92, 68]])




```python
B.T
```




    array([[6, 4, 2],
           [5, 3, 1]])




```python
A
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])




```python
B.T @ A
```




    array([[36, 48, 60],
           [24, 33, 42]])



![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Size of objects in Memory

### Int, floats


```python
# An integer in Python is > 24bytes
sys.getsizeof(1)
```




    28




```python
# Longs are even larger
sys.getsizeof(10**100)
```




    72




```python
# Numpy size is much smaller
np.dtype(int).itemsize
```




    8




```python
# Numpy size is much smaller
np.dtype(np.int8).itemsize
```




    1




```python
np.dtype(float).itemsize
```




    8



### Lists are even larger


```python
# A one-element list
sys.getsizeof([1])
```


```python
# An array of one element in numpy
np.array([1]).nbytes
```

### And performance is also important


```python
l = list(range(100000))
```


```python
a = np.arange(100000)
```


```python
%time np.sum(a ** 2)
```

    CPU times: user 1.06 ms, sys: 279 µs, total: 1.34 ms
    Wall time: 701 µs





    333328333350000




```python
%time sum([x ** 2 for x in l])
```

    CPU times: user 36.1 ms, sys: 0 ns, total: 36.1 ms
    Wall time: 35.5 ms





    333328333350000



![green-divider](https://user-images.githubusercontent.com/7065401/52071924-c003ad80-2562-11e9-8297-1c6595f8a7ff.png)

## Useful Numpy functions

### `random` 


```python
np.random.random(size=2)
```


```python
np.random.normal(size=2)
```


```python
np.random.rand(2, 4)
```

---
### `arange`


```python
np.arange(10)
```


```python
np.arange(5, 10)
```


```python
np.arange(0, 1, .1)
```

---
### `reshape`


```python
np.arange(10).reshape(2, 5)
```


```python
np.arange(10).reshape(5, 2)
```

---
### `linspace`


```python
np.linspace(0, 1, 5)
```


```python
np.linspace(0, 1, 20)
```


```python
np.linspace(0, 1, 20, False)
```

---
### `zeros`, `ones`, `empty`


```python
np.zeros(5)
```


```python
np.zeros((3, 3))
```


```python
np.zeros((3, 3), dtype=np.int)
```


```python
np.ones(5)
```


```python
np.ones((3, 3))
```


```python
np.empty(5)
```


```python
np.empty((2, 2))
```

---
### `identity` and `eye`


```python
np.identity(3)
```


```python
np.eye(3, 3)
```


```python
np.eye(8, 4)
```


```python
np.eye(8, 4, k=1)
```


```python
np.eye(8, 4, k=-3)
```


```python
"Hello World"[6]
```

![purple-divider](https://user-images.githubusercontent.com/7065401/52071927-c1cd7100-2562-11e9-908a-dde91ba14e59.png)
