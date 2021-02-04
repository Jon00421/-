# SCSS

<a name="TmaBz"></a>
# sass/scss
> Scss 是 Sass 3 为了兼容 CSS 而引入的新语法

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
<br />**父选择器`&`**<br />在嵌套CSS 规则时，有时也需要直接使用嵌套外层的父选择器，可以使用 `&`<br />

<a name="gay92"></a>
## 复用 mixin/include
无参数混合

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
<a name="KqH7d"></a>
## @for
```css
@for $i from <start> through <end>
@for $i from <start> to <end>
```
 through 表示包括 end ，而 to 则不包括 end 这个数
<a name="eDvjv"></a>
# 媒体查询
> 媒体查询是CSS3中引入的一种CSS技术。仅当满足特定条件时，它才使用对应的CSS属性块。

![](https://cdn.nlark.com/yuque/0/2020/jpeg/2999046/1608683191931-825e4080-7f95-46af-b3f1-dae02da25107.jpeg#align=left&display=inline&height=288&margin=%5Bobject%20Object%5D&originHeight=576&originWidth=772&size=0&status=done&style=none&width=386)<br />**断点**

1. 媒体查询用`max-width`表示条件的时候，大的断点放上面。
1. 用`min-width`表示条件的时候，小的断点放上面。


<br />

