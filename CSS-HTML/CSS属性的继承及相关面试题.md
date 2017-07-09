---
title: CSS属性的继承及相关面试题
date: 2017-06-30 16:56:14
tags:
---
## CSS属性的继承
- 子级元素从父级元素身上继承的一些可继承的css属性

```
<style>
div{color:red;}
</style>
<p>woshiyige[biaoqian</p>
```
- 根据 CSS，子元素从父元素继承属性。看看下面这条规则：
    - body {font-family: Verdana, sans-serif;}
        - 根据上面这条规则，站点的 body 元素将使用 Verdana 字体（假如访问者的系统中存在该字体的话）。
- 继承的权重较小，可被其他选择器的样式覆盖


## 面试题：
- 哪些css样式可以被继承：和文字有关的css样式 和列表有关的css样式
### 总结：
- 1.可继承属性
- 1)可以继承的文本相关属性：
```
<azimuth><border-collapse><border-spacing><caption-side><color><cursor><direction><elevation><empty-cells><font-family><font-size><font-style><font-variant><font-weight><font><letter-spacing><line-height><list-style-image><list-style-position><list-style-type><list-style><orphans><pitch-range><pitch><quotes><richness><speak-header><speaknumeral><speak-punctuation><speak><speechrate><stress><text-align><text-indent><texttransform><visibility><voice-family><volume><whitespace><widows><word-spacing>
```
- 2)可以继承的列表相关属性：
```
<azimuth><border-collapse><border-spacing><caption-side><color><cursor><direction><elevation><empty-cells><font-family><font-size><font-style><font-variant><font-weight><font><letter-spacing><line-height><list-style-image><list-style-position><list-style-type><list-style><orphans><pitch-range><pitch><quotes><richness><speak-header><speaknumeral><speak-punctuation><speak><speechrate><stress><text-align><text-indent><texttransform><visibility><voice-family><volume><whitespace><widows><word-spacing>
```
- 2.不可继承属性
```
<display><margin><border><padding><background><height><min-height><max-height><width><min-width><max-width><overflow><position><left><right><top><bottom><z-index><float><clear><table-layout><vertical-align><page-break-after><page-bread-before>和<unicode-bidi>
```
- 3.所有元素可继承：
- `<visibility>（可见性）和<cursor>(光标)`

- 4.终端块状元素可继承：
- `<text-indent>和<text-align>`


- 5.如果css属性不带有继承性，如何继承父级身上的属性，可以将要继承的属性的属性值写上inherit
```
ul{float:left;}
li{float:inherit;}
```