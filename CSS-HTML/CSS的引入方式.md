---
title: CSS的引入方式
date: 2017-06-30 15:27:20
tags:
---
## css如何在html中使用（html引入css的四种方法）
- 1. 行内式：直接写在标签内，通过标签属性style引入
    - 媒介：style属性`<style type="text/css">选择器{}</style>`
```
<div style="css属性名:属性值；"></div>
<img style="css属性名:属性值；"alt="">
```
- css想要生效，html中必须有这个元素才可以

- 2. 内嵌式（内联式）:将css代码写在style元素内，通过css选择器选择html元素，将css样式添加个这个元素
    - 媒介：style标签+选择器
- style这个元素一般放在head元素内
    - style元素：盛装css样式
```
<style>
div{height:100px;}
</style>

<div></div>
```
- 3. 外联式（外链式）：将css代码单独放置在一个css文件中，再通过link标签将这个css文件引入到html文件中
    - 媒介：link标签+选择器
```
<link rel="stylesheet" herf="css文件链接地址" type="text/css">
```
- css这个文件中不能出现标签

- 4. 导入式：都是引入一个单独的css文件
    - 媒介：@import"css文件链接地址";
        - 当有多个css文件的时候，可以使用导入式先导入到一个css文件中，再用外链式link外链进html文件
    - @import"css文件链接地址";既不是html标签，也不是css属性，他是一条声明语句
    - 这条语句必须写在style元素内,或者css文件内
    - 这条语句必须在所在文件内的第一行


## 外链式和导入式的差别：
- link和@import虽然都是引入外部的css文件，但是他们是由天差地别的区别的
    - 1) link是html标签，@import完全是css提供的方式，要写在css文件或者style标签中。
    - 2) 他们的加载顺序也是有区别的，当一个页面被加载的时候，link引用的css文件会被同时加载，而@import引入的css文件会等页面全部下载完后再加载。
    - 3) 当使用javascript控制DOM去改变css样式的时候，只能使用link标签，因为import是不能被DOM控制的。

### 在工作中常用的引入方式是外链式
- 四种引入方式的权重（一个html元素最终加载的css样式是谁决定的）
    - 有行内式的时候，听行内的
    - 在选择器相同的情况下，谁最后加载就听谁的

- 外链式和内嵌式一般都放在head元素内

# CSS层叠样式表
- css的作用：
    - 给html文档添加静态或者动态的样式
- css和html如何融合到一起
- 在css文件中如何选择一个html元素，将样式添加给这个元素