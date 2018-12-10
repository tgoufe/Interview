# **JavaScript部分**

## 数据类型
### 1.JavaScript有哪些种基本数据类型？
```
    基本数据类型:(原始数据类型)Undefined、Null、Boolean、Number、String、
                Symbol( ECMAScript 2015新增 )
```
 
#### 1.1基本数据类型和引用数据类型的区别是什么？

```
    原始数据类型直接存储在栈(stack)中，占据空间小、大小固定，没有原型，没有构造函数;
    使用typeOf区分。typeof null === 'object'; // 从一开始出现JavaScript就是这样的
    引用数据类型存储在堆(heap)中的对象,占据空间大、大小不固定。引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。
    使用instanceof区分。
```
#### 1.2Null和Undefined的区别

```markdown
 - null 		表示一个对象是“没有值”的值，也就是值为“空”；
   undefined 	表示一个变量声明了没有初始化(赋值)；

 - undefined不是一个有效的JSON，
   而null是；
   
 - undefined的类型(typeof)是undefined；
   null的类型(typeof)是object；
```

## 变量与运算
### 1.JavaScript转数字类型有哪几种方法？各有什么优缺点？
```markdown
    转换函数parseInt()、parseFloat(),强制类型转换Number(),弱类型转换。
  - 转换函数转换的主体是字符串，其他类型都将被转换为NaN，转换的时候，从字符串的第一位开始，直到字符串不能转换为正确的数字或字符串最后一位停止。
  - 强制类型转换和弱类型转换转换的是整体，如‘22.33.66’将被转换为NaN，可以将null转换为0。
  - 弱数据类型转换多发生在计算过程中，可能造成意想不到的错误，应尽量避免。
```

### 2.JavaScript字符串互相比较的原理是什么？为什么'9' > '11'?
```
    从第一位开始，逐个比较charCode
    根据charCode表，9的对应是3A，1的对应是32，所以'9'>'11'
```
**注意区分二元加减运算符对js数据类型进行的转换是不同的。**

### 3.运算和优先级：
#### 3.1
```javascript
    let a = '22' + '66'; 
    let b ='22' - '66 ';
    console.log(a,b) //'2266',-44
```
#### 3.2
```javascript
    console.log("0 || 1 = " + (0 || 1));//0 || 1 = 1
    console.log("1 || 2 = " + (1 || 2));//1 || 2 = 1
    console.log("0 && 1 = " + (0 || 1));//0 && 1 = 0
    console.log("1 && 2 = " + (1 || 2));//1 && 2 = 2
```
**在JavaScript中，都是||和&&是逻辑运算符，当从左向右计算时返回第一个完全确定的“逻辑值”。
对于||运算符，当左边的第一个值的Boolean为true时，就返回该值，如果为false，就返回下一个值。
对于&&运算符，当左边的第一个值的Boolean为true时，计算下一个值并返回，如果为false，则返回当前值。**

#### 3.3
```javascript
    console.log(false == '0');//true
    console.log(false === '0');//false
```
**"=="会将其两边的数据进行弱数据类型转换之后再进行比较,'0'被转换为Boolean值false，所以返回true。而"==="则会直接进行相等的比较，所以返回false**

## DOM与BOM
### 1.基本的DOM操作有哪些？

```markdown
    获取节点:getElementById、getElementsByClassName、getElementsByTagName、 getElementsByName、querySelector、querySelectorAll,
    对元素属性进行操作:getAttribute、 setAttribute、removeAttribute，
    对节点进行增删改:appendChild、insertBefore、replaceChild、removeChild、 createElement
    ……
```

## 对象
### 1.JavaScript有哪些内置对象？
```
    在引擎初始化阶段就被创建好的对象,不需要New
    global、Object、Function、Array、String、Boolean、Number、Math、Date、RegExp、JSON、
    Error（Error,EvalError, RangeError, ReferenceError,SyntaxError, TypeError ,URIError)
```

### 2.Array对象方法有哪些方法？

```javascript
    - push() //添加元素到数组的末尾
    - unshift() //添加元素到数组的头部
    - pop() //删除数组末尾的元素
    - shift() //删除数组头部的元素
    - reverse() //颠倒数组中元素的顺序
    - sort() //对数组的元素进行排序
    - indexOf() //找出/某个元素在数组中的索引
    - splice() //通过索引删除某个元素
    - concat() //连接两个或更多的数组
    - join() //	把数组的所有元素放入一个字符串
    - slice() //从某个已有的数组返回选定的元素
    - valueOf() //返回数组对象的原始值
    - toString() //把数组转换为字符串
    - toLocaleString() //	把数组转换为本地数组
```
[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)

#### 2.1怎么区分数组和对象
```javascript
   - Object.prototype.toString.call(arr) === "[object Array]" //数组 => true;
   - Array.isArray(arr);//数组 => true;
   - arr instanceof Array;//数组 => true;
   - arr.constructor == Array;//数组 => true;
   - Array.prototype.isPrototypeOf(arr);//数组 => true;
   - typeof arr && !isNaN(arr.length);//数组 => true;
```
#### 2.2求两个数组的并集、交集、差集？
```javascript
    let array1 = new Set([1,3,4,7,8,9]),
        array2 = new Set([2,5,6,8]);
    // 并集
    let unionSet = new Set([...array1, ...array2]);
    console.log([...unionSet]);
    //交集
    let intersectionSet = new Set([...array1].filter(x => array2.has(x)));
    console.log([...intersectionSet]);
    //差集 
    let differenceSet = new Set([...array1].filter(x => !array2.has(x)).concat([...array2].filter(x => !array1.has(x))));
    console.log([...differenceSet]);

```
#### 2.3使用ES6的语法实现下面的功能
```javascript
    //将'start'插入到[1,2,3,4,5]数组的头部
    let myArray = [1,2,3,4,5],
        str = 'start';
    myArray = ___________;//[str, …myArray]
```
**在ES6中，有对数组进行的扩展操作，…运算符即是其中一种**

#### 3.["1", "2", "3"].map(parseInt)的结果是什么？parseInt("6.022e23", 10) 和 parseInt(" 131", 2)的结果是什么？    
```javascript
    ["1", "2", "3"].map(parseInt) //[1, NaN, NaN]
    parseInt("6.022e23", 10)      //6
    parseInt(" 131", 2)           //1
```


### 4.使用new 实例化一个对象，经历了哪些步骤?
```markdown
   1.构造一个新的对象
   2.使用指定的参数调用构造函数,并将 this 绑定到新创建的对象，同时继承该函数的原型。
   3.执行构造函数中的代码
   4.返回新对象
```

## 请求与存储
### 1.什么是跨域？有什么跨域解决方案？
```markdown
   跨域即不同源，
   如果两个页面的协议、端口、和域名都相同，则两个页面具有相同的源。
   
   jsonp、iframe、Window 属性的跨源访问(window.postMessage等)、服务器上设置
```
### 2.如何实现一个Ajax请求?
```markdown
 1.创建XMLHttpRequest对象,也就是创建一个异步调用对象
 2.创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息
 3.设置响应HTTP请求状态变化的函数
    0 (未初始化) or (请求还未初始化)
    1 (正在加载) or (已建立服务器链接)
    2 (加载成功) or (请求已接受)
    3 (交互) or (正在处理请求)
    4 (完成) or (请求已完成并且响应已准备好)
 4.打开链接
 5.发送HTTP请求
 6.获取异步调用返回的数据
 7.使用JavaScript和DOM实现局部刷新
```

### 3.Cookie LocalStorge SessionStorge 区别
```
  数据传递:
    cookie数据始终在同源的http请求中携带（即使不需要），即会在浏览器和服务器间来回传递。
    sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

  存储大小：
  	cookie数据大小不能超过4k。
  	sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。

  有期时间：
  	localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
  	sessionStorage  数据在当前浏览器窗口关闭后自动删除。
  	cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭.
  	
  作用域:
    sessionStorage不在不同的浏览器窗口共享，即使是同一个页面。
    localStorage和cookies是在所有同源窗口中共享的。
```
### 4.从浏览器输入url到页面渲染经历了哪些步骤?
```markdown
   1.地址栏输入url
   2.域名解析(DNS解析）
   3.建立连接(TCP三次握手，四次挥手)
   4.发送请求(HTTP请求)
   5.服务器处理请求，返回response
   6.浏览器渲染页面(浏览器解析HTML文件构建DOM树，然后解析CSS文件构建渲染树,js会阻塞渲染)
```

## ES6
### 1.平常会使用哪些ES6的特性
```
- let 和 const 命令
- 变量的解构赋值
- 模板字符串
- RegExp 构造函数
- 箭头函数
- async 函数
- Promise 对象
- for...of 循环
- Set 和 Map 数据结构
- Symbol 数据类型
- ……
```
---

## 继承
### 1.Js继承有多少种方式？原理是什么？有什么缺点？
```markdown
   
```

## 作用域
### 1.怎么理解js作用域？什么是作用域链？怎么理解闭包？
```markdown
   js的作用域是基于函数的，每创建一个函数就生成一个新的作用域。作用域的内部可以访问外部，但是外部不可以访问内部。
   作用域的存在可以避免命名污染 ，但是在创建函数的过程中因为要声明新的函数或者新的变量，所以会污染当前作用域，可以使用IIFE来避免。
   ES6之前，js并不提供块级作用域，但是可以使用try/catch的catch分句、with、eval来创建和修改作用域
   
```
---

##事件
### 1.什么是事件冒泡、事件捕获？怎么理解事件代理、事件委托
```markdown

```

##其他
### 1.实现函数 createCurry 
>已知如下
```javascript 1.8
const A = function (a,b,c) {
    return a + b + c;
};
var _A = createCurry(A);
```
>希望以下操作结果相同
```javascript 1.8
A(1,2,3);
_A(1)(2)(3);
_A(1,2)(3);
_A(1)(2,3);
_A(1,2,3);
```
### 2.实现函数 compose 
>期望如下
```javascript 1.8
const fn = compose(f1,f2,f3,f4)
fn(...args) === f1(f2(f3(f4(...args))))
```
