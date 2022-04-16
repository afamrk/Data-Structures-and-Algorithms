# Linear Search

```python
def search(arr, value):

    for i in range(len(arr)):
        if arr[i] == value:
            return i

    return -1
```

# Binary Search
```python
def search(arr, value):

    low = 0
    high = len(arr) -1

    while low <= high:

        mid = (low+high)//2

        if arr[mid] == value:
            return mid
        elif arr[mid] > value:
            high = mid - 1
        elif arr[mid] < value:
            low = mid + 1
    return -1
```

# Binary Search (**using recursion**)
```python
def bs(arr, value):
    return binary_search(arr, value, 0, len(arr)-1)

def binary_search(arr, value, l, r):

    mid = (l+r)//2
    if arr[mid] == value:
        return True
    if l >= r:
        return False
    elif arr[mid] < value:
        return binary_search(arr, value,mid+1, r)
    else:
        return binary_search(arr, value, l, mid)
```