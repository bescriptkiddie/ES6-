## ...扩展运算符

利用`...`扩展运算符可以实现数组的复制，因为在 js 中数组是引用类型，正常的赋值只会改变指针的指向，在对新数组进行赋值时，也会改变原数组的值。

```
let arr1=['hello','world'];
let arr2=arr1;
console.log(arr2);//hello world
arr2.push('!!!');
console.log(arr1);//hello world!!!
```

如此便不能达到我们修改的目的，我们利用...扩展运算符对代码进行改写。

```
let arr1=['hello','world'];
let arr2=[...arr1];
arr2.push('!!!');
console.log(arr1);//hello world
console.log(arr2);//hello world!!!
<-----------转换成ES5之后-------------->
var arr2 = [].concat(arr1);
```

我们会发现扩展运算符使用了 concat()函数，这样就不会改变 arr1 的值了，但是...扩展运算符只是给我们提供了`部分深拷贝`的功能，可以利用`JSON.parse(JSON.stringify(arr))`实现常规的深拷贝

```
arr1 = JSON.parse(JSON.stringify(arr))
arr1 = JSON.parse(JSON.stringify(obj))
```

## ...rest 运算符

rset 运算符跟扩展运算符一样都是用`...`表示，我们通常用它来接受一个不知道会传进多少个参数得情况中。

```
function js(first,...arg){
    for(let val of arg){
        console.log(val);
    }
}
js(0,1,2,3,4,5,6,7);
```

正常情况中不用特地去区分扩展运算符跟 rest 运算符，他们的用法很相似，不过更多的是在实践中体验最佳实践。
