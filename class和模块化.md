## 类

**_类的声明_**

先声明一个最简单的 coder 类，类里只有一个 name 方法，方法中打印出传递的参数。

```
class coder{
    name(val){
        console.log(val);
    }
}
```

**_类的使用_**

我们已经声明了一个类，并在类里声明了 name 方法，现在要实例化类，并使用类中的方法。

```
class Coder{
    name(val){
        console.log(val);
    }
}

let pika= new Coder;
pika.name('jspang');
```

**_类的多方法声明_**

```
class Coder {
  name(val) {
    console.log(val);
    return val;
  }
  skill(val) {
    console.log(this.name("pika") + ":" + "Skill is " + val);
  }
}
let pika = new Coder();
// pika.name("pika");
pika.skill("web");
```

这里需要注意的是两个方法中间不要写逗号了，还有这里的 this 指类本身，还有要注意 return 的用法。

**_类的传参_**

在类的参数传递中我们用 constructor()进行传参。传递参数后可以直接使用 this.xxx 进行调用。

```
class Coder {
  name(val) {
    console.log(val);
    return val;
  }

  skill(val) {
    console.log(this.name("pika") + ":" + "Skill:" + val);
  }

  constructor(a, b) {
    this.a = a;
    this.b = b;
  }

  add() {
    return this.a + this.b;
  }
}

let pika = new Coder(1, 2);
console.log(pika.add());
```

我们用 constructor 来约定了传递参数，然后用作了一个 add 方法，把参数相加。这和以前我们的传递方法有些不一样，所以需要多注意下。

**_class 的继承_**

ES6 中的继承与 java 的继承有点相类似，直接看代码：

```
class htmler extends Coder {}
let xiaoQ = new htmler();
xiaoQ.name("pikaQ");//pikaQ
```

声明一个 htmler 的新类并继承 Coder 类，htmler 新类里边为空，这时候我们实例化新类，并调用里边的 name 方法。结果也是可以调用到的。

## 模块化

模块化操作主要包括两个方面：

- export :负责进行模块化，也是模块的输出。
- import : 负责把模块引，也是模块的引入操作。

**_export 的用法_**

export 可以让我们把变量，函数，对象进行模块话，提供外部调用接口，让外部进行引用。先来看个最简单的栗子，把一个变量模块化。创建一个 module.js 文件，然后在文件中输出一个模块变量。

```
export var a = 'hello';
```

然后可以在 index.js 中以 import 的形式引入。

```
import {a} from './module.js';

console.log(a);
```

这就是一个最简单的模块的输出和引入。

**_多变量的输出_**

这里声明了 3 个变量，需要把这 3 个变量都进行模块化输出，这时候我们给他们包装成对象就可以了。

```
var a ='hello';
var b ='world';
var c = '!!!';

export {a,b,c}
```

**_函数的模块化输出_**

```
export function add(a,b){
    return a+b;
}
```

**_as 的用法_**

有些时候我们并不想暴露模块里边的变量名称，而给模块起一个更语义话的名称，这时候我们就可以使用 as 来操作。

```
var a ='hello';
var b ='world';
var c = '!!!';

export {
    a as hello,
    b as world,
    c as mark
}
```

**_export default 的使用_**

加上 default 相当是一个默认的入口。在一个文件里 export default 只能有一个。我们来对比一下 export 和 export default 的区别

**1.export**

```
export var a ='hello world';

export function add(a,b){
    return a+b;
}
```

对应的导入方式

```
import {a,add} form './module';//也可以分开写
```

**2.export defalut**

```
export default var a='hello world';
```

对应的引入方式

```
import hw from './temp';//随便的名字，因为export default是默认的，名字对他没影响，不过在开发中还是要做到语义化，不然后期维护就麻烦了。
```

ES6 的模块化不能直接在浏览器中预览，必须要使用 Babel 进行编译之后正常看到结果。
