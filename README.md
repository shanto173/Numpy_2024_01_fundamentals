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
