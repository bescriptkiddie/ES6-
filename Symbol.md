## 声明 Symbol

Symbol，它的意思是全局标记。我们先声明一个 Symbol，然后我们在控制台输出一下。

```
var symbol = Symbol('jspang');
console.log(symbol);
console.log(symbol.toString());
```

这时候我们仔细看控制台是有区别的，没有 toString 的是红字，toString 的是黑字。
![image](http://note.youdao.com/yws/res/4244/A9FC90C8C47440519E679BE1A3559D43)

## Symbol 在对象中的应用

那我们该怎么使用 Symbol 构建对象的 Key，并调用和赋值呢？先贴代码：

```
var key = Symbol();
var obj={
    [key]:'hello'
}
console.log(obj[key]);//hello
obj[key]='world';
console.log(obj[key]);//world
```

首先我们得在对象外面声明一个 symbol 类型变量，然后在对象里面用[]将变量传入`[key]:'value'`,如果我们想在全局状态下改变 key 的值，利用`obj[key]`的形式去获取。

## Symbol 对象元素的保护作用

在对象中有很多值，但是循环输出时，并不希望全部输出，那我们就可以使用 Symbol 进行保护。

没有进行保护的写法：

```
var obj = { name: "pika", skill: "web", age: 18 };

for (let item in obj) {
  console.log(obj[item]);//pika web 18
}
```

现在我不想别人知道我的年龄，这时候我就可以使用 Symbol 来进行循环保护。

```
let obj = { name: "pika", skill: "web" };
let age = Symbol();
obj[age] = 18;
for (let item in obj) {
  console.log(obj[item]);//pika 18
}
console.log(obj);//{name:"pika",skill:"web,Symbol():18}
```

有结果可知，这样便可以很巧妙地保护属性，方便开发以及维护。
