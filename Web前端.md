# Web前端



<a name="0i4uY"></a>
# HTML
![](https://cdn.nlark.com/yuque/0/2020/jpg/2999046/1607944673788-13acbeff-28ad-4981-a7f0-60422955ee17.jpg#align=left&display=inline&height=369&margin=%5Bobject%20Object%5D&originHeight=738&originWidth=1146&size=0&status=done&style=none&width=573)<br />
<br />

- **<!DOCTYPE html>**
1.   作用:告知浏览器该页面文件的文档类型，指示 web浏览器使用哪个HTML版本编写页面。
1.  位置:`<!DOCTYPE>`声明必须是HTML文档的第一行，位于`<html>`标签之前。
1. `<!DOCTYPE>`声明对大小写不敏感。
1. `<!DOCTYPE>`声明没有结束标签。


<br />
<br />

- **<html lang= "en">...</html>**

1.此元素可告知浏览器其自身是一个HTML文档。<br />2.`<html>`与`</html>`标签限定了文档的开始点和结束点，在它们之间是文档的头部和主体。文档的头部由`<head>`标签定义，而主体由`<body>`标签定义。<br />3.lang属性（语言属性)︰当搜索引擎或者浏览器拿到语言属性后，有可能做一些针对指定语言的辅助操作，'en'表示英   文。<br />
<br />

- **文档的头部<head> . ..< / head>**

1.head元素定义文档的头部，我们通常在这里引用样式表、提供元信息等。<br />2.文档的头部中的`<title>...</title>`定义文档的标题，在网页上体现为网页标签的标题。<br />3.一个`<head>`元素必须包含且只能包含一个`<title>`元素。<br />

- **注释**`**<!--  ...  -->**`



<a name="y4KeK"></a>
## 文本标签


<a name="sHNFO"></a>
### 块状标签

   - 独占一行
   - `<p>` 、`<h1>`、`<div>`
<a name="TlBPZ"></a>
### 内联标签

   - 只占一行中的一部分，常被嵌套于块状标签
   - `<span>`、`<img>`、`<strong>`
<a name="EqiUk"></a>
### 标题标签

- `<h1>` ~ `<h6>`
- 数字越大，级别越低，标题越小
- 标题之间不可越级，比如—级标题`<h1>`下直接写三级标题`<h3>`，会导致文章失去清晰的文章结构
<a name="Xsq8A"></a>
### 常用文本标签

- 段落标签 `<p>`
- 内联标签 `<strong>`  表示内容具有 **重要性**
   - `<b>`标签也能让内容变粗体，但它没有语义，只是单纯表示样式加粗。
- 内联标签 `<span>` 表示一个行内短语，可以使网页更有条理
<a name="J6mIv"></a>
### 图片标签
`<img src="  ...  "   alt="" />`

- `alt`定义了描述图像的替换文本
- `src`中写入图片的**相对路径**或**绝对路径**
- 属于内联标签
- 无结束标签
<a name="wllML"></a>
### 链接标签
`<a href="URL"> ... </a>`

- 属于内联标签
- `href`给出链接指向的网址，URL或者锚点
- `title`给出链接的说明信息，当鼠标悬停在链接上方，会显示该属性的值
- `target`指定如何展示打开的链接，
   - `_self`（默认）在当前页面打开
   - `_blank`  在新页面打开
   - `_parent`
   - `_top`
<a name="yPA1a"></a>
### 列表
无序列表`<ul>` 有序列表`<ol>`
```html
<ul>
    <li> ● </li>
  	<li> ● </li>
</ul>

<ol>
    <li> 1.</li>
    <li> 2.</li>
</ol>

```


<a name="ELfi0"></a>
## 表单标签
<a name="KmPqO"></a>
### form标签
```html
<!-- <form>是块状标签，要注意：<form>标签不能嵌套<form>标签 -->
<form action="">
  <!-- 这里会有一些表单控件 -->
</form>
```

- `action` :一个处理此表单信息的程序所在的 URL，所述表格信息将在表单提交时被发送到定义的地址;
- `method` :它的值可以是GET 或POST，用来规定如何发送表单信息;



<a name="JtH7q"></a>
### 单行文本输入框
```html
<!-- action=""则表单信息将提交到当前页面 -->
<form action="">
  <input type="text" />
</form>
```

- **占位文本 "placeholder"**
   - 用来提示用户需要输入什么
- **输入框名字  "name"**
   - 为了区别其他`<input>`
- **输入框的值 "value"**
   - 预填写值
- **不可修改的输入框 "readonly"和"disabled"**
| **属性** | **disbled** | **readonly** |
| --- | --- | --- |
| 对象 | 所有表单元素 | input和testarea |
| 作用 | 使文本框不能输入，当表单以POST或GET的方式提交时，使用了disabled元素的值不会被传递出去。 | 仅使文本框不能输入 |
| 外观(不同浏览器会有区别) | 使文本框变灰 | 没有变化 |



<a name="bjGtX"></a>
### 多行文本输入框
当多行文本输入框中输入的内容超过一行的长度时，它会自动换行，而单行文本输入框则不会换行。
```html
<!-- name属性表示表单元素的名称，placeholder属性表示表单元素的占位文本 -->
<textarea
  name="sign"
  rows="5"
  cols="30"
  placeholder="请输入个性签名"
></textarea>
```

- rows：行数（高度）
- cols：文本域的可视宽度



<a name="UJPkM"></a>
### 密码输入框
密码输入框和昵称输入框有点区别，用户输入的内容将会以 **黑圆点 **的形式显示。<br />`<input type="password" name="password" placeholder="密码" />`<br />

<a name="N1nDk"></a>
### 单选框

- 所谓单选框，其实只是把控件类型`type="text"`改成了`type="radio"`
- 属于同一道“单选题"的每个单选按钮，应该拥有 **相同 **的`name` 属性值。
```html
<!-- 通过<label>使点击文字也能选中对应的选项 -->
<label> <input type="radio" name="gender" value="male" />男 </label>
<label> <input type="radio" name="gender" value="female" />女 </label>

<!-- 另一种写法 -->
<input id="male" type="radio" name="gender" value="male" />
<label for="male">男</label>
<input id="female" type="radio" name="gender" value="female" />
<label for="female">女</label>
```
<a name="Aj6QJ"></a>
### 复选框

- `type="checkbox"`
- 单击选中，再次单击取消选中
- 属于同一道“多选题"的每个复选框元素，应该拥有 **相同 **的`name`属性值。



<a name="WUkxZ"></a>
### 选项菜单

- 提交的内容是`<option>`标签的标签属性`value`的值。所以每个option的value值要互不相同。
- 添加`multiple`属性，可以变成多选菜单
```html
<select name="career" multiple>  
  <option value="default">请选择职业</option>
  <option value="staff">公司职员</option>
  <option value="freelancer">自由职业者</option>
  <option value="student">学生</option>
  <option value="other">其他</option>
</select>
```


<a name="P6MIv"></a>
### 按钮

- `<button type="submit">注册</button>`
- 因为<button>标签有闭合标签，在开始标签和结束标签之间，我们可以放上文字、图片、图标等等。
```html
<form action="">
  <input type="text" name="name" placeholder="请输入昵称" />
  <textarea
    name="sign"
    rows="5"
    cols="30"
    placeholder="请输入个性签名"
  ></textarea>
  <input name="password" type="password" placeholder="请输入密码" />

  <label> <input type="radio" name="gender" value="male" />男 </label>
  <label> <input type="radio" name="gender" value="female" />女 </label>

  <label> <input type="checkbox" name="interest" value="coding" />编程 </label>
  <label> <input type="checkbox" name="interest" value="other" />其他 </label>

  <select name="career">
    <option value="default">请选择职业</option>
    <option value="staff">公司职员</option>
    <option value="freelancer">自由职业者</option>
    <option value="student">学生</option>
    <option value="other">其他</option>
  </select>

  <button type="submit">注册</button>
</form>
```


<a name="zDLCp"></a>
## CSS-美化文档


- **字体大小 ****font-size**

`<p style="font-size: 12px;">`<br />

- **字体粗细 font-weight**
   - 设置文字粗细的时候，其值可以是100，200，300，400，500，600，700，800，900中的任何一个,或者可以用英文代替，normal(正常粗细) ，lighter(细)，bold (粗)，bolder(更粗)



- **字体颜色**
1. **英文字母形式**

`color:balck;`、 ` color:blue;`<br />

2. **十六进制颜色(多数情况下)**

   十六进制颜色由#开头，后面跟三个数字，每个数字的范围为00 ～FF，每个数字代表一种颜色，最终的颜色由这三种颜色调和而成<br />`color: #D5E8D4;`  `color: #DAE8FC;`<br />

3. **rgb形式**

`color: rgb(253,217,106)`<br />
<br />   4.** rgba形式**<br />** **a代表Alpha(透明度)，a的值在0～1之间，为了简化书写，也可以直接省略0，写成.4，等同于0.4。<br />`color: rgba(253,217,106,0.3);``color: rgba(253,217,106,1.0);`<br />

- **文字对齐方式**
   - text-align: center; 居中
   - text-align: left; 左对齐
   - text-align: right; 右对齐



- **文字行高**

`line-height:32px;`

   - 改变段落中行距
   - 使文字上下居中



- **字间距**

`letter-spacing:30px;`<br />

- **字体**

`font-family: sans-serif;`

   - 可以设置多个字体，浏览器会按顺序加载
<a name="8GTJ0"></a>
## CSS的引入方式


<a name="gA2MT"></a>
### 三种引入方式


- **行内式**

内嵌在每一个HTML标签中<br />

- **内部样式**
```html
<style>
  /*给h3标签添加样式*/
  h3{
    font-size:28px;
    color:#333;
    letter-spacing:5px;
  }
    /*给p标签添加CSS样式*/
    p{
      font-size:12px;
      color:#666;
    }
</style>
```

- 不要忘记写声明标签`<style></ style>`
- 样式要用**花括号**括起来
- 每个样式后面要用**分号**结尾
- CSS中注释格式为  `/* ... */`

`<br />`<br />

- **外部样式**
- 新建一个`.css`文件，把`CSS`样式写在里面
- 建立`HTML`和`CSS`文件的联系，用`link` （`link`标签引入的位置要在`head`标签内）
```html
<link rel="stylesheet" type="text/css" href="index.css" />
```

- `rel`属性 规定当前文档与被链接文档之间的关系，`stylesheet`(外部样式表) 值被所有浏览器支持
- `type`属性 规定了被链接文档的 MIME(多用途互联网邮件扩展类型) ，最常见的值是`text/css`
- `href`属性 后跟的是要引入的链接地址



<a name="R7e2u"></a>
### 常用选择器

- 选择器的层叠性

  若之前写过的标签重新再写了一次，然后给里面添加样式，这样做可能会造成两种结果:

   1. 添加新的效果（如果添加的是一个新属性)
   1. 改变之前已经存在的效果(如果该属性之前就存在)


<br />

<a name="GNJMw"></a>
#### 类选择器

- 类选择器同样具有层叠性，改变顺序可能会影响结果
- 可以一个标签添加多个类名
```html
.article {
  color: red;
  font-size: 14px;
}

<p class="article">
   class是定义类的关键字，article是类名，类名可以任意，但是要符合规范
</p>

```


<a name="tlxBe"></a>
#### id选择器

- id选择器在文档中只能出现一次
- 一个标签只能定义一个id名
```html
#p-item {
  font-size: 24px;
  font-weight: 400;
}

<p id="p-item">这是一段文字</p>
```
<a name="yzOPZ"></a>
### 高级选择器

<br />

<a name="RJ81A"></a>
#### 后代选择器（空格）

- 书写规则：用空格隔开
```css
/* 选择id名为password的标签内部所有类名为box的元素内部的所有p标签 */
#password .box p{}
/* 选择所有p标签内部的所有span标签 */
p span{}
/* 选择所有p标签内部的所有类名为spanItem的标签 */
p .spanItem{}
```


<a name="jKJhf"></a>
#### 交集选择器

- `a.special{}`    在所有a标签内，类名为special的标签。
- <br />
<a name="7bWRw"></a>
#### 子选择器

- 与后代选择器类似，不同的是后代选择器突出“后代”，子选择器突出“子”

`p>span`  在`p`标签内的`span`适用<br />`p span`  在`p`标签中的所有`span`，不一定是`p`的子元素，只要是`p`的后代都适用<br />
<br />**并集选择器**

- 给不同的标签，或者不同类名的标签添加相同的样式
- 规则是在标签名或者类名后面用逗号（，）隔开

`.box,p,h3,.phone{}`

<a name="fKoMK"></a>
#### 优先级

- 单个选择器的优先级
   - id选择器>类选择器>标签选择器



- 高级选择器的优先级
   - 权重，优先级越高，权重越大
   - 权重的作用是决定当两个不同的选择器给同一标签设置了相同的属性，该听谁的
   - 只有当同时选中一个标签时才考虑权重


<br />只有当权重一样或优先级一样才考虑层叠性
<a name="59ru0"></a>
## CSS-盒模型 

- 默认没有高度，有宽度(继承于父标签)



<a name="fQLHh"></a>
### content

- `width/height`--宽高
   - 值是数字，单位是`px`
   - 可以设置为半分比尺寸 `%` （相对于父元素），所以要先确定父元素的尺寸
- `background-color`--背景颜色
   - 值有十六进制，`rgb`，`rgba`，英文颜色

<br />
<a name="fDB5F"></a>
### padding 内边距

- 第一个值是上，第二个值是右，第三个值如果没有，就和第一个值保持一致，第四个值如果没有就和第二个值保持一致
```css
div{
    padding: 30px 20px; /* top:30 right:20 bottom:30 left:20 */
}                       /* 上右下左  */
```

- **box-sizing**

      `box-sizing` 规定了如何计算一个元素的总宽度和高度，它有两个值`content-box` ，`border-box`，<br />      默认是`content-box`

   - content-box尺寸计算公式:
      - width =内容的宽度
      - height =内容的高度
   - border-box尺寸计算公式:
      - width = border + padding +内容的宽度
      - height = border + padding +内容的高度

`border-box`的`width`包含了`content `、`padding` 、`border`，所以子元素设置        `padding `, `border`后不会溢         出父元素的`content`<br />
<br />

<a name="y2KuU"></a>
### border 边框
`border-width`：边框的粗细，单位px<br />`border-color`：边框的颜色<br />`border-style`：线型  `solid`为实线，`dashed`为虚线<br />`border-radius`：圆角  可分开设置`border-top-left-radius` 左上角，右上角。。。

- 分别设置边框

`border-top-color: blue;`
```css
/* 简写 */
.box {
  /* 添加顶部border */
  border-top: 1px solid black;
  /*添加右侧border*/
  border-right: 3px solid orange;
  /*添加底部border*/
  border-bottom: 5px dashed pink;
  /*添加左侧border*/
  border-left: 10px dashed purple;
}
/* 利用层叠性，减少代码书写量 */
.box{
  border: 2px solid black;
  /*重新设置一个下边框的样式来层叠掉统一设置的边框的样式*/
  border-bottom: 5px solid orange;
}
```

- 阴影  
```css
  /* x偏移量 | y偏移量 | 阴影模糊半径 | 阴影扩散半径 | 阴影颜色 */
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
```

   - x偏移量: 在x轴上移动，向右为正
   - y偏移量: 在y轴上移动，向下为正
   - 阴影模糊半径: 就是边线的清晰度
   - 阴影扩散半径: 就是向外伸展
   - 阴影颜色: 就是矩形下面那个矩形的背景色。



<a name="ep2Eo"></a>
### margin 外边距

- 两个盒子之间margin计算

水平距离为两个盒子外边距相加；<br />垂直距离为两个盒子外边距最大值；

- 盒子左右居中

margin可以使盒子在父盒子中居中，但前提是有宽度<br />`margin:0 auto;`<br />

<a name="zTZgw"></a>
### 块元素 block

- 独占一行
- 可以设置宽高
- `display: block;`



<a name="rvhzd"></a>
### 行内元素inline

- 不能设置宽高
- 可以设置`padding`
- 可以设置左右`margin`，不能设置上下`margin`
- `display: inline`
<a name="NTLEh"></a>
### 
<a name="s5vbN"></a>
### 行内块 inline-block

- 可在同一行显示的块元素
- 空白问题（两个盒子间会有空白，是由于两个div间多了一个回车，被当做成一个文字）
   1. 去除回车
   1. 给父元素添加 `word-spacing` 属性

`word-spacing`就是单词和单词之间的距离，值要尽量小，一般小于`-20px`

   1. 给父元素设置 `font-size: 0px;`

              回车被当做是一个文字，则可以设置文字大小为0<br />
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

