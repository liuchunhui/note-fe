## 盒模型
在模块还不太稳定的阶段，浏览器会采用厂商前缀实现某个特征。  

* -webkit-: Chrome、Safari
* -o-: Opera
* -moz-: Firefox
* -ms-: Internet Explorer

盒模型（box model），盒模型两部分组成：内容和边框。
![](./imgs/CSS-盒模型-1.png)
                    

### W3C盒模型和IE盒模型区别：

![](./imgs/CSS-盒模型-2.png)
    
W3C模型中：
* CSS中的宽（width）=内容（content）的宽
* CSS中的高（height）=内容（content）的高

IE模型中：
* CSS中的宽（width）=内容（content）的宽+（border+padding）*2
* CSS中的高（height）=内容（content）的高+（border+padding）*2

解决：
1. 在IE8及以下的浏览器中只支持IE盒模型，在IE8+及其他主流浏览器中，通过CSS新增的box-sizing属性可以设置浏览器的盒模型。box-sizing属性的默认值是content-box，即W3C标准盒模型；而将box-sizing值设置为border-box时，则会更改为IE盒模型。
box-sizing ： content-box | border-box | inherit

  - content-box : 让元素采用标准的W3C盒模型。
  - border-box：让元素采用IE盒模型。
  - inherit：让元素继承父元素的`box-sizing`属性

2. 避免触发IE盒模型的方法是使用<!DOCTYPE html>声明，告诉IE采用W3C盒子模型即可。


## 应用

### 元素内边距（padding）

应用内边距会在元素内容和边框之间添加空白。

内边距属性：
|属性|说明|值|
|---|---|---|
|padding-top|为顶边设置内边距|长度值或百分比|
|padding-right|为右边设置内边距|长度值或百分比|
|padding-bottom|为底边设置内边距|长度值或百分比|
|padding-left|为左边设置内边距|长度值或百分比|
|padding|简写|1~4个长度值或百分比|

使用百分数值指定内边距，百分数是跟`包含块(父元素)`的宽度相关，高度不在考虑范围内。

### 元素外边距（margin）

外边距是元素边框和页面上围绕在它周围的所有东西之间的空白区域。围绕的东西包括父元素或其它元素。

外边距属性：
|属性|说明|值|
|---|---|---|
|margin-top|为顶边设置外边距|长度或百分比|
|margin-right|为右边设置外边距|长度值或百分比|
|margin-bottom|为底边设置外边距|长度值或百分比|
|margin-left|为左边设置外边距|长度值或百分比|
|margin|简写|1~4个长度值或百分比|

使用百分数值指定外边距，百分数是跟`包含块(父元素)`的宽度相关，高度不在考虑范围内。

### 元素尺寸（width、height）

浏览器会基于页面上的内容的流设置元素尺寸。

尺寸属性：

|属性|说明|值|
|---|---|---|
|width-height|设置元素的宽度和高度|auto、长度值或百分比|
|min-width|设置元素最小可接受宽度|auto、长度值或百分比|
|min-height|设置元素最小可接受高度|auto、长度值或百分比|
|max-width|设置元素最大可接受宽度|auto、长度值或百分比|
|max-height|设置元素最大可接受高度|auto、长度值或百分比|
|box-sizing|设置尺寸调整应用到元素盒子的哪一部分|content-box <br>padding-box <br>border-box <br>margin-box|

宽度相关百分数值是根据`包含块(父元素)`的宽度高度来计算的；
高度计算待定？？？

### 溢出内容（overflow）

元素内容太大，无法完全显示在元素的内容盒中，默认处理方式是溢出，并继续显示。

属性：

|属性|说明|值|
|---|---|---|
|overflow-x|设置水平方向溢出方式|auto, hidden, no-content, no-display, scroll, visible|
|overflow-y|设置垂直方向溢出方式|同上|
|overflow| 简写|同上|

溢出属性值：

|值|说明|
|---|---|
|auto|浏览器自行处理溢出内容。通常如果内容被裁剪掉就显示滚动条，否则就不显示|
|hidden|多余的部分直接剪掉，只显示内容盒里面的内容|
|no-content|如果内容无法全部显示，就直接移除。主流浏览器都不支持这个值|
|no-dispaly|如果内容无法全部显示，就隐藏所有内容。主流浏览器都不支持这个值|
|srcoll|让用户看到所有内容添加滚动机制，通常是滚动条|
|visible|默认值，不管是否溢出内容盒，都显示元素内容|

### 元素的可见性（visibility）

属性：

|属性|说明|值|
|---|---|---|
|visibility|设置元素的可见性|collapse, hidden, visible|

属性值：

|值|说明|
|---|---|
|collapse|元素不可见，且在页面布局中不占据空间（只能应用到表相关元素，如tr和td）|
|hidden|元素不可见，但在页面布局中占据空间|
|visible|默认值，元素在页面上可见|

`collapse`值只能应用到表格元素，对于非表格元素可以用dispaly属性应用none值可以达到相同的目的。

### 元素的盒类型（display）

`display`属性提供了一种改变元素盒类型的方式，这相应会改变元素在页面上的布局方式。

display属性的值：

|值|说明|
|---|---|
|inline|盒子显示为文本行中的字|
|block|盒子显示为段落|
|inline-block|盒子显示为文本行|
|list-item|盒子显示为列表项，通常具有项目符号或者其他标记符号|
|run-in|盒子类型取决于周围元素|
|compact|盒子的类型为块或者标记盒（类似list-item类型）|
|flexbox|弹性盒布局|
|table|与表格中的元素布局相关|
|inline-table||
|table-row-group||
|table-header-group||
|table-footer-group||
|table-row||
|table-column-group||
|table-column||
|table-cell||
|table-caption||
|ruby|跟带ruby注释的文本布局相关|
|ruby-base||
|ruby-text||
|ruby-base-group||
|ruby-text-group||
|none|元素不可见，且在页面布局中不占空间|

#### 块级元素（display: block）

块级元素会在垂直方向跟周围元素有所区别。通常在元素前后放置换行符也能达到这种效果，在元素和周围元素之间制造分割的感觉。像`<p>`标签默认样式就包括块级元素`display: block`。

#### 行内元素（display: inline）

使用inline值的时候，浏览器会忽略某些属性，如width，height和margin。

#### 行内-块级元素（display: inline-block）

`display: inline-block`会创建一个其盒子混合了块级元素和行内元素特征的盒子，盒子整体上作为行内元素显示，在垂直方向上该元素和周围的内容并排显示，没有区别。但盒子内部作为块级元素显示，width、height和margin属性都能应用到盒子上。
`整体作为行内元素，内部作为块级元素。`

#### 插入元素

`display: run-in`值会创建插入元素：其盒子类型取决于周围元素。
1. 如果插入元素包含一个display属性值为block的元素，那么插入元素就是块级元素。
2. 如果插入元素的相邻兄弟元素是块级元素，那么插入元素就是兄弟元素中的第一个行内元素。
3. 其他，插入元素均为块级元素对待。

[注意]只有safari和IE8+支持

#### 隐藏元素

`dispaly: none`告诉浏览器不要为元素创建任何类型的盒子，元素没有后端元素，元素在页面布局中不占据任何空间。


### 浮动盒（float）

使用float属性创建浮动盒，浮动盒会将元素的左边界与右边界移动到包含块或另一个浮动盒的边界。

|属性|说明|值|
|---|---|---|
|float|设置元素的浮动样式|left, right, none|

|值|说明|
|---|---|
|left|移动元素，使其左边界挨着包含块的左边界，或者另一个浮动元素的右边界|
|right|移动元素，使其右边界挨着包含块的右边界，或者另一个浮动元素的左边界|
|none|元素位置固定|

#### 阻止浮动元素堆叠

设置了多个浮动元素，默认情况下会一个挨着一个的堆叠在一起，使用`clear`属性可以阻止出现这种情况。

|属性|说明|值|
|---|---|---|
|clear|设置元素的左边界、右边界或左右两个边界不允许出现浮动元素|left、right、both、none|

|值|说明|
|---|---|
|left|元素的左边界不能挨着另一个浮动元素|
|right|元素的右边界不能挨着另一个浮动元素|
|both|元素的左右边界不能挨着浮动元素|
|none|元素的左右边界都能浮动元素|