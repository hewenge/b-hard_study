######Head first HTML
元素 标签 属性 内容，所有的一切其实都是为了表示内容，属性是修饰标签的。
元素分为void元素和非void元素，即有内容和无内容元素。<br> <image>为void元素
li  list item
ol  ordered list
ul  unordered list  无序列表
***问题：ol是块元素还是内联元素,li呢？***
***回答：参考是否有换行,ol和li都有换行，则都是块元素***
***ol或者ul元素内部只能包含li元素,其它元素不可以***

id：唯一标识元素的方法
用id链接到元素
<a href="index.html#chai">链接到index.html id为chai元素中</a>
<a href="#chai">链接到网页 id为chai中</a>

HTML提供结构，CSS提供表现
一旦把image元素放置到a元素中，浏览器就会把这个图像当作一个可点击的链接。
image实际上是一个内联元素

`<style>
    h1,p,h2 {color: maroon}  字体颜色 
    规则选择器
    h1 {border-bottom: 1px solid black;}
</style>`

link元素是链接外部样式表
CSS规则，父元素继承，但并不是所有的样式都继承，比如方框什么的就不继承

CSS类  .GREEN  
p.GREEN  (规则特定，就是指GREEN类中的P段落采用的样式)

font-family 字体系列
font-size   字体大小
color       字体颜色
font-weight 字体粗细
text-decoration 文本装饰（上划线 下划线 删除线）
font-style  字体风格，比如italic

@font-face 建立新字体的规则（内置的CSS规则）
@import允许导入其它的CSS文件
@medis允许创建特定于某些媒体类型的规则

制定字体大小
px % em, 其中% em都是相对父元素的百分数
或则用关键字，比如small medium

######如何选择字体大小
1. 选择一个关键字（small或者medium），指定它作为body规则中的字体大小，这相当于页面的默认字体大小。
2. 使用em或者百分比，相当于body字体大小指定其它字体大小。

######盒模型
1. 内容 内边距 边框 外边距
2. 内边距 外边距是透明的，本身是没有颜色和装饰。但由于是透明的，所以呈现背景颜色或者背景头像
3. 元素的背景颜色会延伸到内边距下面，但不会延申到外边距。

background-image background-position background-repeat 
border-style
border-width
border-color
border-radis

p#footer {
    color: red;
} // 这会选择一个id为'footer'的<p>元素
类一般是用于一组，id用于元素的唯一
要在CSS中创建一个类，并选择这个类中的一个元素，可以编写一个类选择器
p.greentea {
    color: green
}
// 选择器会选择greentea类中的所有段落
使greentea类中的一个段落中的所有文本为绿色

CSS子孙选择器：
#elixirs h2 表示选择的<h2>元素可以是elixirs的所有子孙
#elixirs>h2 直接孩字  只有当<h2>是一个id为"elixirs" 的元素的直接孩字时，才会选择这个<h2>

 标签选择器：
 h1,p,h2 (逗号)

媒体查询：
`<link href="lounge-mobile.css" ref="stylesheet" media="screen and (max-device-width: 480px)">`
也可以直接在CSS中使用@media 媒体查询
最佳实践：用link元素来指定不同的样式表

width属性只制定内容区的宽度，整个盒子的宽度还需要包括左右内边距，边框以及左右外边距的宽度

text-align：适用于对任何类型的内联元素对齐。且 text-align属性只能在块元素上设置，如何直接在内联元素上(如img)上使用，则不起任何作用。

line-height:行高，属性有一个特殊，如果使用数1，就表示elixirs <div> 中的各个元素的行高是其自己字体大小的1倍，而不是elixirs<div>字体大小的一倍。

div是逻辑块，是一个块元素
span：创建内联字符和元素的逻辑分组

如果强调某些文字，可以使用em 
如果强调一个重点，可以使用strong

伪类：你可以对伪类制定样式，但是没有人在HTML中真正输入这些类。实质是浏览器在后台像这些类中增加或者删除元素
a:link
a:visited
a:hover
(伪类最重要的是':')

##### 布局和定位
1. 流：沿着元素流逐个的显示所遇到的元素,它会在每个块元素之间增加一个换行。即从上往下流。
内联元素：在水平上会相互挨着，总体上会左上方流向右下方。
2. 默认的图像是作为内联元素显示，并且支持外边距、内边距、边框设置。
3. 浏览器上下放置两个块元素时，它会把他们共同的外边距折叠在一起，折叠的外边距高度就是最大的外边距高度。
4. float属性首先尽可能远的向左或者向右浮动一个元素，然后它下面的所有内容会绕流这个元素。
5. 如何浮动一个元素
   1. 指定一个标识
   2. 指定一个高度
   3. 现在增加float属性 float:right
6. 首先要记住的是边栏浮在页面上，主内容区在它的下面扩展。（P526）
7. clear属性：当元素流入页面时，在这个元素的左边、右边或者两边不允许有浮动内容。clear:right or clear:left
8. 能不能把浮动元素想成是被块元素忽略的元素，但是内联元素知道他们在哪里，这个考虑是对的。但有一个例外，对一个块元素设置clear属性时，这回导致块元素下移，直到它右边，左边或两边没有浮动元素挨着它。
9. 冻结布局：与流体布局相对的，当用户调整屏幕时，冻结布局会锁定元素，让它们冻结在页面上，这样这些元素根本不能移动。做法就是将整个页面的宽度固定。
10. 凝胶布局：凝胶布局会锁定页面中内容区的宽度，不过会将浏览器居中。外边距为auto时，浏览器会确定正确的外边距是多少，另外还会确保左右外边距相同，所以内容会居中。
11. 绝对定位：position:absolute。绝对定位的元素会从流中删除，并根据制定的top left right 或者button属性定位。因为从流中删除，其它元素将完全感知不到绝对定位的元素。
12. 固定定位：position:fixed  固定定位是相对于浏览器窗口的，不是相对于页面，则此固定元素永远不会定位。

######专业名词：
1. 浮动 页面浮动流(左或者右浮动)，块元素忽略此元素，但内联元素会扰流这个元素。float:left  or  float:right
2. 冻结 布局的宽度大小冻结
3. 凝胶 当局部的宽度冻结的时候，左右margin是自动的。
4. 定位-position


