---
layout: post
title: canvas 学习笔记一
description: canvas api 学习
keywords: canvas
date: 2018-05-12 10:48:27
updated:
category:
- html
tags:
- canvas
photos:
---
![](/images/timg8.png)
<!-- more -->

## 参考资料
 * Canvas API - Web APIs | MDN  https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API
 * CanvasRenderingContext2D https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D

## 创建canvas对象
```js
    //创建canvas标签(节点或对象)
    var cans=document.createElement("canvas");
    //设置宽高
    //canvas只接收px单位值，要想canvas自适应宽高可以把canvas挂载到某一自适应节点(父节点宽高自适应)上canvas继承该节点宽高。或者直接把计算过的宽高赋值给canvas
    cans.width=500;
    cans.height=500;
    //挂载到body上
    document.querySelector(body).appendChild(cans);
    //创建一个CanvasRenderingContext2D对象作为2D渲染的上下文(这一步非常重要，后面的操作都是通过ctx来完成的)
    var ctx = cans.getContext("2d");
```

## CanvasRenderingContext2D接口
> CanvasRenderingContext2D 接口用于绘制矩形，文本，图像和其他对象到画布元件。它为canvas元素的绘图表面提供2D渲染上下文。为了得到这个接口的一个对象，调用getContext() canvas element，提供“2d”作为参数

## canvas 坐标系
> canvas 默认情况下 坐标原点位置为最左上角0.0开始 x轴向右增大，y轴向下增大

* [实例1](https://codepen.io/x447618716/pen/aGGQNR?editors=0010): 创建一个距离x轴20px y轴20px 宽度为150px 高度为100px的蓝色边框的矩形
效果展示，请看实例1 https://codepen.io/x447618716/pen/aGGQNR?editors=0010
```js
    //实例1
    ctx.save();
    ctx.beginPath();
    ctx.strokeStyle="blue";
    ctx.rect(20,20,150,100);
    ctx.stroke();
    ctx .restore();
```

> 改变canvas坐标圆点:CanvasRenderingContext2D提供了translate()方法，它接收两个参数x轴坐标 y轴坐标分别用来指定重新映射的圆点位置

* [实例2](https://codepen.io/x447618716/pen/aGGQNR?editors=0010):重新映射圆点的坐标位置到画布中心点，创建一个距离x轴0px y轴0px 宽度为150px 高度为100px的红色边框的矩形
效果展示，请看实例2 https://codepen.io/x447618716/pen/aGGQNR?editors=0010
```js
   //实例2
   ctx.save();
   ctx.beginPath();
   ctx.translate(250,250);
   ctx.strokeStyle="red";
   ctx.rect(0,0,150,100);
   ctx.stroke();
   ctx .restore();
```

## canvas绘制
> CanvasRenderingContext2D提供了多个绘制路劲的方法(我们主要就是用这些方法来绘制各种各样的图形)这边先摘取各别做一些介绍

* beginPath() 起始一条路径，或重置当前路径

> beginPath: 核心的作用是将 不同绘制的形状进行隔离，每次执行此方法，表示重新绘制一个路径,跟之前的绘制的墨迹可以进行分开样式设置和管理。

* closePath() 创建从当前点回到起始点的路径
* moveTo()把路径移动到画布中的指定点，不创建线条
* lineTo() 添加一个新点，然后在画布中创建从该点到最后指定点的线条
* stroke() 绘制已定义的路径



* [实例3](https://codepen.io/x447618716/pen/aGGQNR?editors=0010):  通过提供的API 绘制两个黑色边框的矩形
* [实例4](https://codepen.io/x447618716/pen/aGGQNR?editors=0010): 绘制两个绿色边框的矩形  当不使用beginPath() 会发现两个矩形颜色略有不同 那是因为两个绿色边框绘制的墨迹重叠在一起了，导致一深一浅（把实例4的颜色换成一黄一绿就比较明显的看出来）
因此在每绘制一个图形都建议套用套用如下代码

```js
   ctx.save();
   ctx.beginPath();

   ````绘制图形逻辑

   ctx.restore();
```
效果展示，请看实例3，实例4 https://codepen.io/x447618716/pen/aGGQNR?editors=0010
```js
  //实例3
  ctx.save();
  ctx.beginPath();
  ctx.strokeStyle="black";
  ctx.moveTo(20,200);
  ctx.lineTo(170,200)
  ctx.lineTo(170,300)
  ctx.lineTo(20,300)
  ctx.closePath();
  ctx.stroke();
  ctx.restore();

  ctx.save();
  ctx.beginPath();
  ctx.strokeStyle="black";
  ctx.moveTo(20,350);
  ctx.lineTo(170,350);
  ctx.lineTo(170,450)
  ctx.lineTo(20,450)
  ctx.closePath();
  ctx.stroke();
  ctx.restore();

  //实例4
  ctx.save();
  ctx.strokeStyle="green";
  //ctx.strokeStyle="yellow";
  ctx.rect(250,20,150,100);
  ctx.stroke();
  ctx.restore();

  ctx.save();
  ctx.strokeStyle="yellow";
  //ctx.strokeStyle="green";
  ctx.rect(250,140,150,100);
  ctx.stroke();
  ctx.restore();
```

* 绘制了这么多图形不知发现没有我们设置的颜色与绘制出来的颜色好像变淡了
嘿嘿，解决方法也很简单那就是在已绘制的路径上在绘制一遍具体做法查看[canvas2](https://codepen.io/x447618716/pen/aGGQNR?editors=0010)

## canvas作用域
* CanvasRenderingContext2D提供了两个方法
 * save() 保存当前环境
 * restore() 返回之前保存过的路径状态和属性

>顾名思义所谓作用域就好比一个密封箱子，不管箱子里面有什么难闻的气味或什么只有在箱子里面才能闻到外面依旧空气清新


```js
   //实例5
   //只要在其下的绘图 透明度都会变成0.2
   ctx.globalAlpha=0.2;

   ctx.save();
   ctx.beginPath();
   //如果把它写到save() restore()它有只会作用于当前绘图环境
   ctx.globalAlpha=0.2;
   ctx.translate(250,250);
   ctx.strokeStyle="orange";
   ctx.rect(0,150,150,100);
   ctx.stroke();
   ctx.stroke();
   ctx.restore();
```

