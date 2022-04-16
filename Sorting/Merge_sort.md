# Merge Sort


```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        lefthalf = arr[:mid]
        righthalf = arr[mid:]

        merge_sort(lefthalf)
        merge_sort(righthalf)

        i = 0
        j = 0
        k = 0
        while i < len(lefthalf) and j < len(righthalf):
            if lefthalf[i] < righthalf[j]:
                arr[k] = lefthalf[i]
                i = i + 1
            else:
                arr[k] = righthalf[j]
                j = j + 1
            k = k + 1

        while i < len(lefthalf):
            arr[k] = lefthalf[i]
            i = i + 1
            k = k + 1

        while j < len(righthalf):
            arr[k] = righthalf[j]
            j = j + 1
            k = k + 1
    return arr
```


```python
def merge_sort(arr):
    if len(arr) <=1:
        return arr
    mid = len(arr)//2
    left_side = merge_sort(arr[:mid])
    right_side = merge_sort(arr[mid:])

    left_index = 0
    right_index = 0
    index = 0
    while left_index!=len(left_side) or  right_index!=len(right_side):
        if right_index==len(right_side) or left_index!=len(left_side) and left_side[left_index] < right_side[right_index]:
            arr[index] = left_side[left_index]
            left_index += 1
        else:
            arr[index] = right_side[right_index]
            right_index += 1
        index += 1
    return arr
```

