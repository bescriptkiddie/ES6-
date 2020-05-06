这里需要区分一下，Set 是 ES6 新增的数据结构，并不是数据类型。Set 的数据结构是以数组的形式构建的。

## Set 的声明

```
let setArr = new Set(["hello", "world", "!!!", "hello"]);
console.log(setArr);
```

Set 和 Array 的区别是 Set 不允许内部有重复的值，如果有只显示一个，相当于去重。需要注意，虽然 Set 很像数组，但是他不是数组，`typeof Set`的值是`function`

## Set 值的增删查

**_追加 add_**

在使用 Array 的时候，可以用 push 进行追加值，那 Set 稍有不同，它用更语义化的 add 进行追加。

```
setArr.add('web');
console.log(setArr);
```

**_删除 delete_**

跟数组的删除类似

```
setArr.delete('web');
console.log(setArr);
```

**_查找 has_**

用 has 进行值的查找，返回的是 true 或者 false。

```
console.log(setArr.has('hello'));//true
```

**_删除 clear_**

```
setArr.clear();
console.log(setArr);//{}
```

## set 的循环

**_for…of…循环_**

```
let setArr = new Set(["hello", "world", "!!!", "hello"]);
for (let item of setArr){
    console.log(item);
}
console.log(setArr.size);//3
```

这里还要说一下 size 属性，size 可以获得 Set 的数量。
**_forEach 循环_**

```
let setArr = new Set(["hello", "world", "!!!", "hello"]);
setArr.forEach((value)=>console.log(value));
```

使用箭头函数跟 foreach 搭配，可以完成很多功能。

## WeakSet 的声明 --->对象的 Set 方法

```
let weakObj=new WeakSet();
let obj={a:'hello',b:'world'}
weakObj.add(obj);
console.log(weakObj);
```

这里需要注意的是，如果你直接在 new 的时候就放入值，将报错。
WeakSet 里边的值也是不允许重复的，可是存在一些小坑，值得我们去注意！直接看代码：

```
let weakObj=new WeakSet();
let obj={a:'hello',b:'world'}
//let obj1=obj;
weakObj.add(obj);
weakObj.add(obj1);

console.log(weakObj);
```

<html>
<div align="center"> 
<img style ='width:300px' src ='http://note.youdao.com/yws/res/4339/FFDCE2C88E06465EA9F2890C427FFEA8'/>
</div>
</html>
从控制台我们可以看到，这里是把我们两个相同的数组都添加进去了，因为对象是引用类型，所以我们知识添加了指针的指向，所以他在浏览器看来是不同的，要想实现不重复输出，我们需要把，`boj = obj1`在把obj添加进去。

**_总结_**

在实际开发中 Set 用的比较多，WeakSet 用的并不多，但是他对传入值必须是对象作了很好的判断，我们灵活应用还是有一定的用处的。
