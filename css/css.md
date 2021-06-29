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
 
 
 
 
 

