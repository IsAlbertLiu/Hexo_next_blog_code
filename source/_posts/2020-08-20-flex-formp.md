---
title: 在小程序中使用flex布局
tags: 小程序
date: 2020-08-20 
categories: 
- web前端
---


#### 1. 何为布局

布局就是用代码按照设计图的样式实现。布局是非常重要的技能，网页开发人员应该精通布局.
<!-- more -->
在小程序中 view 标签相当于 html 里面的 div 都是一个块级元素。

行内元素（inline）是不能设置宽和高的。但是（inline-block）元素可以。

#### 2. flex 布局

flex （flexible） 弹性盒子。

##### 2.1 flex 消除了 item 的块状特性

使用 flex 可以实现三个元素在一行。当一个容器里面有很多的子元素时，给这个父容器添加 flex 属性，其子元素的块级元素的特征就会消失。子元素就会默认排列在一行中。

##### 2.2 flex-direction 的应用

当给容器设置了 flex 属性的时候，它的子元素的 block 属性就会失去作用，就算给子元素设置block 属性也是起不了作用的。

 ```css
.container{
    display: flex;
    flex-direction: column;
}
 ```

给父元素添加 `flex-direction: column;` 属性，其子元素就会采用纵向排列.`flex-direction` 的默认值是 `row`

##### 2.3 reverse 倒序排布

```css
.container{
    display: flex;
    flex-direction: column-reverse;
}
```

`flex-direction` 的四个常用取值：

1. `row`
2. `column`
3. `row-reverse`
4. `column-reverse`


使用 flex 之后，容器的高度是自适应的，其会根据容器的内部元素的高度而改变。

总结：对于 view 这个组件，它的宽度默认是 100% ，高度通常是自适应的。对于 reverse 倒序，不仅仅元素排列的顺序会发生改变，其对齐的方向也会改变。

##### 2.4 justify-content属性

对齐方向: `justify-content`
常用属性：

```css
.container{
    display: flex;
    flex-direction: row;
    /*开始的位置对齐*/
    justify-content: flex-end;
    /*结束的位置对齐*/
    justify-content: flex-start;
    /*居中对齐*/
    justify-content: center;
    /*平均分布：两侧对齐，中间平均分布*/
    justify-content: space-between;
    /*等距分布：对于每个子元素，他们两侧的距离均相等*/
    justify-content: space-around;
}
```

##### 2.5 主轴与交叉轴

flex 里面有两个轴：主轴和交叉轴。

实现元素水平方向和垂直方向上面都居中：

```css
.container{
    display: flex;
    justify-content: center;
    align-items: center;
}
```

主轴和交叉轴是可以自定义的：通过 `flex-direction` 属性进行定义。`justify-content` 属性设置在主轴上面的排列方式 `align-items` 属性设置在交叉轴的排列方式。

##### 2.6 baseline 与 stretch

`align-items: stretch;` 在没有设置item 的高度的时候，将 `align-items:` 的属性值设置为 stretch 的时候，item 会充满父元素。

`align-items: baseline;`baseline 的意思是，让 items 元素按照第一个元素里面的文字对齐。

##### 2.7 flex-wrap 与消除间距

`flex-wrap` 属性是设置换行。
当我们给设置了 flex 属性的容器的子元素设置了宽度之后，就算子元素的总宽度超过的容器的宽度，flex 也不会让他们自动换行。
假如我们需要那些子元素换行的话，就需要用到 `flex-wrap` 属性.
`flex-wrap` 常用属性值：

```css
    /* 换行，*/
    flex-wrap: wrap;
    /*不换行，默认状态下的取值*/
    flex-wrap: nowrap;
    /*颠倒换行*/
    flex-wrap: wrap-reverse;
```

当容器的高度过多时，被换行的元素的上下间距会平分。如果不需要平分间距的话，将容器的高度设置一下即可.



