ES6 中的`promise`的出现给我们很好的解决了回调地狱的问题，`Promise`更符合人类的行为思考习惯，你可以想象它是一种承诺，当它成功时执行一些代码，当它失败时执行一些代码。完美解决了 ES5 中，多层回调带来的难题。

## promise 的基本用法

promise 执行多步操作非常好用，那我们就来模仿一个多步操作的过程，我们现在来模仿一个早上上班的流程：

1. 起床洗漱
2. 吃早餐
3. 换衣服上班
   这个过程是有一定的顺序的，必须先完成了前面的步骤才可以进行下一个步骤。那现在我们用 promise 来模拟这些步骤。

```
let status = 1; //定义一个成功的状态

function step1(resolve, reject) {
  console.log("1.起床洗漱");
  if (state == 1) {
    resolve("起床洗漱--完成");
  } else {
    reject("起床洗漱--失败");
  }
}

function step2(resolve, reject) {
  console.log("2.吃早餐");
  if (state == 1) {
    resolve("吃早餐--完成");
  } else {
    reject("吃早餐--失败");
  }
}

function step3(resolve, reject) {
  console.log("3.换衣服上班");
  if (state == 1) {
    resolve("换衣服上班--完成");
  } else {
    reject("换衣服上班--失败");
  }
}

new Promise(step1)
  .then(function (val) {
    console.log(val);
    return new Promise(step2);
  })
  .then(function (val) {
    console.log(val);
    return new Promise(step3);
  })
  .then(function (val) {
    console.log(val);
    return val;
  });//控制台输出如下：
        <!--1.起床洗漱-->
        <!--起床洗漱--完成-->
        <!--2.吃早餐-->
        <!--吃早餐--完成-->
        <!--3.换衣服上班-->
        <!--换衣服上班--完成-->
```

Promise 构造函数接受一个函数作为参数，该函数的两个参数分别是`resolve`和`reject`。它们是两个函数，由 JavaScript 引擎提供，不用自己部署。

- `resolve`函数的作用是:将 Promise 对象的状态从“未完成”变为“成功”（即从 pending 变为 resolved),在异步操作成功时调用,并将异步操作成功的结果,作为参数传递出去；
- `reject`函数的作用是:将 Promise 对象的状态从“未完成”变为“失败”（即从 pending 变为 rejected),在异步操作失败时调用,并将异步操作报出的错误,作为参数传递出去。

Promise 实例生成以后，可以用`then()`方法分别指定 resolved 状态和 rejected 状态的回调函数。

Promise 还有很多巧妙的用法，需要我们在实战中检验，查阅更多请到[阮一峰老师的 ES6](https://es6.ruanyifeng.com/?search=proxy&x=0&y=0#docs/promise)
