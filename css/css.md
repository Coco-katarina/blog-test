# CSS篇

## 语法  
at语法

```
@charset "UTF-8"; //字符集设置必须放在第一行
@import url(2.css);
@media (min-width : 100px) and (max-width : 200px){
  语法一
}
```
## 盒模型  

html文档中的每个元素都被描绘成矩形盒子，这些矩形盒子通过一个模型来描述其占用空间，这个模型称为盒模型。盒模型通过四个边界来描述：margin（外边距），border（边框），padding（内边距），content（内容区域），如图所示：
![image](https://user-images.githubusercontent.com/26460242/123813038-273a0d80-d927-11eb-9193-a77ec35237e0.png)

* content-box 内容盒
  内容就是盒子的边界
* border-box 边框盒
  边框才是盒子的边界
 
 ### 公式
 content-box width = 内容宽度
 border-box width = 内容宽度 + padding + border
 
 ### 长度单位
 * px 像素
 * em 相对于自身font-size的倍数
 * 百分数
 * 整数
 * rem
 * vw 和 vh
 
 ### 颜色
 * 十六进制 #FF6600 或 #F60
 * RGBA颜色 
 * hsl颜色
 
 彩虹小练习 http://js.jirengu.com/babimurizi/1/edit?html,css
 
 ## 布局
 ### float布局
 #### 步骤 
 子元素上加 `float: left`和`width`  
 在父元素上加`.clearfix` ，height为子元素包含的高度
 ```
 .clearfix:after{
  content:'';
  display:block;
  clear:both;
 }
 ```
 #### 经验 
*  会留一些空间，或者最后一个不设置width
*  不需要做响应式，手机没有IE，而float是为IE准备的
*  IE 6/7存在双倍margin bug，解决办法
   1. 将错就错，margin减半，`_margin-left:5px`
   2. 加上一个`display:inline-block`
* 平均布局，利用好-marigin
 
 例子：http://js.jirengu.com/sanutafute/1/edit?html,css,output
 
### flex局部
#### 属性
1. justify-content 将flex元素和主轴对齐
 * flex-start: 元素和容器的左端对齐
 * flex-end: 元素和容器的右端对齐
 * center: 元素在容器里居中
 * space-between:元素之间保持相等的距离
 * space-around:元素周围保持相等的距离
2.align-items 在交叉轴上对齐多个元素  align-self 在交叉轴上对齐一个元素，替换align-items
 * flex-start: 元素与容器的顶部对齐
 * flex-end: 元素与容器的底部对齐
 * center: 元素纵向居中
 * baseline: 元素在容器的基线位置显示
 * stretch: 元素被拉伸以填满整个容器
 3.flex-direction 定义主轴的方向
 * row: 元素摆放的方向和文字方向一致
 * row-reverse: 元素摆放的方向和文字方向相反
 * column: 元素从上放到下
 * column-reverse: 元素从下放到上
 4. flex-wrap 必须在单行或自动换行成多行
 *  nowrap: 所有的元素都在一行
 *  wrap: 元素自动换成多行
 *  wrap-reverse: 元素自动换成逆序的多行
 5. flex-flow
 * flex-direction和flex-wrap两个属性合一起的缩写，空格隔开
 6. align-content 行与行之间隔
 * flex-start: 多行都集中在顶部
 * flex-end: 多行都集中在底部
 * center: 多行居中
 * space-between: 行与行之间保持相等距离
 * space-around: 每行的周围保持相等距离
 * stretch: 每一行都被拉伸以填满容器

以上例子整改：http://js.jirengu.com/vuxuhufede/1/edit

#### 练习 青蛙跳 https://flexboxfroggy.com/#zh-cn

#### 经验
* 永远不要把width和height写死，除非特殊情况
* 用min-width / max-width / min-height / max-height
* flex和margin-xxx:auto 配合有意外的效果


### 草图软件
1. Balsamiq
2. Figma
3. 墨刀
4. Adoube XD
