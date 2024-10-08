
# Index

- [NumPy Examples](#numpy-examples)
- [What is NumPy?](#what-is-numpy)
- [Creating NumPy Arrays](#creating-numpy-arrays)
- [Array Creation with `dtype`, `arange`, `ones`, `zeros`](#array-creation-with-dtype-arange-ones-zeros)
- [Random Numbers, Linspace, and Identity Matrix](#random-numbers-linspace-and-identity-matrix)
- [Array Attributes: `ndim`, `shape`, `size`, `dtype`](#array-attributes-ndim-shape-size-dtype)
- [NumPy Array Operations](#numpy-array-operations)
- [Array Functions: `np.round`, `np.prod`, `np.var`, `np.sin`, `np.dot`](#array-functions-npround-npprod-npvar-npsin-npdot)
- [Indexing and Slicing](#indexing-and-slicing)
- [Iterating and Reshaping](#iterating-and-reshaping)
- [Stacking and Splitting](#stacking-and-splitting)


# NumPy Examples

This repository contains examples of using the NumPy library for numerical computing in Python. NumPy provides support for large, multi-dimensional arrays and matrices, along with a collection of mathematical functions to operate on these arrays.

## What is NumPy?

NumPy is the fundamental package for scientific computing with Python. It includes:

- A powerful N-dimensional array object (`ndarray`)
- Functions for element-wise computations
- Tools for working with arrays, including I/O, sorting, and reshaping
- Mathematical operations such as discrete Fourier transforms, random simulations, and linear algebra

## NumPy Arrays vs. Python Sequences

Key differences between NumPy arrays and Python sequences:
- **Fixed Size**: NumPy arrays have a fixed size, unlike Python lists, which can grow dynamically.
- **Data Type**: NumPy arrays contain elements of the same type, stored in a continuous block of memory, making them more memory-efficient.
- **Efficiency**: Operations on NumPy arrays are executed more efficiently and with less code than equivalent operations on Python sequences.

---

## Creating NumPy Arrays

```python
import numpy as np

# 1D array
a = np.array([1, 2, 3])
print(a)  # Output: [1 2 3]

# 2D array
b = np.array([[1, 2, 3], [4, 5, 6]])
print(b)  # Output: [[1 2 3], [4 5 6]]

# 3D array
c = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
print(c)  # Output: [[[1 2] [3 4]] [[5 6] [7 8]]]
```

## Array Creation with `dtype`, `arange`, `ones`, `zeros`

```python
# Create arrays with specific data types and shapes
np.array([1, 2, 3], dtype=float)  
# Output: array([1., 2., 3.])

# Create arrays using np.arange
np.arange(1, 11, 2)  
# Output: array([1, 3, 5, 7, 9])

# Reshaping arrays
np.arange(16).reshape(2, 2, 2, 2)  
# Output: array([[[[ 0,  1],
                   [ 2,  3]],

                   [[ 4,  5],
                   [ 6,  7]]],

                  [[[ 8,  9],
                    [10, 11]],

                  [[12, 13],
                   [14, 15]]]])

# Ones and zeros arrays
np.ones((3, 4))  
# Output: array([[1., 1., 1., 1.], [1., 1., 1., 1.], [1., 1., 1., 1.]])

np.zeros((3, 4))  
# Output: array([[0., 0., 0., 0.], [0., 0., 0., 0.], [0., 0., 0., 0.]])
```


## `Random Numbers`, `Linspace` and `identity` Matrix

```python
# Random array
np.random.random((3, 4))  
# Output: Random values, e.g., array([[0.857, 0.312, 0.088, 0.352],
                                      [0.968, 0.446, 0.563, 0.530],
                                      [0.032, 0.285, 0.095, 0.879]])
                                      

# Linearly spaced array (Equal distance array)
np.linspace(-10, 10, 10, dtype=int)  
# Output: array([-10,  -8,  -6,  -4,  -2,   1,   3,   5,   7,  10])

# Identity matrix
np.identity(3)  
# Output: array([[1., 0., 0.],
                 [0., 1., 0.],
                 [0., 0., 1.]])
```

## Array Attributes `ndim`, `shape`, `size`, `dtype`
```python
a3 = np.arange(8).reshape(2, 2, 2)

# Number of dimensions
print(a3.ndim)  
# Output: 3

# Shape of the array
print(a3.shape)  
# Output: (2, 2, 2)

# Size of the array
print(a3.size)  
# Output: 8

# Data type
print(a3.dtype)  
# Output: int64
```

## Numpy Array Operations

```python
a1 = np.arange(12).reshape(3, 4)
a2 = np.arange(12, 24).reshape(3, 4)

# Scalar operations: Arithmetic and relational
a1 ** 2  
# Output: array([[  0,   1,   4,   9], [ 16,  25,  36,  49], [ 64,  81, 100, 121]])

# Relational operations
a2 == 15  
# Output: array([[False, False, False,  True], [False, False, False, False], [False, False, False, False]])

# Vector operations: Arithmetic
a1 ** a2  
# Output: array([[                   0,                    1,                16384, 14348907], [4294967296, 762939453125, 101559956668416, 11398895185373143], [ 1152921504606846976, -1261475310744950487,  1864712049423024128,  6839173302027254275]])


```

## Array Functions `np.round`, `np.prod`, `np.var`, `np.sin`, `np.dot`

```python

# Array functions for mathematical computations
a1 = np.random.random((3, 3)) * 100
a1 = np.round(a1)

# Max/Min/Sum/Product
np.prod(a1, axis=0)  
# Output: Product along axis 0, e.g., array([35991., 46872., 17892.])

# Mean, median, standard deviation, variance
# axis = 0 referes to column : axis = 1 referes to Row
np.var(a1, axis=1)  
# Output: Variance along axis 1, e.g., array([317.56, 854., 96.22])

# Trigonometric functions
np.sin(a1)  
# Output: array of sine values for each element

# Dot product
a2 = np.arange(12).reshape(3, 4)
a3 = np.arange(12, 24).reshape(4, 3)
np.dot(a2, a3)  
# Output: array([[114, 120, 126],
                 [378, 400, 422],
                 [642, 680, 718]])

```

## Indexing and Slicing

```python

a1 = np.arange(10)
a2 = np.arange(12).reshape(3, 4)

# Slicing
a1[2:5:2]  
# Output: array([2, 4])

# Slicing with steps
a2[0:2, 1::2]  
# Output: array([[1, 3], [5, 7]])

# Accessing elements in multi-dimensional arrays
a2[1:, 1:3]  
# Output: array([[5, 6], [9, 10]])


```

## Iterating (nditer,ravel,) and Reshaping 

```python

# Iterating over 1D and 2D arrays
for i in a1:
    print(i)  
# Output: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9

# Iterating over a 2D array
for i in a2:
    print(i)  
# Output: Rows of the 2D array

# Reshaping and transposing
np.transpose(a2)  
# Output: Transposed array, e.g., array([[0, 4, 8], [1, 5, 9], [2, 6, 10], [3, 7, 11]])

# Flattening (ravel) convert n dimension array to 1D array
a2.ravel()  
# Output: Flattened array, e.g., array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])

```


## Stacking and Splitting

```python
a4 = np.arange(12).reshape(3, 4)
a5 = np.arange(12, 24).reshape(3, 4)

# Horizontal stacking
np.hstack((a4, a5))  
# Output: Stacked array horizontally

# Vertical stacking
np.vstack((a4, a5))  
# Output: Stacked array vertically

# Splitting
np.hsplit(a4, 2)  
# Output: Splits array into two, e.g., [array([[ 0,  1], [ 4,  5], [ 8,  9]]), array([[ 2,  3], [ 6,  7], [10, 11]])]

```
### `Q-1` Create a null vector of size 10 but the fifth value which is 1.
```python
a = np.nan*np.empty(10)
a[4] = 1
a
result : array([nan, nan, nan, nan,  1., nan, nan, nan, nan, nan])

                      # OR

b = np.full(10,np.nan)
b[4]=1
b
Result: array([nan, nan, nan, nan,  1., nan, nan, nan, nan, nan])
```


### `Q-2` Ask the user to input two numbers a, and b. Write a program to generate a random array of shapes (a, b) and print the array and avg of the array.
```python

a = int(input('Enter a number'))
b = int(input('Enter a number'))

c = np.random.random((a,b))
print(c)
np.mean(c)

Result:
Enter a number 2 
Enter a number 3
[[0.46295527 0.93246053 0.51971643]
 [0.55760796 0.30813307 0.0548773 ]]
Avg is : 0.47262509258357205

                    # OR


## or another approach
#  Storing 2 integer
a,b = np.int32(input('Enter 2 value with space : ').split())

# making a 2D array of user given input shape
c = np.random.random((a,b))
print(c)
print('Avg is :',np.mean(c))

Result:

Enter 2 value with space :  2 3
[[0.93245822 0.27240621 0.99575976]
 [0.38927475 0.93636674 0.14778126]]
Avg is : 0.6123411580768572

                  # OR

## or another approach using `MAP`
#  Storing 2 integer
a,b = map(int,input('Enter 2 value with space : ').split())

# making a 2D array of user given input shape
c = np.random.random((a,b))
print(c)
print('Avg is :',np.mean(c))

Result:

Enter 2 value with space :  2 3 
[[0.65119993 0.1640673  0.10375826]
 [0.97082532 0.77452849 0.60682133]]
Avg is : 0.5452001065512276

```


### `Q-3`Write a function to create a 2d array with 1 on the border and 0 inside. Take 2-D array shape as (a,b) as parameter to function.

Eg.-
```
[[1,1,1,1],
[1,0,0,1],
[1,0,0,1],
[1,1,1,1]]
```

```python

def fun(a,b):
    c = np.ones((a,b))  
    c[1:(a-1),1:(b-1)] = 0
    return c

a,b = np.int32(input("Enter a number:").split())
fun(a,b)

result

Enter a number: 4 5
array([[1., 1., 1., 1., 1.],
       [1., 0., 0., 0., 1.],
       [1., 0., 0., 0., 1.],
       [1., 1., 1., 1., 1.]])

```

### `Q-4` Create a vector of size 10 with values ranging from 0 to 1, both excluded `np.linespace`.

```python
np.linspace(0,1,12)[1:-1]

resultL
array([0.09090909, 0.18181818, 0.27272727, 0.36363636, 0.45454545,
       0.54545455, 0.63636364, 0.72727273, 0.81818182, 0.90909091])
```

### `Q-5` Can you create a identity mattrix of shape (3,4). If yes write code for it `np.identity` and `np.eye`.

```python
# no, i can't create a identity matrix of shape (3,4)

np.identity(3)

result:
array([[1., 0., 0.],
       [0., 1., 0.],
       [0., 0., 1.]])


#          OR

np.eye(4)

result:
array([[1., 0., 0., 0.],
       [0., 1., 0., 0.],
       [0., 0., 1., 0.],
       [0., 0., 0., 1.]])

```


### `Q-6:` Create a 5x5 matrix with row values ranging from 0 to 4.

```python

a = np.zeros((5,5))

a[:,:] = np.arange(0,5)
a

result:
array([[0., 1., 2., 3., 4.],
       [0., 1., 2., 3., 4.],
       [0., 1., 2., 3., 4.],
       [0., 1., 2., 3., 4.],
       [0., 1., 2., 3., 4.]])

```

### `Q-7:`  Consider a random integer (in range 1 to 100) vector with shape `(10,2)` representing coordinates, and coordinates of a point as array is given. Create an array of distance of each point in the random vectros from the given point. Distance array should be interger type.

```
point = np.array([2,3])
```

```python

a = np.random.randint(1,100,20).reshape(10,2)
b = np.array([2,3])
print(a)

np.sqrt(np.sum((a-b)**2,axis=1)).astype(int)

result:

[[ 7 52]
 [76 69]
 [15 76]
 [65 42]
 [72 97]
 [22 94]
 [95 10]
 [82  2]
 [97 72]
 [11 10]]
array([ 49,  99,  74,  74, 117,  93,  93,  80, 117,  11])

```


### `Q-8:` Consider a (6,7,8) shape array, what is the index (x,y,z) of the 100th element `np.unravel_index(array element index,array shape) : np.unravel_index(100,a.shape)`?

```python

a = np.arange(6*7*8).reshape(6,7,8)
print(a)
np.unravel_index(100,a.shape)

result :
(1, 5, 4)
```
### `Q-9:` Arrays, You are given a space-separated list of numbers. Your task is to print a reversed NumPy array with the element type float.

```python
a = input('enter number').strip().split()
print(a) 
a = np.array(a[::-1],dtype=float)
a


result:

enter number 1 2 3 4 -8 -10
['1', '2', '3', '4', '-8', '-10']
array([-10.,  -8.,   4.,   3.,   2.,   1.])

```

### `Q-11:` Softmax function Create a Python function to calculate the Softmax of the given numpy 1D array. The function only accepts the numpy 1D array, otherwise raise error. 

```sql
x = np.array([33.17344305, 45.61961654, 82.05405781, 80.9647098,  68.82830233, 91.52064278])
y = (np.exp(x))/np.sum(np.exp(x))
print(y)
import matplotlib.pyplot as plt
plt.plot(x,y)

```

![softmax plot](https://github.com/shanto173/Numpy_2024_01_fundamentals/blob/main/images/1.png)


### `Q-12:` Vertical stack
Write a python function that accepts infinite number of numpy arrays and do the vertical stack to them. Then return that new array as result. The function only accepts the numpy array, otherwise raise error.
**Example 1:**

Input:
```bash
a= [[0 1 2 3 4]
 [5 6 7 8 9]]

b= [[1 1 1 1 1]
 [1 1 1 1 1]]
```

Output:

```bash
[[0 1 2 3 4]
 [5 6 7 8 9]
 [1 1 1 1 1]
 [1 1 1 1 1]]
```

**Example 2:**

Input:
```bash
a= [[0 1 2 3 4]
 [5 6 7 8 9]]

b= [[1 1 1 1 1]
 [1 1 1 1 1]]

c= [[0.10117373 0.1677244  0.73764059 0.83166097 0.48985695]
 [0.44581567 0.13502419 0.55692335 0.16479622 0.61193593]]
```

Output:
```bash
[[0.         1.         2.         3.         4.        ]
 [5.         6.         7.         8.         9.        ]
 [1.         1.         1.         1.         1.        ]
 [1.         1.         1.         1.         1.        ]
 [0.10117373 0.1677244  0.73764059 0.83166097 0.48985695]
 [0.44581567 0.13502419 0.55692335 0.16479622 0.61193593]]
```

```python
def numpya(*args):
    for i in args:
        if type(i) != np.ndarray:
            raise TypeError('Requeired numpy array')
    return np.vstack(args)

a = np.arange(1,6).reshape(1,5)
print(a)
b = np.arange(6,11).reshape(1,5)
print(b)
c = np.random.random(5).reshape(1,5)
print(c)
print(numpya(a,b,c))

Result:

a = [[1 2 3 4 5]]
b = [[ 6  7  8  9 10]]
c = [[0.32588096 0.31129063 0.67641655 0.89509923 0.06168605]]

[[ 1.          2.          3.          4.          5.        ]
 [ 6.          7.          8.          9.         10.        ]
 [ 0.32588096  0.31129063  0.67641655  0.89509923  0.06168605]]

```

### `Q-14:` Subtract the mean of each row from a matrix.

```python

a = np.arange(0,20).reshape(4,5)
print(a)
a-np.mean(a,axis=1).reshape(4,1)

result:
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]]
array([[-2., -1.,  0.,  1.,  2.],
       [-2., -1.,  0.,  1.,  2.],
       [-2., -1.,  0.,  1.,  2.],
       [-2., -1.,  0.,  1.,  2.]])

```

### `Q-16:` Replace odd elements in arrays with -1.

```python

a = np.arange(0,20).reshape(4,5)
a
array([[ 0,  1,  2,  3,  4],
       [ 5,  6,  7,  8,  9],
       [10, 11, 12, 13, 14],
       [15, 16, 17, 18, 19]])



np.where((np.arange(0,20).reshape(4,5) % 2 == 1)==True,-1,a)

array([[ 0, -1,  2, -1,  4],
       [-1,  6, -1,  8, -1],
       [10, -1, 12, -1, 14],
       [-1, 16, -1, 18, -1]])


```



### `Q-17:` Given two arrays of same shape make an array of max out of two arrays. (Numpy way)
```
a=np.array([6,3,1,5,8])
b=np.array([3,2,1,7,2])

Result-> [6 3 1 7 8]
```

```python
a=np.array([6,3,1,5,8])
b=np.array([3,2,1,7,2])

np.max((a,b),axis=0)

```
















