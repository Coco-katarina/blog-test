# JS的前世今生

本文你将了解到：

* JavaScript 的诞生
* JavaScript 的发展
* JavaScript 的10个设计缺陷

主要参考以下文章
* 阮一峰的博客 http://www.ruanyifeng.com/blog/2011/06/10_design_defects_in_javascript.html
* JavaScript 历史 https://zh.wikipedia.org/wiki/JavaScript#%E5%8E%86%E5%8F%B2
## 一、Javascript 诞生
### 1. JS 语言概览
JavaScript（简称“JS”） 是一种具有函数优先的轻量级，解释型或即时编译型的编程语言。虽然它是作为开发Web页面的脚本语言而出名，但是它也被用到了很多非浏览器环境中，JavaScript 基于原型编程、多范式的动态脚本语言，并且支持面向对象、命令式和声明式（如函数式编程）风格。

### 2. 诞生背景
1994年，网景公司（Netscape）发布了 Navigator 浏览器0.9版。这是历史上第一个比较成熟的网络浏览器，轰动一时。但是，这个版本的浏览器只能用来浏览，不具备与访问者互动的能力。比如，如果网页上有一栏"用户名"要求填写，浏览器就无法判断访问者是否真的填写了，只有让服务器端判断。如果没有填写，服务器端就返回错误，要求用户重新填写，这太浪费时间和服务器资源了。

因此，网景公司急需一种网页脚本语言，使得浏览器可以与网页互动。工程师 Brendan Eich 负责开发这种新语言。他觉得，没必要设计得很复杂，这种语言只要能够完成一些简单操作就够了，比如判断用户有没有填写表单。因而，为了应付公司安排的任务，他只用10天时间就把 JavaScript 设计出来了。

由于设计时间太短，语言的一些细节考虑得不够严谨，导致 JS 诞生后很长一段时间，写出来的程序混乱不堪。

### 3. JS 设计思路
总的来说，Brendan Eich 的设计思路是这样的：

借鉴C语言的基本语法；
借鉴Java语言的数据类型和内存管理；
借鉴Scheme语言，将函数提升到"第一等公民"（first class）的地位；
借鉴Self语言，使用基于原型（prototype）的继承机制。
所以，JavaScript语言实际上是两种语言风格的混合产物----（简化的）函数式编程+（简化的）面向对象编程。这是由Brendan Eich（函数式编程）与网景公司（面向对象编程）共同决定的。

## 二、Javascript 发展
### 1. 从混乱到规范
发展初期，JavaScript的标准并未确定，同期有Netscape的JavaScript，微软的JScript和CEnvi的ScriptEase三足鼎立。为了互用性，Ecma国际（前身为欧洲计算机制造商协会）创建了ECMA-262标准（ECMAScript），两者都属于ECMAScript的实现，尽管JavaScript作为给非程序人员的脚本语言，而非作为给程序人员的脚本语言来推广和宣传，但是JavaScript具有非常丰富的特性。

1997年，在ECMA（欧洲计算机制造商协会）的协调下，由Netscape、Sun、微软、Borland组成的工作组确定统一标准：ECMA-262。完整的JavaScript实现包含三个部分：ECMAScript，文档对象模型，浏览器对象模型。

### 2. 现状及发展
良好编程规范的确立，加上第三方函数库的帮助，Javascript能够实现非常强大的功能。

JavaScript目前是网页编程的唯一语言，只要互联网继续发展，它就必然一起发展。目前，许多新项目大大扩展了它的用途，Node.js 使得JavaScript可以用于后端的服务器编程，coffeeScript 使我们可以用 python 和 ruby 的语法，撰写 Javascript。

复杂的数据交互（比如内嵌过滤、即时反馈、基于上下文的规则等）以前需要花数个星期才能编出来的效果，随着前端工程化的实现，Vue、React等框架的不断普及，如今能达到开箱即用的程度。作为一门语言，JavaScript在迅速成长，高质量的开发会不断地催生新的需求、新的工具。

## Javascript 十个设计缺陷
1. 不适合开发大型程序
JavaScript没有名称空间（namespace），很难模块化；没有如何将代码分布在多个文件的规范；允许同名函数的重复定义，后面的定义可以覆盖前面的定义，很不利于模块化加载。

2. 非常小的标准库
JavaScript提供的标准函数库非常小，只能完成一些基本操作，很多功能都不具备。

3. null和undefined
null属于对象（object）的一种，意思是该对象为空；undefined则是一种数据类型，表示未定义。
```
　　typeof null; // object

　　typeof undefined; // undefined
```
两者非常容易混淆，但是含义完全不同。
```
　　var foo;

　　alert(foo == null); // true

　　alert(foo == undefined); // true

　　alert(foo === null); // false

　　alert(foo === undefined); // true
```
在编程实践中，null几乎没用，根本不应该设计它。

4. 全局变量难以控制
JavaScript的全局变量，在所有模块中都是可见的；任何一个函数内部都可以生成全局变量，这大大加剧了程序的复杂性。
```
　　a = 1;

　　(function(){

　　　　b=2;

　　　　alert(a);

　　})(); // 1

　　alert(b); //2
```
5. 自动插入行尾分号
JavaScript的所有语句，都必须以分号结尾。但是，如果你忘记加分号，解释器并不报错，而是为你自动加上分号。有时候，这会导致一些难以发现的错误。

比如，下面这个函数根本无法达到预期的结果，返回值不是一个对象，而是undefined。
```
　　function(){

　　　　return
　　　　　　{
　　　　　　　　i=1
　　　　　　};

　　}
```
原因是解释器自动在return语句后面加上了分号。
```
　　function(){

　　　　return;
　　　　　　{
　　　　　　　　i=1
　　　　　　};

　　}
```
6. 加号运算符
+号作为运算符，有两个含义，可以表示数字与数字的和，也可以表示字符与字符的连接。
```
　　alert(1+10); // 11

　　alert("1"+"10"); // 110
```
如果一个操作项是字符，另一个操作项是数字，则数字自动转化为字符。
```
　　alert(1+"10"); // 110

　　alert("10"+1); // 101
```
这样的设计，不必要地加剧了运算的复杂性，完全可以另行设置一个字符连接的运算符。

7. NaN
NaN是一种数字，表示超出了解释器的极限。它有一些很奇怪的特性：
```
　　NaN === NaN; //false

　　NaN !== NaN; //true

　　alert( 1 + NaN ); // NaN
```
与其设计NaN，不如解释器直接报错，反而有利于简化程序。

8. 数组和对象的区分
由于JavaScript的数组也属于对象（object），所以要区分一个对象到底是不是数组，相当麻烦。Douglas Crockford的代码是这样的：
```
　　if ( arr &&
　　　　typeof arr === 'object' &&
　　　　typeof arr.length === 'number' &&
　　　　!arr.propertyIsEnumerable('length')){

　　　　alert("arr is an array");

　　}
```
9. == 和 ===
==用来判断两个值是否相等。当两个值类型不同时，会发生自动转换，得到的结果非常不符合直觉。
```
　　"" == "0" // false

　　0 == "" // true

　　0 == "0" // true

　　false == "false" // false

　　false == "0" // true

　　false == undefined // false

　　false == null // false

　　null == undefined // true

　　" \t\r\n" == 0 // true
```
因此，推荐任何时候都使用"==="（精确判断）比较符。

10. 基本类型的包装对象
JavaScript有三种基本数据类型：字符串、数字和布尔值。它们都有相应的建构函数，可以生成字符串对象、数字对象和布尔值对象。
```
　　new Boolean(false);

　　new Number(1234);

　　new String("Hello World");
```
与基本数据类型对应的对象类型，作用很小，造成的混淆却很大。
```
　　alert( typeof 1234); // number

　　alert( typeof new Number(1234)); // object
  ```
