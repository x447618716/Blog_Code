---
layout: post
title: IE条件注释详解
description: IE条件注释
keywords: IE,条件注释
date: 2017-07-13 16:12:29
updated:
category: Html
tags:
- IE条件注释
photos:
---
![](/images/timg5.jpg)
<!-- more -->
## 只有IE才能识别
```javascript
<!--[if IE]>
 <link type="text/css" rel="stylesheet" href="test.css" />
<![endif]-->
```
因为只有IE5以上的版本才开始支持IE条件注释，所有“只有IE”才能识别的意思是“只有IE5版本以上”才能识别。
## 只有特定版本才能识别
```javascript
<!--[if IE 8]> 
<link type="text/css" rel="stylesheet" href="test.css" />   
<![endif]-->
```
识别特定的IE版本，高了或者低了都不可以。上例只有IE8才能识别。
## 只有不是特定版本的才能识别
```javascript
<!--[if !IE 7]> 
<link type="text/css" rel="stylesheet" href="test.css" />   
<![endif]-->
```
上例中特定IE7版本不能识别，其他版本都能识别，当然要在IE5以上。
## 只有高于特定版本才能识别
```javascript
<!--[if gt IE 7]> 
<link type="text/css" rel="stylesheet" href="test.css" />   
<![endif]-->
```
上例中只有高于IE7的版本才能识别。IE7无法识别。
## 等于或者高于特定版本才能识别
```javascript
<!--[if gte IE 7]> 
<link type="text/css" rel="stylesheet" href="my.css" />   
<![endif]-->
```
上例中IE7和更高的版本都能识别。
## 只有低于特定版本的才能识别
```javascript
<!--[if lt IE 7]> 
<link type="text/css" rel="stylesheet" href="my.css" />   
<![endif]-->
```
上例中只有低于IE7的版本才能识别，IE7无法识别。
## 等于或者低于特定版本的才能识别
```javascript
<!--[if lte IE 7]> 
<link type="text/css" rel="stylesheet" href="my.css" />   
<![endif]-->
```
上例中IE7和更低的版本可以识别。
## 关键词解释
lt ：就是Less than的简写，也就是小于的意思。
lte ：就是Less than or equal to的简写，也就是小于或等于的意思。
gt ：就是Greater than的简写，也就是大于的意思。
gte：就是Greater than or equal to的简写，也就是大于或等于的意思。
!：就是不等于的意思，跟javascript里的不等于判断符相同。
## 特别提示
条件注释只有在IE浏览器下才能执行，这个代码在非IE浏览下被当做注释视而不见。