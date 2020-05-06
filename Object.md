## 对象赋值

ES6 允许把声明的变量直接赋值给对象，直接上代码。

```
let h="hello";
let w= 'world';
var obj= {h,w};
console.log(obj);  //{h: "hello", w: "world"}
```

解决了在 ES5 上那种臃肿的赋值形式`{h:h,w:w}`，这种显得代码更加简洁。

## 对象 Key 值构建

有时候我们会在后台取出 key 值，但可能不是我们前台定义好的，这时候我们就需要构建 key 值，可以通过`[]`的形式，进行对象的构建。

```
let key='skill';
var obj={
    [key]:'web'
}
console.log(obj.skill);//
```

## 自定义对象方法

对象方法就是把对象中的属性，用匿名函数的形式编程方法。这个方法在 ES5 就存在，这里复习一下。

```
var obj={
    add:function(a,b){
        return a+b;
    }
}
console.log(obj.add(1,2));  //3
```

## Object.is( ) 对象比较

对象的比较方法,以前进行对象值的比较，经常使用`===`来判断，现在 ES6 为我们提供了 is 方法进行对比。但是我们如何区分`===`和`Object.is()`方法的区别是什么，先看下面的代码结果。

```
console.log(+0 === -0);  //true
console.log(NaN === NaN ); //false
console.log(Object.is(+0,-0)); //false
console.log(Object.is(NaN,NaN)); //true
```

`===`为同值相等，`Object.is()`为严格相等。

## Object.assign( )合并对象

操作数组时我们经常使用数组合并，那对象也有合并方法，那就是`Object.assgin( )`。

```
var a={a:'hello'};
var b={b:'world'};
var c={c:'!!!'};

let d=Object.assign(a,b,c)
console.log(d);
```
