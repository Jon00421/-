# Web前端



<a name="0i4uY"></a>
# HTML
![](https://cdn.nlark.com/yuque/0/2020/jpg/2999046/1607944673788-13acbeff-28ad-4981-a7f0-60422955ee17.jpg#align=left&display=inline&height=369&margin=%5Bobject%20Object%5D&originHeight=738&originWidth=1146&size=0&status=done&style=none&width=573)




- **<!DOCTYPE html>**
1.   作用:告知浏览器该页面文件的文档类型，指示 web浏览器使用哪个HTML版本编写页面。
1.  位置:`<!DOCTYPE>`声明必须是HTML文档的第一行，位于`<html>`标签之前。
1. `<!DOCTYPE>`声明对大小写不敏感。
1. `<!DOCTYPE>`声明没有结束标签。







- **<html lang= "en">...</html>**

1.此元素可告知浏览器其自身是一个HTML文档。
2.`<html>`与`</html>`标签限定了文档的开始点和结束点，在它们之间是文档的头部和主体。文档的头部由`<head>`标签定义，而主体由`<body>`标签定义。
3.lang属性（语言属性)︰当搜索引擎或者浏览器拿到语言属性后，有可能做一些针对指定语言的辅助操作，'en'表示英   文。




- **文档的头部<head> . ..< / head>**

1.head元素定义文档的头部，我们通常在这里引用样式表、提供元信息等。
2.文档的头部中的`<title>...</title>`定义文档的标题，在网页上体现为网页标签的标题。
3.一个`<head>`元素必须包含且只能包含一个`<title>`元素。


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
密码输入框和昵称输入框有点区别，用户输入的内容将会以 **黑圆点 **的形式显示。
`<input type="password" name="password" placeholder="密码" />`
























