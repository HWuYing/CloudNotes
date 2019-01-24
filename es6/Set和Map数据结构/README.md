## Set和Map

![](/assets/2615789-677c9382b37392f5.webp)

####1、ES6中的Set

ES6中提供了Set数据容器，这是一个能够存储无重复值的有序列表。

创建Set

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

检查某个值是否存在于Set中

```javascript
let set = new Set([1,2,3,3,3,3]);
console.log(set.has(5)); //false
```

删除值

使用delete()方法从Set中删除某个值，或者使用clear()方法从Set中删除所有值：
```javascript
let set = new Set([1,2,3,3,3,3]);
console.log(set.size);//3
console.log(set.has(5)); //false

set.delete(1);

console.log(set.has(1)); //false
console.log(set.size); //2
```