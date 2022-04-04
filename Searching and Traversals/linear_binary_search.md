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
def rec_search(arr, value):

    if not arr:
        return -1

    mid = len(arr)-1//2

    if arr[mid] == value:
        return mid

    if arr[mid] > value:
        rec_search(arr[0:mid],value)
    else:
        rec_search(arr[mid+1:],value)
```