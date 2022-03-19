# Doubly Linked list

## Javascript
```javascript
//node class
class Node {
  constructor(data, next=null, prev=null) {
    this.data = data;
    this.next = next;
    this.prev = prev; 
  }
}

//linkedlist class
class LinkedList {
  constructor(){
    this.head = null;
    this.tail = null;
    this.length = 0;
  }

  toString(){
    return this.array().join(' => ')
  }

  array() {
    const list = new Array(this.length);
    let front = this.head;
    let f_index = 0;
    let back = this.tail;
    let b_index = this.length-1;
    while(front || back ){
      if(front === back){
        list[f_index] = front.data;
        break;
      }else if (front.next === back){
        list[f_index] = front.data;
        list[b_index] = back.data;
        break;
      }
      else{
        list[f_index] = front.data;
        list[b_index] = back.data;
        front = front.next;
        back = back.prev;
        f_index += 1;
        b_index -= 1;
      }
    }
    return list
  }

  has(value){
    let front = this.head;
    let back = this.tail;
    while(front || back ){
      if (front.data === value || back.data === value){
        return true
      }
      if(front === back){
        break;
      }else if (front.next === back){
        break;
      }
    }
    return false
  }
//adding value at the end
  append(value){
    //checking linked list is empty or not
    const node = new Node(value);
    if(!this.head){
      this.head = this.tail = node;
      this.length = 1;
    } else {
      node.prev = this.tail;
      this.tail.next = node;
      this.tail = node;
      this.length++;
    }
    return this
  }
//return node at a specific index
  get_node(index){
    let node = '';
    let dist = this.length - (index + 1); 
    if(index > dist) {
      node = this.tail;
      for(let i=0; i < dist;i++){
        node = node.prev;
      }
    } 
    else {
      node = this.head;
      for(let i=0; i < index; i++){
        node = node.next;
        }
    }
    return node;
  }
//inserting node at a specified index
  insert(value, index=0){
    if(index < 0 || !Number.isInteger(index))
    {
      throw new Error(`Please enter a valid index`)
    }
    //index is greater than size or linked_list is empty
    else if(index >= this.length || !this.head)
    {
      this.append(value);
    } 
    //inserting at the front
    else if(!(index))
    {
      const node = new Node(value);
      node.next = this.head;
      this.head.prev = node;
      this.head = node;
      this.length++;
    } 
    else 
    {
      const inode = this.get_node(index-1);
      const node = new Node(value);
      node.prev = inode;
      inode.next.prev = node;
      node.next = inode.next;
      inode.next = node;
      this.length++;
    }
  return this;
  }

  remove(index){
    if(index < 0 || !Number.isInteger(index) || index > this.length)
    {
      throw new Error(`Please enter a valid index`)
    }
    else if(index === 0){
      this.head = this.head.next;
      this.head.prev = null;
      this.length--;
    }else{
      const inode = this.get_node(index-1);
      //if it is last node then change the tail
      if(index == this.length-1){
        this.tail = inode;
      } else {
        inode.next.next.prev = inode;
      }
      inode.next = inode.next.next;
      this.length--;
    }
    return this
  }
}
debugger;
linked_list = new LinkedList();
debugger;
linked_list.append(4);
debugger;
console.log(`adding value 4\n ${''+linked_list}`)
linked_list.append(5);
console.log(`adding value 5\n ${''+linked_list}`)
linked_list.append(7);
console.log(`adding value 7\n ${''+linked_list}`)
linked_list.insert(1);
console.log(`inserting value 1\n ${''+linked_list}`)
linked_list.insert(2,1);
console.log(`inserting value 2 at position 1\n ${''+linked_list}`)
linked_list.insert(3,2);
console.log(`inserting value 3 at position 2\n ${''+linked_list}`)
linked_list.insert(6,5)
console.log(`inserting value 6 at position 5\n ${''+linked_list}`)
linked_list.append(8)
console.log(`adding value 8\n ${''+linked_list}`)
linked_list.remove(7)
console.log(`remove value at position 7\n ${''+linked_list}`)
linked_list.remove(0)
console.log(`remove value at position 0\n ${''+linked_list}`)
linked_list.remove(4)
console.log(`remove value at position 4\n ${''+linked_list}`)
console.log(`linkedlist.has(2) => ${linked_list.has(2)}`)

```

## Python

```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        self.prev = None

class DLL:
    def __init__(self, value):
        self.head = self.tail = Node(value)
        self.size = 1
        
    def __iter__(self):
        node = self.head
        while node is not None:
            yield node
            node = node.next
            
    def insert(self, value, index=None):
        if index is not None and index > self.size+1:
            raise IndexError('please use currect index')
        elif self.head == None:
            self.__init__(value)
            return
        else:
            node = Node(value)
            if index == 0:
                node.next = self.head
                self.head.prev = node
                self.head = node
            elif index == None or index == self.size:
                node.prev = self.tail
                self.tail.next = node
                self.tail = node
            else:
                current =self.head
                i = 1
                while i < index:
                    current = current.next
                    i += 1
                print(current.value)
                node.prev = current
                node.next = current.next
                current.next.prev = node
                current.next = node
        self.size += 1
    
    def search(self, value):
        current = self.head
        while current:
            if current.value == value:
                return current
            current = current.next
        return False
    
    def delete(self,index=None):
        if (index is not None and index > self.size) or not self.head:
            raise IndexError('Cant do the operation')
        elif index == 0:
            if self.head == self.tail:
                self.head = None
                self.tail = None
            else:
                self.head = self.head.next
                self.head.prev = None
        elif index is None or index == self.size-1:
            if self.head == self.tail:
                self.head = None
                self.tail = None
            else:
                self.tail = self.tail.prev
                self.tail.next = None
        else:
            current = self.head
            i = 1
            while i <= index:
                current = current.next
                i += 1
            current.prev.next = current.next
            current.next.prev = current.prev
        self.size -= 1 
    def clear(self):
        current = self.head
        while current != None:
            current.prev = None
            current = current.next
        self.head = None
        self.tail = None

```