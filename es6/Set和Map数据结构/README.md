## Set和Map

![](/assets/2615789-677c9382b37392f5.webp)

####1、ES6中的Set

ES6中提供了Set数据容器，这是一个能够存储无重复值的有序列表。

#####创建Set

通过new Set()可以创建Set，然后通过add方法能够向Set中添加数据项：
```javascript
//Set
let set= new Set();
set.add(1);
set.add('1');
console.log(set.size);//2       
```

Set内部使用Object.is()方法来判断两个数据项是否相等，唯一不同的是+0和-0在Set中被判断为是相等的。

同时可以使用数组来构造Set，或者说具有迭代器的对象都可以用来构造Set，并且Set构造器会确保不会存在重复的数据项：

```javascript
let set = new Set([1,2,3,3,3,3]);
console.log(set.size);//3
```

#####检查某个值是否存在于Set中

```javascript
let set = new Set([1,2,3,3,3,3]);
console.log(set.has(5)); //false
```

#####删除值

使用delete()方法从Set中删除某个值，或者使用clear()方法从Set中删除所有值：
```javascript
let set = new Set([1,2,3,3,3,3]);
console.log(set.size);//3
console.log(set.has(5)); //false

set.delete(1);

console.log(set.has(1)); //false
console.log(set.size); //2
```

#####forEach()方法

可以使用forEach方法来遍历Set中的数据项，该方法传入一个回调函数callback，还可以传入一个this，用于回调函数之中：

回调函数callback中有三个参数：

1、元素值；
2、元素索引；
3、将要遍历的对象；

```javascript
 let set = new Set([1,2,3,3,3,3]);
 set.forEach(function (value,key,ownerSet) {
     console.log(value);
     console.log(key);           
 })
 ```
 
Set中的value和key是相同的，这是为了让Set的forEach方法和数组以及Map的forEach方法保持一致，都具有三个参数。

在forEach方法中传入this，给回调函数使用：

```javascript
let set = new Set([1,2,3,3,3,3]);
let operation ={

    print(value){
        console.log(value);
    },

    iterate(set=[]){
        set.forEach(function(value,key,ownerSet){
            this.print(value);
            this.print(key);
        },this);
    }

}

operation.iterate(set);

输出：1 1 2 2 3 3
```
如果回调函数使用箭头函数的话，就可以省略this的入参，这是因为箭头函数会通过作用域链找到当前this对象，将上面的示例代码使用箭头函数来写：
```javascript
let set = new Set([1,2,3,3,3,3]);
let operation ={

    print(value){
        console.log(value);
    },

    iterate(set=[]){
        set.forEach((value,key)=>{
            this.print(value);
            this.print(key);
        })
    }

}

operation.iterate(set);
```

#####将Set转换成数组
将数组转换成Set十分容易，可以将数组传入Set构造器即可；而将Set转换成数组，需要使用扩展运算符。扩展运算符能将数组中的数据项切分开，作为独立项传入到函数，如果将扩展运算符用于可迭代对象的话，就可以将可迭代对象转换成数组：

```javascript
let [...arr]=set;
console.log(arr); // [1,2,3]
```

#####Weak Set
Set在存放对象时，实际上是存放的是对象的引用，即Set也被称之为Strong Set。如果所存储的对象被置为null，但是Set实例仍然存在的话，对象依然无法被垃圾回收器回收，从而无法释放内存：
```javascript

```