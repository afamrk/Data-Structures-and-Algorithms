# BFS

### Javascript
```javascript 
function bfs(current_node){
  visited = [];
  queue = [current_node];
  while(queue.length > 0){
    current_node = queue.shift();
    if(current_node.left){
      queue.push(current_node.left)
    }
    if(current_node.right){
      queue.push(current_node.right)
    }
    if(!visited.includes(current_node.value)){
      visited.push(current_node.value)
    }
  }
  return visited

}
```
#### Using Recursion
```javascript
function bfs_recursive(queue = [], list =[]){
  if(queue.length < 1){
    return list
  }
  current_node = queue.shift()
  if(!list.includes(current_node.value)){
    list.push(current_node.value);
  }
  if(current_node.left){
    queue.push(current_node.left);
  }
  if(current_node.right){
    queue.push(current_node.right);
  }
  return bfs_recursive(queue, list)
}
bfs_recursive([node])
```

### Python
```python
from collections import deque
def bfs(node):
    result = {}
    queue = deque()
    queue.append(node)
    while(queue):
        node = queue.popleft()
        if node.value not in result:
            result[node.value] = None
        if node.leftChild:
            queue.append(node.leftChild)
        if node.rightChild:
            queue.append(node.rightChild)

    return result.keys()

```
