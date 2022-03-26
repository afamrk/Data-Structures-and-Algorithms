# Min Heap

### Python
```python
class MinHeap:
    def __init__(self):
        self.heap_list = [0]
        self.current_size = 0

    def insert(self, value):
        self.heap_list.append(value)
        self.current_size += 1
        self.heapify_up(self.current_size)
        print(self.heap_list)
        
    def delete(self):
        if self.current_size == 0:
            raise IndexError('empty heap')
            
        current_min = self.heap_list[1]
        self.heap_list[1] = self.heap_list[self.current_size]
        self.heap_list.pop()
        self.current_size -= 1
        self.heapify_down(1)
        return current_min

    def heapify_up(self, position):
        pos = position
        parent = pos // 2
        while(parent):
            if self.heap_list[pos] < self.heap_list[parent]:
                temp = self.heap_list[pos]
                self.heap_list[pos] = self.heap_list[parent]
                self.heap_list[parent] = temp
                pos = parent
                parent = pos // 2
            else:
                break
                
    def min_child(self, i):
        if i * 2 + 1 > self.current_size:
            return i*2
        else:
            if self.heap_list[i*2] < self.heap_list[i*2+1]:
                return i*2
            else:
                return i*2+1
    
    def heapify_down(self, i):
        while( i*2 <= self.current_size ):
            min_child = self.min_child(i)
            if self.heap_list[min_child] < self.heap_list[i]:
                temp = self.heap_list[min_child]
                self.heap_list[min_child] = self.heap_list[i]
                self.heap_list[i] = temp
                i = min_child
            else:
                break
```

### Read
https://www.youtube.com/watch?v=g9YK6sftDi0
