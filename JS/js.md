# JS概览
## 数据类型
* number
* string
* null
* undefined
* bool
* symbol
* object

## 常用常考
* 闭包、原型
* 类、继承
* MVC、Flux
* 高阶函数
* 前端工程化

## 英语小课堂
* Operating System 操作系统，简称OS
* kernel 内核
* runtime 运行时
* compile 编辑
* environment 环境，简称env
* memory 记忆、存储
* person 一个人
* people 一群人

## 操作系统(以Linux为例)
1. 首先加载操作系统内核
2. 启动初始化进程，编号为1，每个进程都有编号
3. 启动系统服务：文件、安全、联网
4. 等待用户登录：输入密码登录/ssh登录
5. 登录后，运行shell，用户就可以和操作系统对话了
6. bash是一种shell，图形化界面可认为是一种shell

## 浏览器的功能
* 发起请求，下载HTML，解析HTML，下载CSS，解析CSS，渲染界面，下载JS，解析JS，执行JS等
* 功能模块：用户界面、渲染引擎、JS引擎、存储等

## JS引擎
### JS引擎举例
* Chrome用的是V8引擎，C++编写
* 网景用的是SpiderMonkey，后被Firefox使用，C++
* Safari用的是JavaScriptCore
* IE用的是Chakra(JScript9) 
* Edge用的是Chakra(JavaScript)
* Node.js用的是V8引擎

### 主要功能
* 编译： 把JS代码翻译为机器能执行的字节码或机器码
* 优化：改写代码，使其更高效
* 执行：执行上面的字节码或机器码
* 垃圾回收：把JS用完的内存回收，方便之后再次使用

## 瓜分内存
![neicun](https://user-images.githubusercontent.com/26460242/126871963-46545be2-e147-4247-b776-aa0c6c8bb9b0.PNG)

### 红色区域
#### 作用
* 存档数据，目前只研究该领域
* 不存变量名，变量名存在【不知什么区】
* 每种浏览器的分配规则并不一样
* 区域并不完整

#### Stack和Heap
* Stack ：栈，每个数据顺存放
* Heap：堆，每个数据随机存放

## JS入门三座大山之原型



