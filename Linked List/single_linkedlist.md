# Single Linked list

### javscript
```javascript
//node class
class Node {
  constructor(data, next=null) {
    this.data = data;
    this.next = next;
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
    const list = [];
    let current_node = this.head;
    while(current_node != null){
      list.push(current_node.data);
      current_node = current_node.next;
    }
    return list
  }

  has(value){
    let current_node = this.head;
    while(current_node != null){
      if(current_node.data === value){
        return true
      }
      current_node = current_node.next;
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
      this.tail.next = node;
      this.tail = node;
      this.length++;
    }
    return this
  }
//return node at a specific index
  get_node(index){
    let node = this.head;
    for(let i=0; i < index; i++){
      node = node.next;
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
      this.head = node;
      this.length++;
    } 
    else 
    {
      const inode = this.get_node(index-1);
      const node = new Node(value);
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
      this.length--;
    }else{
      const inode = this.get_node(index-1);
      inode.next = inode.next.next;
      //if it is last node then change the tail
      if(index == this.length-1){
        this.tail = inode;
      }
      this.length--;
    }
    return this
  }
}

linked_list = new LinkedList();
linked_list.append(4);
console.log(`adding value 4\n ${''+linked_list}`)
linked_list.append(5);
console.log(`adding value 4\n ${''+linked_list}`)
linked_list.append(7);
console.log(`adding value 4\n ${''+linked_list}`)
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
linked_list.remove(5)
console.log(`remove value at position 5\n ${''+linked_list}`)
console.log(`linkedlist.has(2) => ${linked_list.has(2)}`)


```

### Python
```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None

class SingleLinkedList:
    def __init__(self, value):
        self.head = self.tail = Node(value)
        self.size = 1
    def __iter__(self):
        node = self.head
        while node is not None:
            yield node
            node = node.next
    def insert(self, value, position=None):
        node = Node(value)
        if self.head == None:
            self.head = node
            self.tail = node
        elif position == None or position == self.size+1:
            self.tail.next = node
            self.tail = node
        else:
            if position > self.size:
                raise IndexError(f'value is greater than total size{self.size}')
            else:
                if position == 0:
                    node.next = self.head
                    self.head = node
                else:
                    tempnode = self.head
                    for i in range(position-1):
                        tempnode = tempnode.next
                    node.next = tempnode.next
                    tempnode.next = node
        self.size += 1
    
    def __setitem__(self,index,value):
        self.insert(value,index)
    
    def __getitem__(self,index):
        if index >= self.size:
            raise IndexError("entered value is greater than size of linkedlist")
        current = self.head
        for i in range(index):
            current = current.next
        return current
    
    def search(self,value):
        if self.head == None:
            raise IndexError('empty linkedlist')
        current = self.head
        for i in range(self.size):
            if current.value == value:
                return i
            current = current.next
        return False
    
    def __contains__(self, value):
        return bool(self.search(value))
    
    def delete(self, index):
        if self.head == None or index >= self.size:
            raise IndexError("can't do the operation")
        elif index == 0:
            if self.head == self.tail:
                self.head = None
                self.tail = None
            else:
                self.head = self.head.next
        elif index == self.size-1:
            if self.head == self.tail:
                self.head = None
                self.tail = None
            else:
                previous_node = self.__getitem__(index-1)
                print(previous_node.value)
                previous_node.next = None
                self.tail = previous_node
        else:
            previous_node = self.__getitem__(index-1)
            previous_node.next = previous_node.next.next
    
        self.size -= 1
    
    def clear(self):
        #when we make head null,the reference to first node is 0.so it garbage collected and second node reference become 0
        #becuz the first node is garbage collected, this will continue until the end
        self.head = None
        self.tail = None
        self.size = 0

```