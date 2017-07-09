---
title: CSS常用选择器
date: 2017-06-30 15:14:52
tags:
---
## CSS选择器
- 因为html和css分离，那么就出现一个问题，如何选择一个元素，将样式添加给这个元素-->css选择器
- 选择器是css属性和html元素的连接桥梁，通过正确的选择器来找到想要操作的元素，添加一定的样式。
- 选择器{}

### 1.语法
选择器{key:value;key:value;}

- 可以批量选择**选择器**名称相同的元素
- 通过选择器类型不同，可以选择不同的html元素


## 2.CSS基础选择器分类

### 1) 标签选择器
- 直接使用元素标签进行选择
    - 例如：`<p></p>`
    - p{color:red;}
- 权重：1
```
<style>
h1{color:red;}
</style>
<h1>标签选择器</h1>
```

### 2) 类选择器
- 将html元素的class标签属性值当作选择器使用，需要在这个属性值前面加一个“.”
- 通过元素的类名，来选择元素，一个元素可以有多个类名，都代表这个元素
- 类名是元素class属性中的属性值，例如
    - <p class='sum'></p>
    - .sum{}
- 一个html元素可以有多个css属性值（可以有多个类名，每一个类名之间用空格隔开）
  类名可以重复使用
- 权重：10
- p.s：类选择器最前方一定要有点
```
<style>
.tytle{color:red;}
</style>
<h1 class="tytle title1">标签选择器</h1>
<h1 class="tytle">标签选择器</h1>
```

### 3) id选择器
- 一个html元素，id属性值只能用一次，id在html中具有唯一性
- 类选择器最前方一定要有#
- 通过元素的id名，来选择元素
- 权重：100
- 类名是元素id属性中的属性值，例如
```
<style>
#tytle{color:red;}
</style>
<h1 id="tytle title1">id选择器</h1>
<h1 id="tytle">错误的，不识别</h1>
```
###总结：
标签选择器相当于人的姓名，类选择器相当于人的名字，id选择器相当于身份证号码。

### 4) 通配符选择器
- 通过*匹配全部html元素，包括根元素
- 一般不使用，因为全部匹配耗性能
- *{}
- 权重<1，可被覆盖
```
*{key:value}

```

### 5) 并集选择器
- 你可以对选择器进行分组，这样，被分组的选择器就可以分享相同的声明。用逗号将需要分组的选择器分开。在下面的例子中，我们对所有的标题元素进行了分组。所有的标题元素都是绿色的。
    - 例如：
```
h1,h2,h3,h4,h5,h6{color:green;}
```

### 6) 属性选择器
- 对带有指定属性的 HTML 元素设置样式，可以为拥有指定属性的 HTML 元素设置样式，而不仅限于 class 和 id 属性。
- 属性选择器：
    - 下面的例子为带有 title 属性的所有元素设置样式：
```
    [title]
        {
        color:red;
        }
```
- 利用标签的属性名和属性值来选择html元素
- 权重：10
- 语法：
- [标签属性名]{}
- [标签属性名=属性值]{}
```
<style>
h1[title]{}交集选择器
标签+属性的权重=11
[type]{}
权重：10
[type=text]{}
权重：10
</style>
<a href="" title="">link</a>
```

### 7)属性和值选择器
- 下面的例子为 title="zfpx" 的所有元素设置样式：
```
    [title=zfpx]
        {
        border:5px solid blue;
        }
```
    - 设置表单的样式
    ```
      input[type="text"]
      {
        width:150px;
        display:block;
        margin-bottom:10px;
        background-color:yellow;
        font-family: Verdana, Arial;
      }
      ```



### 8)分组选择器
作用（应用场景）：同一份css样式，可以一次性的添加给多个不同的html元素
权重：分组选择器将不同的html分为一组，权重计算的时候都是独立计算，不会叠加。
语法：
选择器1，选择器2，选择器3{}
```
.box,li,.p1{color: red}
.box{color:green}
```

### 9)交集选择器
- 两种属性同属一个元素的时候，我们可以使用交集选择器来进行元素的准确选择
    - `<p class='name1 name2' id='id1'></p>`
        - `p.name1{}`
        - `p#id1{}`
        - `.name1.name2{}`
- 组合选择器之间没有任何的符号和空格
- 标签选择器和其他选择器组合的时候，标签选择器要放在前面
- 交集选择器是两个选择器组合在一起，可以是标签和类名，标签和属性选择器，标签和ｉｄ，两个类选择器

- 作用：精确查找元素，增加选择器的权重
```
<style>
h1{} 标签选择器 权重：1
[title]{} 属性选择器 权重：10
[title=zfpx]{} 属性选择器 权重：10
h2[title]{} 交集选择器 权重：11
h2[title=zfpx]{} 交集选择器 权重：11
</style>
<h1 title="zfpx"></h1>
<h2 title="zfpx"></h2>
<style>
p.p1{}  交集选择器  权重：11
</style>
<p class="p1"></p>
<style>
.p1.p2{}  交集选择器  权重：20
</style>
<p class="p1 p2"></p>
```
- 属性选择器在使用的时候，如果一个元素有两个类名，那么是不生效的。例如：
- 属性选择器我们一般不会使用class，因为class可以直接使用类选择器
```
<!--有多少种方法只获取div-->
 /*如果class值有两个，不能这样使用*/
        [class=div1]{}
<div class="div1 p1" id="div2"></div>
<p class="p1"></p>
```
### 10)子集选择器
- 与后代选择器相比，子元素选择器只能选择作为某元素子元素的元素。
- 语法：父级选择器>子级选择器
- 父级选择器是用来确定范围的，
- 子级选择器才是我们要添加样式的那个元素
- 权重：所有选择器之和
- 子级选择器必须是紧邻的父子关系
```
<style>
ul>li{color:red;} 选择ul下的li
权重：2
</style>
<ul>
    <li></li>
</ul>
```

### 11)后代选择器
- html结构：
    ```
        <ol>
            <li><strong>我是斜体字。这是因为 strong 元素位于 li 元素内。</strong>
            </li>
        </ol>
    ```
- 列表中的 strong 元素变为斜体字，而不是通常的粗体字，可以这样定义一个派生选择器：
```
    li strong {
        font-style: italic;
        font-weight: normal;
                }
```
- 在一个根元素的范围内，查找到它的后代元素
- 语法：祖辈选择器 要查找的后代选择器{}
中间用空格连接

- 后代选择器在写的时候尽量控制在３个左右
- 选择器过多浪费性能，不建议使用

```
<style>
.div1 ul span{}
</style>
<div class="div1">
    <ul>
        <li>
            <span>只选择这个span元素</span>
        </li>
    </ul>
    <ol>
        <li>
            <span>wenzdskaldjaslk</span>
        </li>
    </ol>
</div>
<div class="div2">
    <ul>
        <li>
            <span>wenzdskaldjaslk</span>
        </li>
    </ul>
    <ol>
        <li>
            <span>wenzdskaldjaslk</span>
        </li>
    </ol>
</div>
```

### 12)相邻兄弟选择器
- 相邻兄弟选择器可选择紧接在另一元素后的元素，且二者有相同父元素。
    - `h1 + p {margin-top:50px;}`
- 通过各个元素选择弟弟选择器，两个选择器之间用“+”连接
- 语法：哥哥选择器+弟弟选择器{}
- 权重：选择器之和
```
<style>
    .list1+li{color: red;}
    22222变为红色
    .list3+li{color: green;}
    4444变为绿色
    /*li+.list3{}*/
</style>
<ul>
    <li class="list1">11111</li>
    <li>22222</li>
    <li class="list3">33333</li>
    <li>4444</li>
</ul>

```






### 伪类选择器
- 给一个元素添加某种状态
    - 例如：鼠标经过时 获取焦点时 鼠标点击时
- 权重：10
- 1) a标签
- CSS 伪类用于向某些选择器添加特殊的效果
```
<style>
    a:link {color: #FF0000}
    /* 未访问的链接 是默认状态*/
    a:visited {color: #00FF00}
    /* 已访问的链接 鼠标点击后的状态*/
    a:hover {color: #FF00FF}
    /* 鼠标移动到链接上 鼠标经过的状态*/
    a:active {color: #0000FF}
    /* 选定的链接 鼠标点击的状态*/
</style>
<a href="javascript:void (0)">最初形态</a>
<a href="javascript:void 0">赛亚人形态</a>
<a href="javascript:">超级赛亚人形态</a>
```
- 2)input标签
```
<style>
        .input{border: 1px solid gainsboro}
        .input:hover{border-color: gray}
        .input:focus{border-color: blue}
        /*input:focus 鼠标聚焦后的状态，input独有的属性*/
</style>
<input type="text" class="input">
```

## CSS 伪元素
- 通过css代码向指定元素**内**添加假的（html中不存在的）元素


- CSS 伪元素用于向某些选择器设置特殊效果
- 1)before 会出现在div所有内容之前
    - ":before" 伪元素可以在元素的内容前面插入新内容。
    - 下面的例子在每个 `<h1>` 元素前面插入一幅图片：
```
h1:before
  {
  content:'我是一个伪元素';
  }
```
- 2)after 会出现在div所有内容之后
使用伪元素的时候要保证两个前提
- 要有display这个属性
- 要有content这个属性，这个属性的属性值可以为空，但是引号不能少`content:""`
```
<style>
    div{
        width: 300px;
        height: 300px;
        background-color: red;
        }
    div:before{
        display: block;
        content: "我是before";
        font-size: 40px;
        color: white;
               }
    div:after{
        display: block;
        content: "我是aftre";
        font-size: 40px;
        color: blue;
              }
</style>
<div>
    <span>我是span</span>
</div>
网页显示：
<div>
::before
<span>···<span>
::after
</div>
```












