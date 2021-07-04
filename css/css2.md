# css属性
## position
 * static  默认值，待在文档流里
 * relative 相对定位，升起来但不脱离文档流
 * absolute 绝对定位，定位基准是祖先里的非static
 * fixed 固定定位，定位基准是viewport
 * sticky 沾滞定位 ，让该内容到顶部时，一直存在

### 经验
 1. 如果写了absolute，一般都得补一个relative

## transform
### 四个常用功能
1. 位移 translate
2. 缩放 scale
3. 旋转 rotate
4. 倾斜 skew

`translate:all .5s`可以看到动画效果
### 经验
1. 一般都需要配合transition过渡
2. inline元素不支持transform，需要先变成block

### 例子
跳动的心  https://jsbin.com/dulenosoxe/edit?html,css,output

### transition 过渡
#### 作用 
补充中间帧
#### 语法
属性名 时长 过渡方式 延迟
* 例： transition：left 20ms linear，top 400ms
      ps：可以用逗号分隔两个不同属性
可以用all代表所有属性，transition：all 200ms
* 过渡方式参考 https://developer.mozilla.org/zh-CN/docs/conflicting/Web/CSS/easing-function

