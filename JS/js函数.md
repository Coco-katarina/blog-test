# JS 函数
## 闭包
### 概念
如果一个函数用到了外部的变量，那么这个函数加这个变量就叫做闭包
#### 实例
```
function f1(){
  let a = 1
  function f2(){
    let a = 2
    function f3(){
      console.log(a)
    }
    a = 22
    f3()
  }
  console.log(a)
  a = 100
  f2()
}
f1()
```
 f2 中的a 和 f3 组成了闭包
## arguments
伪代码数组
### 如何传arguments
```
  function fn(){
    console.log(arguments)
  }
  fn(1,2,3)  //调用fn即可传arguments，arguments就是[1,2,3]伪数组
```

## this
### 如何传this
```
  function fn(){
    console.log(this)
  }
  fn.call(xxx,1,2,3)  //xxx会自动转化成对象
```
this是隐藏参数，arguments是普通参数
#### 假设没有this
```
let person = {
  name: 'frank',
  sayHi(){
    console.log(`你好，我叫` + person.name)
  }
}
```
分析  
我们可以用直接保存了对象地址的变量获取 'name'，我们把这种办法简称为引用，会有以下两个问题
1.  问题一
```
let sayHi = function(){
  console.log(`你好，我叫` + person.name)
}
let person = {
  name: 'frank',
  'sayHi': sayHi
}
分析
person 如果改名，sayHi 函数就挂了
sayHi 函数甚至有可能在另一个文件里面
所以我们不希望 sayHi 函数里出现 person 引用

```
2.  问题二
```
class Person{
  constructor(name){
    this.name = name 
    // 这里的 this 是 new 强制指定的
  }
  sayHi(){
    console.log(???)
  }
}
分析
这里只有类，还没创建对象，故不可能获取对象的引用
那么如何拿到对象的 name ？
```

#### Python 代码
```
class Person:
  def __init__(self, name): # 构造函数
    self.name = name

  def sayHi(self):
    print('Hi, I am ' + self.name)
person = Person('frank')
person.sayHi()
特点
  每个函数都接受一个额外的 self
  这个 self 就是传进来的对象
  只不过 Python 会偷偷帮你传对象
  person.sayHi() 等价于 person.sayHi(person)
  person 就被传给 self 了

```
#### JS在每个函数里加了this
```
let person = {
  name: 'frank',
  sayHi(this){
    console.log(`你好，我叫` + this.name)
  }
}

```
person.sayHi()相当于person.sayHi(person),然后 person 被传给 this 了（person 是个地址）。这样，每个函数都能用 this 获取一个未知对象的引用了
#### this的两种使用方法
1. 隐式传递
```
fn(1,2) // 等价于 fn.call(undefined, 1, 2)
obj.child.fn(1) // 等价于 obj.child.fn.call(obj.child, 1)

```
2. 显示传递
```
fn.call(undefined, 1,2)
fn.apply(undefined, [1,2])
```

#### 绑定this
使用 .bind 可以让 this 不被改变
```
function f1(p1, p2){
  console.log(this, p1, p2)
}
let f2 = f1.bind({name:'frank'})   // 那么 f2 就是 f1 绑定了 this 之后的新函数
f2() // 等价于 f1.call({name:'frank'})
```

## 箭头函数
* 里面的this就是外面的this
```
  console.log(this)  //window
  let fn = () => console.log(this)
  fn()  //window
```
* 上述例子使用call也无法改变
 ```
  fn.call({name:'text') //window
 ```
 
