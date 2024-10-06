
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
















