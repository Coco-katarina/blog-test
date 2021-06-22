# html篇
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
