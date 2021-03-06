# html篇
https://wangdoc.com/html/index.html

## 初始hmtl代码讲解

* 禁用缩放

`
<meta name="viewport" content="width=device-width, initial-scale=1.0">
`

* 告诉IE使用最新内核 

`<meta http-equiv="X-UA-Compatible" content="IE=edge">`

## 章节标签
### 表示文章/书的层级
  * 章节 section
  * 文章 article
  * 主要内容main
  * 旁支内容aside
  * `&copy;` 版权标志
## 全局属性
### 所有标签都有的属性
* contenteditable 任何一个元素可以被 编辑
* hidden 
* tabindex  控制tab的选中高亮顺序，0：最后一个，-1：别走我这儿
* id 元素唯一用，对应"#"
* class 元素不唯一时用,对应"."

### 内容标签
* pre 保留输入的回车、空格 <pre>空  格   </pre>

## 英语小课堂
1. hyper  超级
2. target 目标
3. reference 引用
4. frame 边框、框架
5. blank 空白

## 重点标签
### a标签
#### 属性
1. href
取值
 * 网址 https://... 或  http://...  或//...
 * 路径 a/b/c
 * 伪协议 JavaScript：代码; mailto:邮箱；tel: 手机号
 * id  href=#XXX
2. target
内置名字
 * _blank 空白页面
 * _top 最顶层页面
 * _parent 父级窗口
 * _self  当前页面
3. download
5. rel=noopener

### table标签
#### 相关标签
* thead
* tbody
* tfoot
#### 相关样式
1. table-layout
  * auto 根据内容分配宽度
  * fixed 尽量等宽
2. border-collapse
   border是否合并，默认"separate" 分开，合并设为"collapse"
3. border-spacing
   border之间的间隔
   
### img标签
#### 作用
发出get请求，展示一张图片
#### 属性
1. alt 图片加载失败显示的内容
2. height、width 设其一 图片自适应，如果两者一起设置会变形
3. src
#### 事件
onload
onerror
#### 响应式
max-width : 100%

### form标签
#### 作用
发出get/post请求，然后刷新页面
#### 属性
1. action 发情请求的url
2. autocomplete "on"/"off" 自动填充
3. method 发送请求的方法
4. target 规定在何处打开 action URL
   * _blank
   * _self
   * _parent
   * _top
   * framename
#### 事件
onsubmit  
要放一个type=submit才能触发submit事件

ps： input和button的type都设置为"submit"的区别，input因为设置的vaule值所以不可以套用其他标签，但是button可以，例如<button type="submit"><strong>提交</strong></button>

