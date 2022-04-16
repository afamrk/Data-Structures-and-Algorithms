# Bubble Sort
```python
def bubble_sort(arr):
    for i in range(len(arr)-1,0,-1):
        for j in range(i):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr
```

# Selection Sort
```python
def selection_sort(arr):
    for i in range(len(arr)-1,0,-1):
        current_max = 0
        for j in range(i):
            if arr[current_max] < arr[j+1]:
                current_max = j+1
        temp = arr[current_max]
        arr[current_max] = arr[j+1]
        arr[j+1] = temp
    return l
```

# Insertion Sort
```python
def insertion_sort(arr):
    for i in range(1,len(arr)):
        position = i
        temp = arr[i]
        while position > 0 and temp < arr[position-1]:
            arr[position] = arr[position-1]
            position -= 1
        arr[position] = temp
    return arr
```
### Only using for loop
```python
def insertion_sort(arr):
    for i in range(1,len(arr)):
        temp = arr[i]
        for j in range(i,0,-1):
            if temp < arr[j-1]:
                arr[j] = arr[j-1]
                if j == 1:
                    j = 0
                    break
            else:
                break
        arr[j] = temp
    return arr
```

# Shell Sort
```python
def shell_short(arr):
    size = len(arr)
    gap = size//2

    while gap>0:

        for i in range(gap,size):
            position = i
            temp = arr[i]
            while position>=gap and temp < arr[position-gap]:
                arr[position] = arr[position-gap]
                position -= gap
            arr[position] = temp
        gap = gap//2
    return arr
```
[Shell Sort video](https://www.youtube.com/watch?v=VxNr9Vudp4Y&t=15s "link")