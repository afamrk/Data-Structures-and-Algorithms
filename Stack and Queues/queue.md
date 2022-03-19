# Queue

## javascript

```javascript
class Node{
  constructor(value, next=null){
    this.value = value;
    this.next = next;
  }
}

class Queue{
  constructor(){
    this.first = null;
    this.last = null;
    this.length = 0;
  }

  enqueue(value){
    if(!value){
      return null;
    }
    const node = new Node(value);
    //no element in stack
    if(!this.first){
      this.first = this.last = node;
    } else {
      this.last.next = node;
      this.last = node;
    }
    this.length++;
    return this
  }

  dequeue(){
    if(!this.first){
      return null
    }
    const node = this.first;
    //only one element in stack
    if(!this.first.next){
      this.first = this.last = null;
    } else {
      this.first = this.first.next;
    }
    this.length--;
    return node
  }

  peek(){
    return this.first;
  }
}

```