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
跳动的心  https://jsbin.com/cesoxonara/1/edit?html,css,output

### transition 过渡
#### 作用 
补充中间帧
#### 语法
属性名 时长 过渡方式 延迟
* 例： transition：left 20ms linear，top 400ms
* 
      ps：可以用逗号分隔两个不同属性
可以用all代表所有属性，transition：all 200ms
* 过渡方式参考 https://developer.mozilla.org/zh-CN/docs/conflicting/Web/CSS/easing-function

### animation 
1. 声明关键帧  @keyframes 
2. 添加动画  animation 申明的关键帧名字
动画停在最后一帧 最后加上forwards即可
#### @keyframes完整语法
1.标准写法  
https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes
* from  to
```
@keyframes slidein {
  from {
    transform: translateX(0%); 
  }

  to {
    transform: translateX(100%);
  }
}
```
* 百分数
```
@keyframes identifier {
  0% { top: 0; left: 0; }
  30% { top: 50px; }
  68%, 72% { left: 50px; }
  100% { top: 100px; left: 100%; }
}

```
#### animation语法
时长 | 过渡方式 | 延迟 | 次数 | 方向 | 填充模式 | 是否暂停 | 动画名
* 时长：1s / 1000ms
* 过渡方式： 同transition
* 次数： 数字 或infinite 无限
* 方向： reverse | alternate（交替变化） | alternate-reverse
* 填充模式:none | forwards（停在最后一帧） | backwards | both
* 是否暂停：paused | running

##### 例子
跳动的心 
https://jsbin.com/jadecehewu/1/edit?html,css,output



