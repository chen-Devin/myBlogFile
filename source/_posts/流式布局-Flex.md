---
title: 流式布局-Flex
date: 2017-09-20 17:22:51
tags: 布局
---

#### flex布局可以简便，完整，响应式地实现各种页面布局，目前，他已经得到所有浏览器的支持。

	Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。
		任何容器都可以用flex布局 设置 display：flex;(行内元素也可以设置flex布局，display：inline-flex)

	注意：设为 Flex 布局以后，子元素的float、clear和vertical-align属性将失效。


<!-- more -->

## 基本概念
	flex布局元素称为flex容器，默认存在两根轴，水平的主轴(main axis)和垂直的交叉轴(cross axis)，
		主轴的开始位置叫做main start 结束位置叫做 main end；
		交叉轴的开始位置叫做cross start 结束位置叫做 cross end;

## 容器的属性
> flex-direction
> 
> flex-wrap
> 
> flex-flow
> 
> justify-content
> 
> align-items
> 
> align-content
### flex-direction:决定主轴的方向（项目的排列方式）
有四个值：
>row（默认值）：主轴为水平方向，起点在左端。
>
>row-reverse：主轴为水平方向，起点在右端。
>
>column：主轴为垂直方向，起点在上沿。
>
>column-reverse：主轴为垂直方向，起点在下沿。

### flex-wrap：默认情况下，项目都排在轴线上。flex-wrap属性定义，如果一条轴线排不下，如何换行。
 有三个值：
> nowrap(默认值)：不换行；
> 
> wrap:换行，第一行在上方；
> 
> wrap-reverse:换行，第一行在下方；
> 