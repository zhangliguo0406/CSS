# css选择器种类和兼容性总结大全
|名称|举例|描述|详细|权重|ie6-7|ie8|ie9+|其他|
|----|----|----|----|----|----|----|----|----|
|标签选择器|p{}|直接使用元素标签进行选择||1|yes|yes|yes||
|类选择器|.sum{}|类选择器最前方一定要有点|通过元素的类名，来选择元素，一个元素可以有多个类名，都代表这个元素,类名是元素class属性中的属性值，例如`<p class='sum'></p>`|10|yes|yes|yes||
|id选择器|#tytle{color:red;}|id在html中具有唯一性,这个属性值前面加一个“#”|一个html元素，id属性值只能用一次|100|yes|yes|yes||
|通配符选择器|*{key:value}|匹配全部html元素|一般不使用，因为全部匹配耗性能|0<通配符选择器<1|yes|yes|yes|yes||
|(标签)属性选择器|[type]或[type=text]|[标签属性名]{}或[标签属性名=属性值]{}|利用标签的属性名和属性值来选择html元素|10|yes|yes|yes|属性选择器在使用的时候，如果一个元素有两个类名，那么是不生效的|
|分组选择器|.box,li,.p1{color: red};|选择器1，选择器2，选择器3{}|同一份css样式，可以一次性的添加给多个不同的html元素|分组选择器将不同的html分为一组，权重计算的时候都是独立计算，不会叠加。|yes|yes|yes||
|交集选择器|h2[title]{}||两种选择器同属于一个元素的时候，我们可以使用交集选择器来进行元素的准确选择|所有组合选择器权重之和|yes|yes|yes|作用：精确查找元素，增加选择器的权重|
|子级选择器|ul>li{color:red;}|父级选择器>子级选择器{}|存在包含关系的元素选择，通过父级确定选择子级|所有选择器之和|yes|yes|yes|子级选择器必须是紧邻的父子关系|
|后代选择器(派生选择器)|.div1 ul span{}|祖辈选择器 要查找的后代选择器{},中间用空格连接|后代选择器在写的时候尽量控制在３个左右||yes|yes|yes|在一个根元素的范围内，查找到它的后代元素，选择器过多浪费性能，不建议使用|
|相邻兄弟选择器|.list1+li{color: red;}|哥哥选择器+弟弟选择器{}|通过各个元素选择弟弟选择器，两个选择器之间用“+”连接|选择器之和|yes|yes|yes||
|伪类选择器|`a:hover{color: red}鼠标经过的状态,或a:link{color: blue}默认状态,或a：active{color: green}鼠标点击的状态,或a:visited{color: blanchedalmond}鼠标点击后的状态`|||10|yes|yes|yes|.input:focus{border-color: blue};input:focus 鼠标聚焦后的状态，input独有的属性|
|伪元素| div:before{}；或div:after{}|通过css代码向指定元素**内**添加假的（html中不存在的）元素|before 会出现在div所有内容之前，after 会出现在div所有内容之后||no|yes|yes|使用伪元素的时候要保证两个前提：1.要有display这个属性2.要有content这个属性，这个属性的属性值可以为空，但是引号不能少`content:""`|
||visited||||security issue|yes|yes|security issue|
||c|s|s|3|选|择|器|
|属性选择器|E[attr~=value]{}||指定属性名,并且具有属性值,此属性值是一个此列表(类名),并且以空格隔开,其中词列表中包含了一个value词,并且等号前的~不能省略.|||
||E[attr^=value]{}||^ 表示以谁为开头的,value可以是首字母或者类名|必须是第一个类名|||
||E[attr$=value]{}||$ 表示以谁为结尾,value可以是末尾字母或者类名|必须是最后一个类名|||
||E[attr|=value]{}|如果只有一个类名,没有"-",也可以选中|value必须后面带"-"，value必须是第一个类名|||
|伪类选择器|
|1.|.dome p:nth-child(3){background: red;}选择dome下的第三个p标签为背景色红色||||no|no|yes||
|2.|.dome p:first-child{background: yellow;}选择dome下的第一个p标签为背景色黄色||||no|almost|yes||
|3.|.dome p:last-child{background: black;}选择dome下的最后一个p标签为背景色黑色||伪类选择器是针对列表或者很多同级的标签使用,img下是没有效果的也用不到伪类选择器||no|no|yes||
|4.|.dome p:nth-child(nlength){}；选择dome下所有的p标签||||no|no|yes||
|5.|.dome p:nth-child(2n){}；选择dome下的所有偶数个的p标签||||no|no|yes||
|6.| .dome p:nth-child(3n)选择dome下的所有3的倍数的p标签||||no|no|yes||
|7.|.dome p:nth-child(n+length)|从第length个开始改变,包括第length个(n是从0开始取值的)|选择大于length后面的元素||no|no|yes||
|8.|.dome p:nth-child(-n+length)|包括length，length是从0开始的|选择小于length前面的元素及length元素||no|no|yes||
|9.|p:nth-last-child(3) |选择倒数第三个元素|||no|no|yes||
|10.|p:nth-child(n)|从大盒子的第一个元素开始|nth-child选择同级元素||no|no|yes||
|11.|p:nth-of-type(n)|从大盒子的第一个p元素开始|nth-of-type 选择指定的元素||no|no|yes||
|12.|p:nth-last-of-type(n)|倒数第n个|在同级元素中||no|no|yes||
|13.|p:first-of-type{}|同类型的第一个|选择一个上级元素下的同类子元素||no|no|yes||
|14.|p:last-of-type{}|同类型的最后一个|||no|no|yes||
|15.|p:only-child{} |在父元素中,里面的子元素是唯一的|||no|no|yes||
|16.|p:only-of-type{} |在父元素中,里面有很多的子元素,但是有一个子元素是唯一的|||no|no|yes||
|空标签|p:empty{display:none;}|empty 隐藏空标签|||no|no|yes||
|否定选择器|not input:not([type=submit]){}||||no|yes|yes||
|根元素|root :root{} |选择文档的根元素|||no|no|yes||
|目标元素|:target{} |选择器可用于选取当前活动的目标元素|||no|no|no|





