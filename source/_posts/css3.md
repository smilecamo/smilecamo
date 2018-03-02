---
title: css3弹性布局Flexbox学习笔记
date: 2018-02-05 13:54:32
tags: CSS3 
categories: [CSS3布局]
---
![](http://www.runoob.com/wp-content/uploads/2015/07/5a7d00514af1e464221c677c15e8e990.png)
## Flexbox是什么
Flex是Flexible Box的缩写，意为”弹性布局”，用来为盒状模型提供最大的灵活性。
任何一个容器都可以指定为Flex布
## 基础用法
* 要是使用flex来布局,首先需要在父盒子里面定义`display:flex`(其实就是把父元素变成一个flex容器)

<!--more-->

### 父元素的几个属性
> * justify-content  主轴上的对齐方式
> * align-items      交叉轴上的对齐方式
> * align-content     多根轴线的对齐方式
> * flex-direction    排列方向
> * flex-wrap 是否在一行上显示
> * flex-flow

#### justify-content的值 
* 可以传入5个值,分别是flex-start || flex-end || center || space-between || space-around
* flex-start 是默认值,(左对齐)
* flex-end 右对齐
* center 居中对齐
* space-between 两端对齐
* space-around 让每个Flex项目之间具有相同的空间

```css
ul{justify-content: center}
```
![](http://www.runoob.com/wp-content/uploads/2015/07/c55dfe8e3422458b50e985552ef13ba5.png)

#### aligin-items的值
* flex-start 是默认值,让所有项目从开始边缘(上对齐)
* flex-end 让所有flex项目靠Main-Axis结束边缘（下对齐）
* center 居中对齐
具体使用和justify-content类似
![](http://www.runoob.com/wp-content/uploads/2015/07/2b0c39c7e7a80d5a784c8c2ca63cde17.png)
#### aligin-content 多行的flex容器排列方式
* flex-start 是默认值,让所有项目从开始边缘(左对齐)
* flex-end 让所有flex项目靠Main-Axis结束边缘（右对齐）
* center 居中对齐
具体使用和justify-content类似
#### flex-direction 
* row从左到右排列(默认)
* column从上到下排列
#### flex-wrap 是否在一行显示
* wrap 不在一行显示,换行(默认)
* nowrap 在一行显示不换行
#### flex-flow是flex-direction和flex-wrap两个属性的速记属性
```css
 ul { flex-flow: row wrap; }/*从左到右排列,换行 */
```
### 子元素的几个属性
> flex-grow 放大放大元素比例
> order 定义排列顺序,值越小越靠前,默认0
> flex-shrink 缩放比例,默认:0,不进行缩放
#### flex-grow:<number>,
* 本身定义的数值除以总数值就是项目所占比例,
```css
.item1{
flex-grow: 1;
}
.item2{
flex-grow: 2;
}
.item3{
flex-grow: 1;
}
```
![](http://ww3.sinaimg.cn/large/0060lm7Tly1foyjer9jy0j30i902s0sq.jpg)
* 如果某一个项目属性定了宽,那么其他项目根据剩下的空间进行比例划分
```css
    .item1{
        flex-grow:1;
        order: 3;
    }
    .item2{
        width: 200px;
    }
    .item3{
        flex-grow:1;
        order: 1;
    }
```
![](http://ww3.sinaimg.cn/large/0060lm7Tly1foyjs8nsaqj30ho02m0sq.jpg)
#### order:<number> 
* 排列顺序,数值越小越靠前
```css
    .item1{
        flex-grow:1;
        order: 3;
    }
    .item2{
        flex-grow:2;
        order: 2;
    }
    .item3{
        flex-grow:1;
        order: 1;
    }
```
![](http://ww1.sinaimg.cn/large/0060lm7Tly1foyjmfmmcjj30hs02s3yj.jpg)
#### flex-shrink
* 除了2,其他都进行缩放
```css
.item2{
    flex-shrink:0;
}
```
![](http://ww1.sinaimg.cn/large/0060lm7Tly1foyk0mz3uwj30hv02pq36.jpg)
#### 链接
[理解Flexbox：你需要知道的一切:](https://www.w3cplus.com/css3/understanding-flexbox-everything-you-need-to-know.html)

[Flex 布局语法教程](http://www.runoob.com/w3cnote/flex-grammar.html)