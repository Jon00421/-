# Web进阶

**语义化标签**
```html
<!-- 头部 -->
<header>header</header>
<!-- 主体 -->
<main>
    <!-- 导航 -->
    <nav>nav</nav>
    <!-- 区块 -->
    <section>section</section>
    <section>section</section>
</main>
<!-- 侧边栏 -->
<aside></aside>
<!-- 底部 -->
<footer></footer>
```


<a name="xV5MY"></a>
## 伪元素-- ::after/::before
伪元素就是利用`css` 代码在标签内部的前，或后添加一个行内元素`<span>`
```css
/* before、after */
选择器::before{
  /* 使用空白符号占位 */
  content: '';
}

```
<a name="eG6FE"></a>
### 伪类清除浮动
哪个盒子的子元素有浮动，就在哪个盒子上添加清除浮动
```css
.clearfix::after{
  content: '';
  display: block;
  clear: both;
}
```
<a name="bgkKs"></a>
### 事件伪类

- `:hover`--鼠标悬停时
   - 一个标签可以添加多个`:hover`
   - hover一定要在active之前
- `:active`--鼠标点击时



- `:focus`--获取焦点后


<br />

- **通过父元素的伪类****改变****直接子元素****的样式**
```css
<div>
    <span></span>
</div>

div:hover>span{
    background:blue;
}
```

- **通过兄弟元素的伪类改变另一个兄弟元素的属性**

兄弟元素必须紧邻有伪类效果的元素
```css
<div>
    <input type="text">
    <div></div>
</div>
/* 选中获得焦点的 input 元素后面一个 div 元素（input 和 div 是兄弟元素） */
input:focus+div{
    border:1px solid blue;
}
```


<a name="kiqj1"></a>
### 列表伪类
列表伪类的功能更像是一个选择器，选择某个元素的子元素<br />不是只有`li`才能使用，使用条件是同一级别，相同元素<br />

- 匹配其父元素的第一个子元素--`:first-child`
- 匹配其父元素的最后一个子元素--`:last-child`
- 匹配其父元素的第n个子元素--`:nth-child()`
   - 括号内可以写数字，1代表first
   - odd(奇数)，evev(偶数)
```css
ul>li:nth-child(3){
  background-color: #3687FC;
  color: #FFFFFF;
}
```


<a name="J5BoL"></a>
## CSS装饰--curse
鼠标箭头的变化<br />`curse: pointer`<br />MDN文档[https://developer.mozilla.org/zh-CN/docs/Web/CSS/cursor](https://developer.mozilla.org/zh-CN/docs/Web/CSS/cursor)<br />

<a name="sAG33"></a>
## CSS Flex布局
Flex 是 Flexible Box 的缩写，意为"弹性布局"。<br />`display: flex;`

- 最显著的效果是把原来从上到下排列的块状元素变成水平排列

      注意:设为Flex布局以后，子元素的`float`、`clear`和`vertical-align` 属性将失效<br />
<br />采用Flex布局的元素，称为Flex容器(flex container) ，简称"**容器**"。它的所有子元素称为Flex项目(flex item)，简称"**项目**”。<br />

<a name="XrFIW"></a>
####  justify-content调整水平方向的分布
设置在容器上<br />![](https://cdn.nlark.com/yuque/0/2020/jpeg/2999046/1608538399929-25a44e30-3f75-401b-919a-4b8481006a30.jpeg#align=left&display=inline&height=378&margin=%5Bobject%20Object%5D&originHeight=755&originWidth=800&size=0&status=done&style=none&width=400)<br />

<a name="l81M3"></a>
#### align-items调整垂直方向上的分布
设置在容器上<br />![](https://cdn.nlark.com/yuque/0/2020/jpeg/2999046/1608538507845-3c0d9a9c-92c1-45ef-ade1-dc4621324c10.jpeg#align=left&display=inline&height=378&margin=%5Bobject%20Object%5D&originHeight=755&originWidth=800&size=0&status=done&style=none&width=400)<br />

<a name="nr48g"></a>
#### flex-warp项目换行
![](https://cdn.nlark.com/yuque/0/2020/jpeg/2999046/1608540560344-9baca3ac-4b6f-45fb-aab8-0745f8f012ae.jpeg#align=left&display=inline&height=581&margin=%5Bobject%20Object%5D&originHeight=1162&originWidth=800&size=0&status=done&style=none&width=400)<br />

<a name="wgSF9"></a>
#### 项目放大缩小 flex
设置在项目上<br />不允许项目压缩、放大 `flex: none`<br />项目自动充满剩余空间 `flex: 1`<br />

<a name="HLpwz"></a>
#### 改变容器中主轴和交叉轴的方向 flex-direction
设置在容器上<br />**主轴**：水平，从左到右<br />**交叉轴**：垂直，从上到下<br />![](https://cdn.nlark.com/yuque/0/2020/jpeg/2999046/1608596588601-af9ca075-08eb-4b5d-bdfc-80e4a6794491.jpeg#align=left&display=inline&height=188&margin=%5Bobject%20Object%5D&originHeight=250&originWidth=800&size=0&status=done&style=none&width=600)<br />**主轴改变后的影响**

1. 默认情况: `justify-content` 控制水平方向，`align-items`控制垂直方向;
1. 设置了`flex-direction: column` ， `justify-content` 控制垂直方向，`align-items` 控制水平方向;



<a name="pwjYR"></a>
## 文本溢出省略
**单行文本**

1. 强制不换行 `white-space: nowrap;`
1. **overflow**属性

`visible` 这是默认值，从父元素继承overflow属性的值<br />`hidden` 内容会被修剪，并且超出的内容不可见<br />`inherit` 内容不会被修剪，会呈现在元素框之外<br />`scroll` 内容会被修剪，浏览器会显示滚动条以便查看超出的内容<br />`auto `由浏览器定夺，如果内容被修剪，就会显示滚动条

3. 文本溢出省略 **text-overflow**

`clip` : 默认值，超出部分被截断。<br />`ellipsis` :表示用一个省略号("...")来表示被截断的文本。
```css
/* 强制不换行 */
white-space: nowrap;
/* 隐藏超出部分 */
overflow: hidden;
/* 用省略号代替剩余内容 */
text-overflow: ellipsis;
```
**多行文本**<br />通过WebKit内核浏览器 进行多行文本溢出省略
```css
/* 隐藏超出部分 */
overflow : hidden;
/* 文本超出就用省略号 */
text-overflow: ellipsis;
/* 把对象作为弹性伸缩盒子模型显示 */
display: -webkit-box;
/* WebKit内核的浏览器的私有属性，设置文本超出2行就用省略号 */
-webkit-line-clamp: 2;
/* WebKit内核的浏览器的私有属性，设置或检索伸缩盒对象的子元素的排列方式 */
-webkit-box-orient: vertical;
```


<a name="u0460"></a>
## SCSS--CSS预编译器
**Sass** 缩进格式  <br />使用“缩进”代替“花括号”表示属性属于某个选择器，用“换行”代替“分号”分隔属性，<br />
<br />**Scss**语法兼容CSS3<br />变量以"$"开头<br />
<br />**插值法 **`**#{}**`<br />几乎可在Sass样式表任何地方使用
```css
$name: "mail";
$top-or-bottom: "top";
$left-or-right: "left";

.icon-#{$name} {
  background-image: url("/icons/#{$name}.svg");
  position: absolute;
  #{$top-or-bottom}: 0;
  #{$left-or-right}: 0;
}
```
**嵌套**<br />Sass 允许将一套CSS样式嵌套进另一套样式中，内层的样式将它外层的选择器作为父选择器<br />
<br />父选择器 & <br />在嵌套CSS 规则时，有时也需要直接使用嵌套外层的父选择器，可以使用 `&`<br />
<br />**复用 mixin/include**<br />无参数混合

- `@mixin`: 定义可复用的样式
- `@include`: 应用可复用的样式
```css
@mixin square {
  width: 100px;
  height: 100px;
}
// 应用：
.user-avatar {
  @include square;
}
.admin-avatar {
  @include square;
}
```
有参数混合
```css
参数可设置默认值
@mixin square($size: 100px)
@mixin square($size) {
  width: $size;
  height: $size;
}
// 应用
.avatar {
  @include square(100px);
}
```

<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />

