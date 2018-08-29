---
layout: post
title: 根据身份证省市区联动
description: 省市区三联
keywords: 身份证省市区三联
date: 2017-07-16 15:29:04
updated:
category: Html
tags:
- 省市区三联
photos:
---
![](/images/timg.jpg)
<!-- more -->
直接上代码:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>根据身份证号自动关联省市区</title>
    <script src="https://code.jquery.com/jquery-1.12.4.min.js"></script>
    <script src="distpicker.data.min.js"></script>
    <script src="distpicker.min.js"></script>
    <link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css"
</head>
<body>
<div style="margin: 0 auto; text-align: center;">
    <form class="form-inline">
        <div class="form-group">
        <input type="text" id="IDcard"  class="form-control" placeholder="请输入身份证号" oninput="getIdcard()" >
        </div>
        <div id="distpicker">
            <div class="form-group">
                <select class="form-control" id="province1"></select>
            </div>
            <div class="form-group">
                <select class="form-control" id="city1"></select>
            </div>
            <div class="form-group">
                <select class="form-control" id="district1"></select>
            </div>
        </div>
    </form>
</div>
<script>
    $(function () {
        $("#distpicker").distpicker({autoSelect: false});
    })

    function getIdcard(){
        var textlength = document.getElementById("IDcard").value.length;
        var newValue=document.getElementById("IDcard").value.replace(/\uD83C[\uDF00-\uDFFF]|\uD83D[\uDC00-\uDE4F]/g, "").toUpperCase();
        $("#IDcard").val(newValue);
        if (textlength >= 6) {
            var text = document.getElementById("IDcard").value;
            var number = text.substr(0, 6);//区或县
            var number2 = number.substr(0, 2) + "0000";//省
            var number3 = number.substr(0, 4) + "00";//市
            var texts;
            var textsh;
            var textq;
            $("#province1").find("option").each(
                function(index, el) {
                    if ($("#province1").find("option").eq(index).data(
                            'code') === Number(number2)) {
                        index2 = index;
                        texts = this.value;
                        $('#province1').trigger("change");
                    }
                    ;
                })

            $("#city1").find("option").each(
                function(index, el) {
                    if ($("#city1").find("option").eq(index).data(
                            'code') === Number(number3)) {
                        index3 = index;
                        textsh = this.value;
                        $('#city1').trigger("change");
                    }
                    ;
                })
            $("#district1").find("option").each(
                function(index, el) {
                    if ($("#district1").find("option").eq(index).data(
                            'code') === Number(number)) {
                        index4 = index;
                        textq = this.value;
                        $('#district1').trigger("change");
                    }
                    ;
                })
            if (textsh === undefined || textq === undefined) {
                $("#text").text("没有查询到户籍所在地，请选择！");
            } else {
                $("#text").text(texts + textsh + textq);
            }

        }else if(textlength==0){
            $("#province1").get(0).selectedIndex=0;
            $("#city1").get(0).selectedIndex=0;
            $("#district1").get(0).selectedIndex=0;
        }
    }
    var index2;
    var index3;
    var index4;
    var e;
    var f;
    var g;
    $("#province1").change(function() {
        var a = $("#province1").get(0).selectedIndex;
        var b = (a === 0) ? index2 : a;
        e = $("#province1").get(0).options[b].value;
        $("#province1").get(0).selectedIndex = b;
    })
    $("#city1").change(function() {
        var a = $("#city1").get(0).selectedIndex;
        var b = (a === 0) ? index3 : a;
        f = $("#city1").get(0).options[b].value;
        $("#city1").get(0).selectedIndex = b;
    })
    $("#district1").change(function() {
        var a = $("#district1").get(0).selectedIndex;
        var b = (a === 0) ? index4 : a;
        g = $("#district1").get(0).options[b].value;
        $("#district1").get(0).selectedIndex = b;
        $("#text").text(e + f + g);
    })
</script>
</body>
</html>
```
该实例引用[distpicker](https://github.com/fengyuanchen/distpicker)三联组件，github：https://github.com/fengyuanchen/distpicker
因为该组件没有提供**身份证**联动的实例，特此添加一些方法。
身份证联动省市区演示：https://x447618716.github.io/Triad_assembly/