##forEach、for-in与for-of的区别

#####forEach介绍

```javascript
objArr.forEach(function (value) {
  console.log(value);
});
```
foreach 方法没办法使用 break 语句跳出循环，或者使用return从函数体内返回

#####for-in介绍

```javascript
for(var index in objArr){
    console.log(objArr[index])
}
```
以上代码会出现的问题：
1.index 值 会是字符串（String）类型
2.循环不仅会遍历数组元素，还会遍历任意其他自定义添加的属性，如，objArr上面包含自定义属性，objArr.name，那这次循环中也会出现此name属性
3.某些情况下，上述代码会以随机顺序循环数组

#####for-of介绍