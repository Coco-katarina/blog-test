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
 f2中的a 和 f3 组成了闭包
## arguments
伪代码数组

