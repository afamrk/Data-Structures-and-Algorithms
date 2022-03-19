# Stack

## Javascript
### Stack using Linked List
```javascript
class Node{
  constructor(value, next=null){
    this.value = value;
    this.next = next;
  }
}

class Stack{
  constructor(){
    this.bottom = null;
    this.top = null;
    this.length = 0;
  }

  push(value){
    const node = new Node(value);
    //no element in stack
    if(!this.bottom){
      this.bottom = this.top = node;
    } else {
      node.next = this.top;
      this.top = node;
    }
    this.length++;
    return this
  }

  pop(){
    if(!this.top){
      return null
    }
    const node = this.top;
    //only one element in stack
    if(!this.top.next){
      this.bottom = this.top = null;
    } else {
      this.top = this.top.next;
    }
    this.length--;
    return node
  }

  peek(){
    return this.top
  }
}

```
### Stack using Array
```javascript
class Stack{
  constructor(){
    this.arr = [];
  }

  push(value){
    this.arr.push(value);
    return this
  }

  pop(){
    if(!this.arr.length){
      return null
    } else {
      return this.arr.pop()
    }
  }

  peek(){
    if(!this.arr.length){
      return null
    } else {
      return this.arr[arr.length-1]
    }
  }
}

```