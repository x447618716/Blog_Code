---
layout: post
title: 文件拖拽
description: 通过鼠标选中拖拽文件到页面指定位置
keywords: 文件拖拽
date: 2018-02-24 15:07:49
updated:
category:
- js
tags:
- 鼠标拖拽
- 文件拖拽
photos:
---
![](/images/timg7.png)
<!-- more -->
## 准备工作
## JS拖动事件
* 在拖动目标上触发事件 (源元素):
  * ondragstart - 用户开始拖动元素时触发
  * ondrag - 元素正在拖动时触发
  * ondragend - 用户完成元素拖动后触发
* 释放目标时触发的事件:
  * ondragenter - 当被鼠标拖动的对象进入其容器范围内时触发此事件
  * ondragover - 当某被拖动的对象在另一对象容器范围内拖动时触发此事件
  * ondragleave - 当被鼠标拖动的对象离开其容器范围内时触发此事件
  * ondrop - 在一个拖动过程中，释放鼠标键时触发此事件

** 详细事件说明可参考web技术文档-->事件类型-->[拖放事件](https://developer.mozilla.org/en-US/docs/Web/Events/dragstart) **

## file对象[FileReader对象]
FileReader主要用于将文件内容读入内存，通过一系列异步接口，可以在主线程中访问本地文件。
> 使用FileReader对象，web应用程序可以异步的读取存储在用户计算机上的文件(或者原始数据缓冲)内容，可以使用File对象或者Blob对象来指定所要处理的文件或数据。

## 创建实例
> var reader = new FileReader();

## 方法
|方法定义|描述|
|:---:|:---:|
|abort():void|终止文件读取操作|
|readAsArrayBuffer(file):void|异步按字节读取文件内容，结果用ArrayBuffer对象表示|
|readAsBinaryString(file):void|异步按字节读取文件内容，结果为文件的二进制串|
|readAsDataURL(file):void|异步读取文件内容，结果用data:url的字符串形式表示|
|readAsText(file,encoding):void|异步按字符读取文件内容，结果用字符串形式表示|

## 事件
|事件名称|描述|
|:---:|:---:|
|onabort|当读取操作被中止时调用|
|onerror|当读取操作发生错误时调用|
|onload|当读取操作成功完成时调用|
|onloadend|当读取操作完成时调用,不管是成功还是失败|
|onloadstart|当读取操作将要开始之前调用|
|onprogress|在读取数据过程中周期性调用|

** 详细事件说明可参考web技术文档--> Web API 接口-->[FileReader](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader) **

## 直接上代码
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>文件拖拽+图片预览</title>
    <style type="text/css">
        .dragbox{
            width: 300px;
            height: 300px;
            margin: 20px;
            border: 3px dashed #e6e6e6;
        }
        .range{
            margin: 75px auto;
            width: 150px;
            height: 150px;
            display: block;
            background-repeat: no-repeat;
            background-position: center;
            background-size: cover;
            background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFgAAABLCAIAAAB7tddWAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyRpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoTWFjaW50b3NoKSIgeG1wTU06SW5zdGFuY2VJRD0ieG1wLmlpZDo1Q0VBNzA0MjEyMDUxMUUzODk2Q0JFM0Q1RjE4QkExQyIgeG1wTU06RG9jdW1lbnRJRD0ieG1wLmRpZDo1Q0VBNzA0MzEyMDUxMUUzODk2Q0JFM0Q1RjE4QkExQyI+IDx4bXBNTTpEZXJpdmVkRnJvbSBzdFJlZjppbnN0YW5jZUlEPSJ4bXAuaWlkOjAzNDA2MkY1MTIwMzExRTM4OTZDQkUzRDVGMThCQTFDIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOjAzNDA2MkY2MTIwMzExRTM4OTZDQkUzRDVGMThCQTFDIi8+IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY+IDwveDp4bXBtZXRhPiA8P3hwYWNrZXQgZW5kPSJyIj8+K6izdgAAAvpJREFUeNrsnFmPqkAQhWmX667gEp9c/v+/MkSDG+4LrvdcSYgRbw/0ALZQ9WBUJOn+uqvqHGCG3e93hUJRUoSAQBAIAkEgCASBIBAE4neRicEcII51Xb/dbnjPGOt0OqlUKok7ApN3jIKwY6DUIBAEgkAQCALho/X47TeXy8U0TcuyrtdrZKPs9/v2m8FgINYgf9QX/gTV+Xw2DCNKBJKmxmKxsAVc0kEcDgfyGq8CNp/Pa5qWy+WiHG6v13v7/XPt6Ha7Al5D3HQ1Go1sNkvtU8lkMsmtESSoCASBSFqEW/DQ0tbr9W63O51OKK6FQkFV1XQ6nSwQ0OOTyQSvjknZbDaA0mq1QCQafSFFasxmM4eCE1Do0+lUQrcSFggsPhzq20NgsVqtkpIax+MxMs+C/aXruvMxaonND75J9W5hUWWxuYAVdRfTg8EplUphGJywQPAFuBd5Dlhw/aDwwgVtCDgCdzph1QisG+dosVjkn44WYxjGC4XnvBuNRtvt9gtA2Hv47SGsZKVS4ef8eDzG4vMVCrpSgEU3xPbZbDar1erLl1AQ7XabU8xAAXvB3XffBnIHwkR2QcUYq9fr5XIZOxkTg6BEkeNLKdQF7AWPFBy1AoUmu8RG/HmE91nxM+J/ORIr07VcLvf7feCt+stAQGIBRNJtOJolDAhdj/hXGj5+u+TzIKAF+MbkK00XFta2BhDRUE0/9gv8Elogbu4TBW8+nyPhHSeuaVqtVuNQC6TzyQUCXsg0TbfyAxfIKogr9ynP1GJyYQZ57qbg7AuIRfclKZwSlDqWBQSmxM9zFALYh+fFBwJJSkNgqeFxSrAPw+EQ9QJew7Is2Sj8FgSW2nu1gylYPkKRMsRTA+4IcjA2fxsnDkLOq/IfACFP54uP1yAQBIJAEIh4gWCPkHk+GJ7AjU/fICJ+qlIghEfoDwQMtRjvyLYDRih4rsDT+bBM9tP5kuhrzN++e6SqqvCdYUb/SIO6BoEgEASCQBAIAkEgCEQg8VeAAQAB1bbO2qoeewAAAABJRU5ErkJggg==");
        }

        #preview img{
            width: 200px;
            height: 200px;
        }
    </style>
</head>
<body>
<div id="dragbox" class="dragbox">
    <label for="file" class="range"></label>
    <input type="file" id="file" style="display: none">
</div>
<div id="preview"></div>

<script type="text/javascript">

    //文件拖拽事件
    var dropbox = document.getElementsByClassName("dragbox");
    var preview = document.getElementById("preview");

    dropbox[0].addEventListener("dragenter", function(e){
        e.stopPropagation();
        e.preventDefault();
    }, false);

    dropbox[0].addEventListener("dragover", function(e){
        e.stopPropagation();
        e.preventDefault();
    }, false);

    dropbox[0].addEventListener("drop", function(e){
        e.stopPropagation();
        e.preventDefault();

        var dt = e.dataTransfer;
        var files = dt.files;

        update(files);

    }, false);


    //input选择图片
    var file = document.getElementById("file");
    file.addEventListener("change",function () {
        var files = this.files;
        if (!!files) {
            update(files);
        }
    });


    function update(files) {
        for (var i = 0; i < files.length; i++) {
            var file = files[i];
            var imageType = /^image\//;

            if ( !imageType.test(file.type) ) {
                continue;
            }

            // 填充选择的图片到展示区
            var img = document.createElement("img");
            img.classList.add("obj");
            preview.appendChild(img);

            // 读取File对象中的内容
            var reader = new FileReader();
            reader.readAsDataURL(file);
            reader.onload = (function(aImg) {
                return function(e) {
                    aImg.src = e.target.result;
                };
            })(img);
        }
    }
</script>
</body>
</html>

```

## 实例预览
[点击+拖拽上传前预览](https://x447618716.github.io/PicturePreview/fileDrag.html)
