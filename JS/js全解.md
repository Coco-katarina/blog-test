# JS全解

## JS语法
### 表达式与语句
#### 表达式
* 1 + 2 表达式的值为3
* add(1,2)表达式的值为函数的返回值
* console.log表达式的值为函数本身
* console.log(3)表达式的值为多少？ 打印出来的是3，但是值是undefined

#### 语句
* var a = 1 是一个语句

#### 二者的区别
1. 表达式一般都有值，语句可能有也有可能没有
2. 语句一般会改变环境(声明、赋值)
3. 上面两句话并不是绝对的

#### 区分大小写

### 标识符
#### 规则
* 第一个字符，可以是Unicode字母或$或_或中文
* 后面的字符，除了上面所说，还可以是数字

#### 变量名是标识符
* var _ =1
* var $ =2
* var 你好 = ' hi'

### while循环
#### while(表达式){语句}  
先判断表达式真假，do...while先执行后判断

### label语句
#### 语法
```
foo :{
  console.log(1);
  break foo;
  console.log('本行不会输出');
 }
 console.log(2);
```
*  面试
```
{
  foo : 1
}
```
问，上面的是啥

### 进制
* HEX 16进制
* BIN 2进制
* OCT 8进制
* DEC 10进制

###  编码
#### Unicode 万国码
1. 优点
* 已收录 13 万字符（大于 16 位），全世界通用，以后还会继续扩充，不会停止
* 最新版只添加了一个字——令和的合体字

2. 缺点
* 两个字节不够用，每个字符要用三个及以上字节
* 这样所有文件都扩大 50%，不划算，出现UTF-8

#### UTF-8  
##### 实例
1. 存储「a 」
* a 对应的 Unicode 编号为 97，十六进制为 61
* Unicode 直接存： 0000000000000000‭01100001‬
* UTF-8偷懒存法： 01100001
* 三字节变一字节，比GBK 还省
2. 存储「你」
* 你对应的 Unicode 编号为 4F60
* Unicode 直接存： 00000000‭0100111101100000‬
* UTF-8偷懒存法： ‭111001001011110110100000‬
* 还是三字节，没有省，但是字母都能省一点
* UTF-8 中的 8 的意思是最少可用 8 位存一个字符

##### 规则  
以「你a」为例  

 11100100101111011010000001100001
如何知道上述内容表示什么字符？
1. 读 8 位信息 11100100
2. 发现开头有 3 个 1，说明这个字符有 3 个八位
3. 于是再读两个 8 位信息 10111101 10100000
4. 前面的 10 不要，其他合起来，得 0100111101100000
5. 这就还原为 Unicode 的你了：000000000100111101100000 
6. 再读 8 为信息 01100001，发现开头是 0，说明这个字符只占 8 位
7. 这就还原为 Unicode 的 a 了：000000000000000001100001


## JS数据类型
### 7种（大小写无所谓）
* 数字 number
* 字符串 string
* 布尔 bool
* 符号 symbol
* 空 undefined
* 空 null
* 对象 object
总结：四基两空一对象
### 以下不是数据类型
* 数组、函数、日期
* 它们都属于 object

#### 特殊值
* 正0 和 负0 都等于 0，要严谨
* 无穷大 Infinity 、+Infinity 、-Infinit
* 无法表达的数字 NaN(Not a Number) 但它是一个数字

#### 64位浮点数  
64位存储一个number
* 符号占1位
* 指数占11位(-1023~1024)
* 有效数字占52位(开头的1省略)
##### 范围(忽略符号位) 
* 指数拉满、有效数字拉满，得到最大二进制数字Number.MAX_VALUE: 1.7976931348623157e+308
* 指数负方向拉满、有效数字最小1，得到最小值Number.MIN_VALUE: 5e-324

#### 精度(有效数字)
最多只能到52+1个二进制位表示有效数字，2^53 对应的十进制是 9 后面 15 个零,所以15位有效数字都能精确表示
16位有效数字如果小于 90 开头，也能精确表示9110000000000001 就存不下来

### 字符串
转义
* \r 回车
* \t tab制表符

base64 转码
* window.btoa 正常字符串转为Base64编码的字符串
* windeo.atob Base64编码的字符串转为原来的字符串

### bool
5个falsy(相当于false但又不是false)值
1. undefined
2. null
3. 0
4. NaN
5. ‘’

### undefined和null的区别
没有本质区别
1. 如果一个变量声明了但没有赋值，那么默认值就是undefined而不是null
2. 如果一个函数，没有写return，那么默认return undefined而不是null
3. 前端程序员习惯上，把非对象的空值写为undefined，把对象的空值写为null，仅仅是习惯上而已

### symbol
https://zhuanlan.zhihu.com/p/22652486

#### 变量声明
var、let、const

var变量提升，网道教程https://wangdoc.com/javascript/basic/grammar.html#%E5%8F%98%E9%87%8F%E6%8F%90%E5%8D%87

js密码花园 http://bonsaiden.github.io/JavaScript-Garden/zh/


### Object对象
#### 定义
无序的键值对的数据集合
* 隐藏属性 
JS中每一个对象都有一个隐藏属性，这个隐藏属性储存着其共有属性组成的对象(原型)的地址
* 查看属性
1. 查看自身key和values  Object.entries(obj)
2. 查看自身 + 公有属性 console.dir(obj）
4. 判断一个属性是自身的还是共有的
  obj.hasOwnProperty('toString')

## JS的分类
### new
new X()自动做了四件事情
1. 自动创建空对象
2. 自动为空对象关联原型，原型地址指定为X.prototype
3. 自动将空对象作为this关键词运行构造函数
4. 自动return this

构造函数X
* X函数本身负责给对象本身添加属性
* X.prototype对象负责保存对象的共用属性

代码诡诞
1. 大小写
   * 所有构造函数(专门用于创建对象的函数)首字母大写
   * 所有被构造出来的对象，首字母小写
2. 词性
   * new 后面的函数，使用名词形式
   * 其他函数，一般使用动词开头

#### 原型公式
对象.__proto__ === 其构造函数.prototype   
你是谁创造的你的原型就是谁的prototype属性对应的对象

### JS终极一问
1. window是谁构造的
  Window，可以通过constructor属性看出构造者
2. window.Object是谁构造的
  window.Function，因为所有函数都是window.Function构造的
3. window.Function是谁构造的
  window.Function，浏览数构造了Function，然后指定它的构造者是自己
  
### 纠错本
1. 关于「原型」，正确的是（多选）下文中的 x 均代表普通对象
  * 「x 的原型」等价于「x.__proto__ 所指的对象」 ，有时为了方便，我们可以认为「x 的原型」等价于「x.__proto__ 」
  * 一个对象的原型指的是这个对象与其他同类对象的公有属性的集合，比如 obj1 和 ob2 同时拥有 toString / valueOf，那么 toString / valueOf 等属性组成的对象，就是 obj1 和 obj2 的原型，这个原型的地址一般储存在构造函数的 prototype 里
  *  x.__proto__和 Object.prototype 存储着同一个对象的地址，这个对象就是 x 的原型
  *  每个对象都有原型，但除了「根对象 Object.prototype」比较特殊，Object.prototype 这个对象的原型为空 null
 2. 关于 prototype 属性，正确的有
  * 所有函数一出生就有一个 prototype 属性（除了箭头函数）
  * 所有 prototype 一出生就有一个 constructor 属性
  * 所有 constructor 属性一出生就保存了对应的函数的地址
  * 如果一个函数不是构造函数，它依然拥有 prototype 属性，只不过这个属性暂时没什么用
  * 如果一个对象不是函数，那么这个对象一般来说没有 prototype 属性，但这个对象一般一定会有 __proto__ 属性
 3. 关于 Object.prototype，正确的是（多选）
  * Object.prototye 是「Object 构造出来的对象 obj」的原型，即 obj.__proto__ === Object.prototype
  * Object.__proto__ 是 Object 的原型，由于 Object 是函数，而所有函数的原型都是 Function.prototype，所以 Object.__proto__ === Function.prototype
  *  Object.prototye 不是 Object 的原型，Object.__proto__ 才是 Object 的原型（还记着之前答过「x.原型 等价于 x.__proto__」吗，现在只不过是把 x 替换成 Object。很多人都搞不清楚 Object.__proto__ 和 Object.prototype 哪一个才是 Object 的原型，其实只要记住公式就好办了）
 4. 所有「函数对象」的「构造函数」都是 Function
  * 对


## JS数组
js 只提供浅拷贝
#### 新建
* let arr = [1,2,3]
* let arr = new Array(1,2,3)
* let arr = new Array(3)

#### 伪数组
* let divList = document.querySelectorAll('div')
伪数组的原型链中并没有数组的原型
 
### 删元素
delete 删除元素，但是位置保留值为empty，数组长度不变，称为稀疏数组  
删除中间的元素
* arr.splice(index, 1) //删除index的一个元素
* arr.spilice(index,1,'x','y')  //删除并在删除位置添加'x','y'

### 增元素
* 尾部添加 push
* 头部添加 unshift
* 中间添加 splice(index,0,'x') // index出插入x


