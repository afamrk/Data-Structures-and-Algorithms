# Hash table with array

## Javascript
```javascript
class HashTable {
  constructor(length){
    this.length = length
    this.arr = new Array(this.length)
  }

  set(key, value){
    let hash_value = this._hash(key);
    if(!this.arr[hash_value]){
      this.arr[hash_value] = [];
    }
    this.arr[hash_value].push([key,value]);
  }

  get(key){
    const inner = this.arr[this._hash(key)];
    if(inner){
      for(let item of inner){
        if(item[0] === key){
          return item[1];
        }
      }
    }else{
      return undefined
    }
  }

  keys(){
    let keys = [];
    for(let item of this.arr){
      if(item){
        for(let inner_item of item){
          keys.push(inner_item[0]);
        }
      }
    }
    return keys
  }

  _hash(key){
    let hash_value = 0;
    for(let i=0; i<key.length; i++){
      hash_value = (hash_value + key.charCodeAt(i)*i) % this.length
    }
    return hash_value
  }
}


```