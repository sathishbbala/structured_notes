## Numerical Python (numpy)

NumPy is a python library used for working with arrays. NumPy is faster than using Python Lists for working with arrays. 

NumPy arrays are stored at one continuous place in memory unlike lists, so processes can access and manipulate them very efficiently. This is called locality of reference. 

The array object in NumPy is called ndarray.

``` python
import numpy as np

arr = np.array(42) #0d array
print(arr)
print(arr.ndim) # print the array dimension in this case it is 0

arr = np.array([1,2,3,4,5]) #1d array
print(arr)
print(type(arr))
print(arr.ndim) # prints 1 


arr = np.array([[1,2,3],[4,5,6]]) # 2d array think of a spreadsheet or table and columns 2 rows 3 columns 
print(arr)
print(type(arr))
print(arr.ndim) # prints 2


arr = np.array([[[1,2,3],[4,5,6]],[[1,2,3],[7,8,9]]]) #3d array stack of table or spreadsheet 
print(arr)
print(type(arr))
print(arr.ndim) # prints 3

arr = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])
print(arr[0, 1, 2]) # prints 6 first number refers to dimension 1 and second to dimension 2 and 3rd to dimension 3
print(arr[1,0,0) # prints 7
```


