# JavaScript

<a name="pDRa3"></a>
# JavaScript
- `script` 标签写在 `body` 标签末尾
- 引入`xxx.js`文件  `<script src='index.js'></script>`



<a name="Lv5Pc"></a>
## 模板字符串

- 模版字符串的核心是反引号`` ``和占位符`${expression}`

反引号的作用是将**字符串**和**变量**包起来<br />占位符的作用就是在字符串中插**变量**

- 换行可以直接**回车、**
- 在字符串中使用表达式，可以通过占位符`${expression}`

<br />
<a name="jPk74"></a>
## 基础数据类型
<br />
<a name="jmHZL"></a>
### 变量
变量就是保存值的占位符 ，用来临时保存值

`let name = "Jon";`<br />`const name = "Jon";`

- 声明变量时，不能重复声明同名变量（在不同作用域可以）
- `let` 定义的变量可以被多次重新赋值 ， 可以不赋初始值
- `const` 只能赋值一次 ，且必须赋初始值、



<a name="znoEA"></a>
### 数值类型

- **整数**
- **浮点数**
   - 浮点数精度丢失现象：浮点数值最高精度是17位小数，但在算数运算中精度远不如整数，例如 0.1+0.2=0.30000000000000004
- **NaN（非数值）**
   1. 0/0
   1. 字符串乘以数字
   1. `NaN`和任何数进行运算



<a name="AuhRZ"></a>
### 类型转换
**
<a name="fnkIH"></a>
#### 隐式转换

- 数字字符串**加**数字，数字隐式转换为字符串
- 数字字符串与数字（数字字符串）做**非加法运算，**字符串隐式转换为数字



<a name="DSgvO"></a>
#### 强制类型转换

- **parseInt**
   - 整数字符串-->整数
   - 小数字符串-->整数
   - 小数-->整数
- **parseFloat**
   - 小数字符串-->小数



<a name="7vm0W"></a>
### 相等/全等
相等(==) 只判断值是否相同<br />全等(===) 还判断类型是否相同<br />

<a name="JVCQi"></a>
## 数组元素的操作
数组的下标不是在正下方,而是在左下角<br />![](https://cdn.nlark.com/yuque/0/2020/png/2999046/1608966127662-71bc9c92-5d2f-4dfa-aa6b-b35e137a8acf.png#align=left&display=inline&height=56&margin=%5Bobject%20Object%5D&originHeight=75&originWidth=681&size=0&status=done&style=none&width=511)
<a name="G5FFq"></a>
### 增

- `push`（从尾加）
- `unshift`（从头加）
<a name="sfAYq"></a>
### 删

- `pop`（从后删）
- `shift`（从前删）
- `splice`（删除指定位置）
   - 一个参数：表示删除从指定位置到结束位置
   - 两个参数(a,b)：表示从下标a开始删除b个元素    
<a name="gLI2C"></a>
### 改

- `splice` （改指定位置的元素）
   1. 第一个值,整数类型,表示起始位置
   1. 第二个值,整数类型,表示步长(往后选几个元素,1代表往后选1个元素)
   1. 第三个参数,要替换的数组的值
```javascript
let schools = ['清华大学', '北京大学', '浙江大学', '同济大学'];
schools.splice(2, 0, '江西理工大学');
console.log(schools); //  ["清华大学", "北京大学", "江西理工大学", "浙江大学", "同济大学"]
```
<a name="p4cFf"></a>
### 查
`indexOf`

- 一个参数：查询数组内是否有查询的值（-1表示没有）
- 两个参数：第一个参数是我们要找的值,第二个参数是开始寻找的位置
<a name="ZDnHO"></a>
### 
<a name="RUfPy"></a>
## 循环
`for...in` 和 `for...of`
```javascript
let peppaFamily = ['佩奇', '乔治', '猪妈妈','猪爸爸'];

for(let item in peppaFamily) { //遍历结果是数组下标
  console.log(peppaFamily[i]);
}

for(let item of peppaFamily) { //遍历结果是数组的值
  console.log(item);
}
```
<a name="Rfkka"></a>
## 
<a name="ewPsM"></a>
## 函数
<a name="oXsVG"></a>
### 函数的声明

- **function命令**
   - 可以写在函数调用后面，会自动提升到代码头部
```javascript
function pringt() {
  console.log("JavaScript 真有趣");
}

```

- ![](https://cdn.nlark.com/yuque/0/2020/jpeg/2999046/1609210053898-f32a9d7e-cac0-4187-abb9-1675fe21f360.jpeg#align=left&display=inline&height=246&margin=%5Bobject%20Object%5D&originHeight=492&originWidth=692&size=0&status=done&style=none&width=346)**函数表达式声明**
   - 结尾要加`;`
```javascript
let print = function() {
  console.log("JavaScript 真有趣");
};

//可以用箭头函数简写
let print = () => {
  console.log("JavaScript 真有趣");
};
```

- **立即执行函数**

它会在函数声明后立即调用函数，除这一次调用外因为是匿名函数，所以无从调用
```javascript
(function() {
  console.log("这个函数只执行一次");
})();
```
<a name="UIfQ7"></a>
### 函数参数

- JavaScript 允许传入任意个参数而不影响调用，即参数多于，或者缺少，不会报错
- 可以给参数设置默认值
```javascript
// 参数 figure(位数) txt(文本) 默认值"随机数："
function code(figure, txt = "随机数：") {
  const num1 = Math.random() * 0.9 + 0.1;
  const num2 = Math.floor(num1 * Math.pow(10, figure));

  console.log(txt, num2);
}
```
<a name="PyItJ"></a>
### 计时器


<a name="n1vOb"></a>
#### 延时执行setTimeout( func|code , delay )
`setTimeout` 函数用来指定某个函数或某段代码，在多少毫秒之后执行。它返回一个整数，表示定时器的编号，以后可以用来取消这个定时器。
```javascript
// 首先定义计时总秒数，单位 s
let i = 60;
// 定义变量用来储存定时器的编号
let timerId;
// 写一个函数，这个函数即每次要执行的代码，能够完成上述的 1、2、3
function count() {
  console.log(i);
  i--;
  if (i > 0) {
    timerId = setTimeout(count, 1000);
  } else {
    // 清除计时器
    clearTimeout(timerId);
  }
}
// 首次调用该函数，开始第一次计时
count();
```
<a name="P49LH"></a>
#### 无限调用setInterval( func|code , delay )
与 `setTimeout` 区别仅仅在于`setInterva`l 指定某个任务每隔一段时间就执行一次，也就是无限次的定时执行
```javascript
let i = 60;
print();
let timer = setInterval(print, 1000);

function print() {
  console.log(i);
  i--;
  if (i < 1) {
    clearInterval(timer);
  }
}
```


<a name="YCfpn"></a>
## 对象
对象就是一组 "键值对"（key-value）的集合，是一种无序的复合数据的集合<br />

- 字面量定义方法
   - 当一个对象被赋值给person，在person中保存的其实是对象的**内存地址**。而不是对象本身。这种赋值被称为“引用”。
```javascript
let person = {
  name: 'henry',
  age: 18,
  run: function() {
    console.log('running');
  }
}
person.run();
```


- 通过构造函数创建新对象。
   1. 创建一个构造函数，构造函数的名称常根据**大驼峰命名法**命名（所有单词首字母均需要大写）;
   1. 通过new创建对象实例;
```javascript
// 第一步：创建构造函数
function People(name, age) {
  this.name = name;
  this.age = age;
}
// 第二步：通过 new 创建对象实例
let person = new People('henry', 18);
console.log(person);
```


<a name="WoJ0c"></a>
### 属性的读取

- **点运算符**

`person.name`

- **方括号运算符**（方括号中可以是一个变量）

`person['name']`

- **链式引用**（属性的值是对象）

      `person['parents']['mama']`<br />`person.parents.papa`
```javascript
let person = {
  name: 'henry',
  age: 18,
  parents: {
    papa: 'jack',
    mama: 'mary'
  }
}

console.log(person.parents.papa);
console.log(person['parents']['mama']);
```
<a name="VQl9a"></a>
### 属性的查看
`Object.keys(person)`返回一个数组，由`person`对象的所有属性名构成<br />

- Object是JavaScript提供的基本对象，JavaScript的所有其他对象都继承自Object对象，即那些对象都是object的实例。keys是object 对象的一个静态方法。



<a name="oaRP8"></a>
### 属性的删除和增加

- 删除 **delete**

`delete person.name;`

- 增加（ `.`新属性名=值 ）

`person.gender = 'male';`<br />

<a name="0wa6g"></a>
### 遍历对象属性
```javascript
let person = {
  name: 'henry',
  age: 18,
}

//用for...in遍历属性
for (var key in person) {
  console.log('键名：' + key + '；键值：' + person[key]);
}

//借助Object.keys遍历属性
let keys = Object.keys(person);
for (let i = 0; i < keys.length; i++) {
  console.log('键名：' + keys[i] + '；键值：' + person[keys[i]]);
}
```
<a name="b3YCB"></a>
### 对象的继承

- **原型**

一个对象，它称呼继承的上一级对象为原型，它自己也可以称作原型链下一级对象的原型。

- 通过继承创建对象
```javascript
// 字面量
let o1 = {
  name: 'alice',
};

// 构造函数
let o2 = new Object();
let o3 = new Object();

// 继承
let o4 = new o1();
```
<a name="BLmyA"></a>
### 属性是否存在
一个对象中的属性分为：继承属性和自身属性

- `in`运算符 判断对象是否拥有某个属性

`'name' in person;`<br />

- 自身属性是否存在：hasOwnProperty

`person.hasOwnProperty('name');`<br />

<a name="01s8V"></a>
### JSON 格式和 JavaScript 对象的转换

1. JSON.parse()：JSON 格式 => JavaScript 对象

`const obj = JSON.parse(jsonStr);`

2. JSON.stringify()：JavaScript 对象 => JSON 格式

`const jsonStr2 = JSON.stringify(obj);`<br />

<a name="Ggc5b"></a>
### Map 与 Object 的区别

- Map 比 Object 更灵活方便，但是考虑到 Map 不能直接转为 JSON 格式进行通讯，所以我们可以把 Map 作为 Object 的补充来使用。
1. 一个 Object 的键通常是字符串，但一个 Map 的键可以是任意值，包括函数、对象、基本类型，因此 Map 会方便很多；
1. Map 中的键值是有序的，而添加到对象中的键则不是；
1. Map 的键值对个数可以直接获取，Object 则要借助 Object.keys() 等计算得到；
1. Map 可直接进行迭代，Object 则要借助 Object.keys() 等；
1. Map 不存在键名和原型键名冲突问题，可以直接覆盖，Object 则不行；



<a name="D5y1u"></a>
### 内置对象


<a name="ayEK7"></a>
#### Math
Math对象的静态属性，提供以下一些数学常数：
```javascript
Math.E // 常数e。
Math.LN2 // 2 的自然对数。
Math.LN10 // 10 的自然对数。
Math.LOG2E // 以 2 为底的e的对数。
Math.LOG10E // 以 10 为底的e的对数。
Math.PI // 常数π。
Math.SQRT1_2 // 0.5 的平方根。
Math.SQRT2 // 2 的平方根。
```
静态方法
```javascript
Math.abs() // 绝对值
Math.ceil(4.6) // 向上取整，取大于等于 x，并且与它最接近的整数。
Math.floor(4.6) // 向下取整，取小于等于 x，并且与它最接近的整数。
Math.round(4.6) // 四舍五入取整，取与 x 最接近的整数。
Math.max() // 最大值
Math.min() // 最小值
Math.pow() // 指数运算
Math.sqrt() // 平方根
Math.log() // 自然对数
Math.exp() // e的指数
Math.random() // 随机数
```
<a name="elRHl"></a>
#### Storage
Storage 接口用于脚本在浏览器保存数据。<br />两个对象部署了这个接口：`window.sessionStorage` 和 `window.localStorage`

- `sessionStorage` 保存的数据用于浏览器的一次会话（session），当会话结束（通常是窗口关闭，数据被清空；
- `localStorage` 保存的数据长期存在，下一次访问该网站的时候，网页可以直接读取以前保存的数据。



- **数据的存入：setItem**

`window.localStorage.setItem('key', 'value');`<br />两个参数都是字符串，不是字符串的参数会被转成字符串后再存入浏览器。<br />

- **读取数据：getItem**

`window.localStorage.getItem('key')`<br />

- **清楚缓存：clear**

`window.localStorage.clear();`<br />

<a name="SKAwa"></a>
#### String


- 包装对象：原生对象 可以把原始类型的值包装成 对象；

`let v2 = new String('abc');`

   - 使得 JavaScript 的对象涵盖所有的值；
   - 使得原始类型的值可以方便地调用某些方法。

`let len = 'here is an apple'.length;`<br />
<br />

- **查找字符：`indexOf(sub)`**

存在时，返回字符串sub所在下标；不存在时，返回 -1<br />

- **去除两端空格：`trim()`**

不改变原字符串 str，而是复制一份原字符串，修改后返回给 trimedStr<br />

- **截取字符串：**`**substring()/substr()**`

`substring(start, end)`：start —— 要截取的字符串的开始下标，end —— 要截取的字符串的结束下标。<br />`substr(start, len)`：start —— 要截取的字符串的开始下标，len —— 要截取的字符串的长度。<br />

- **分割字符串：`spilt(pattern)`**

split 方法按照给定规则分割字符串，返回一个由分割出来的子字符串组成的**数组**<br />**<br />

<a name="blMev"></a>
#### Array

- **连接数组：`Join(pattern)`**

以 pattern 为分隔符，将所有数组成员连接为一个字符串返回。如果不提供参数，默认用逗号分隔：
```javascript
let arr = [1, 2, 3, 4];

arr.join(' ') // '1 2 3 4'
arr.join(' | ') // "1 | 2 | 3 | 4"
arr.join() // "1,2,3,4"
```

- **倒序排列：`reverse()`**

      颠倒排列数组元素，返回改变后的数组<br />

- **排序：`sort()`**

默认是按照字典顺序排序。可按照自定义方式排序，传入一个函数作为参数。
```javascript
let arr = [
  { name: 'jenny', age: 18 },
  { name: 'tom', age: 10 },
  { name: 'mary', age: 40 }
];

//当返回值大于 0 时，表示第一个成员应该排在第二个成员之后，否则排在第二个成员之前。
arr.sort(function(a, b) {
  return a.age - b.age;
});

console.log(arr);
```


- **有返回值的遍历：map**
```javascript
// elem: 数组成员
// index: 成员下标
// a: 整个数组
const handledArr = arr.map(function(elem, index, a) {
  elem.age += 1;
  console.log(elem, index, a);
  return elem.name
});

console.log(arr);
console.log(handledArr);
```

- **无返回值的遍历：forEach**



<a name="oYyV0"></a>
#### Date
![](https://cdn.nlark.com/yuque/0/2021/jpeg/2999046/1609557115203-9da0e255-78f8-4763-9859-7a5792a12a9d.jpeg#align=left&display=inline&height=249&margin=%5Bobject%20Object%5D&originHeight=498&originWidth=800&size=0&status=done&style=none&width=400)

- **获取当前时间：`new Date()`**
- 生成特定时间对象
```javascript
// 传入表示“年月日时分秒”的数字  月份范围0-11
let dt1 = new Date(2020, 0, 6, 0, 0, 0);
console.log(dt1);

// 传入日期字符串
let dt2 = new Date('2020-1-6');
console.log(dt2);

// 传入距离国际标准时间的毫秒数
let dt3 = new Date(1578240000000);
console.log(dt3);
```


- **日期推算**
```javascript
let dt1 = new Date(2020, 2, 1);
let dt2 = new Date(2020, 3, 1);

// 求差值
let diff = dt2 - dt1;
// 一天的毫秒数
let ms = 24 * 60 * 60 * 1000;
console.log(diff / ms); // 31

//早晚比较
console.log(dt1 > dt2); // false
console.log(dt1 < dt2); // true
```

- **解析日期字符串：`Date.parse()`**

Date.parse 方法用来解析日期字符串，返回该时间距离时间零点（1970 年 1 月 1 日 00:00:00）的毫秒数<br />

- **时间对象转时间字符串： to方法**

`let dtStr = dt.toJSON();`<br />

- **获取时间对象的年/月/日：get方法**
   - 注意，所有这些 get*方法返回的都是整数，不同方法返回值的范围不一样：

         分钟和秒：0 到 59

   - 小时：0 到 23
   - 星期：0（星期天）到 6（星期六）
   - 日期：1 到 31
   - 月份：0（一月）到 11（十二月）
```javascript
let dt = new Date();
dt.getTime(); // 返回实例距离1970年1月1日00:00:00的毫秒数。
dt.getDate(); // 返回实例对象对应每个月的几号（从1开始）。
dt.getDay(); // 返回星期几，星期日为0，星期一为1，以此类推。
dt.getFullYear(); // 返回四位的年份。
dt.getMonth(); // 返回月份（0表示1月，11表示12月）。
dt.getHours(); // 返回小时（0-23）。
dt.getMilliseconds(); // 返回毫秒（0-999）。
dt.getMinutes(); // 返回分钟（0-59）。
dt.getSeconds(); // 返回秒（0-59）。
```

- **设置时间对象的年/月/日：set方法**

没有 setDay 方法，星期几是计算所得
```javascript
let dt = new Date();
dt.setTime(ms); // 设置实例距离1970年1月1日00:00:00的毫秒数。
dt.setDate(date); // 设置实例对象对应每个月的几号（从1开始）。
dt.setFullYear(year); // 设置四位的年份。
dt.setMonth(month); // 设置月份（0表示1月，11表示12月）。
dt.setHours(hour); // 设置小时（0-23）。
dt.setMilliseconds(ms); // 设置毫秒（0-999）。
dt.setMinutes(min); // 设置分钟（0-59）。
dt.setSeconds(sec); // 设置秒（0-59）。
```

---



<a name="vAGcZ"></a>
## BOM

- window（窗口） ：整个网页的框架，每个网页的内容都是装载在window里面
- navigator（浏览器）：存储浏览器相关信息
- history （历史）：存储整个网页栈（网页前进后退）
- screen（显示屏幕）：包含显示屏幕的信息，这个是硬件信息
- Location（地址）：包含当前访问的地址（网址）信息

注意：

1. screen 是整个电脑唯一的
1. navigator 是整个浏览器唯一的，如果有多个浏览器就会有多个navigator
1. window 是每个网页唯一的，每个网页都有一个独立的window
1. history ，location 是每个网页的信息，当然也是网页唯一的



<a name="lFYvr"></a>
### window

1. window 对象表示一个浏览器窗口或一个 frame 框架，它处于对象层次的**最顶端**，它提供了处理浏览器窗口的方法和属性。
1. window 对象是浏览器对象中的**默认对象**，所以可以隐式地引用 window 对象的属性和方法。在浏览器环境中，添加到 window 对象中的方法、属性等，其作用域都是全局的。


<br />

<a name="AByGV"></a>
### Location
| **属性** | **值** | **解释** |
| :--- | :--- | :--- |
| href | [https://resource.youkeda.com/wss_test/5dc54e230f101ed7c2256d0d/5e33d104680dca7ebc7a223b/index.html?time=1580454161498](https://resource.youkeda.com/wss_test/5dc54e230f101ed7c2256d0d/5e33d104680dca7ebc7a223b/index.html?time=1580454161498) | href是整个网页地址 |
| hostname | resource.youkeda.com | hostname是网页域名 |
| host | resource.youkeda.com | host 是网页域名 + 端口信息 |
| protocol | https | protocol 代表协议信息 |
| origin | [https://resource.youkeda.com](https://resource.youkeda.com) | origin 页面来源的域名的标准形式 |
| pathname | /5dc54e230f101ed7c2256d0d/5e33d104680dca7ebc7a223b/index.html | pathname 包含 url 路径部分 |
| search | ?time=1580454161498 | search 表示 URL 参数 |



<a name="QyRsd"></a>
#### Location方法

- `reload()` 为了防止无限快速循环，设置一个定时器延迟调用 reload。
```javascript
setTimeout(function () {
  window.location.reload();
}, 3000);
```


- 跳转到新的地址
```javascript
window.location = 'https://www.youkeda.com';
```


<a name="SezU4"></a>
### History
History 允许操作浏览器的曾经在标签页或者框架里访问的会话历史记录，即会存储该窗口的历史记录。<br />在跳转新地址后，history中会存储会话记录（网址），以栈的形式<br />**方法 -- 返回和前进**

- `back()`
- `forward()`



<a name="DAkEN"></a>
### Navigator
Navigator 表示用户代理的状态和标识，也就是浏览器基本信息。<br />userAgent 代表当前浏览器的用户代理。<br />


---

<a name="ewNTV"></a>
# DOM

- 文档对象模型（Document Object Model）可以将** web页面** 与 **脚本** 或 **编程语言 **连接起来
   - DOM是一种规范，一种约定，只要遵循这个规范，无论是`Javascript` 、`python`或者`java` 都可以被连接起来。
   - HTML文档是树状结构，也对应数据结构中的树。



<a name="L1Ycf"></a>
### 访问DOM


- **获取 DOCUMENT** **--- `window.document;`**



- **选择器查询 --- `querySelector('selectors')`**
```javascript
////加强版本，加上父亲筛选， 筛选 main标签下面 -> class为core的节点下面 -> class为subtitle的节点
document.querySelector('main .core .subtitle');

//可以迭代查询
let subtitle = document.querySelector('main .core .subtitle');
console.log(subtitle.querySelector('a'));
```


- **选择器全量查询 --- **`**querySelectorAll('selectors')**`

可以查询所有 selectors 节点，返回一个**类数组 （NodeList对象）**<br />**
> getElementById(): 根据 id 查询某个节点1
> getElementsByClassName(): 根据 class 查询多个节点1
> getElementsByTagName(): 根据 标签名 查询多个节点1
> 

> querySelector(All) 和 getElementXXX 的区别 --- 动态性
> 1. querySelector 查询出来的元素是拷贝的原始数据，不会再随着页面 DOM 节点的改变而变化
> 2. get 系列方法 查询出来的元素就是原始数据，所以会随着页面的 DOM 节点的改变而变化



<a name="bTY7P"></a>
## DOM属性


<a name="w6SoJ"></a>
### DOM种类
每一种HTML标签基本都有一种DMO类型对应

1. **元素节点**
1. **特性节点**
1. **文本节点**
1. ... ...
<a name="A9sda"></a>
## 
**特性：**

- 整个 HTML 中，无论是标签，标签属性，还是纯文本字符串都是`Element`, 不同的地方在于`nodeType`分别为`1, 2, 3`。
- HTML 标签都是**元素节点**，可以用`nodeName`获取标签名称
- 纯文本都是**文本节点**，可以用`nodeValue`获取文本内容
- 标签的每个属性都是**特性节点**，可以用`nodeName`取得属性 Key，用`nodeValue`取得属性 Value
- `attributes`可以获取元素节点的所有属性，得到的结果是一个字典，通过属性 Key 获取对应的特性节点。



<a name="ITRfB"></a>
### DOM内容
`outerHTML`  ---> 整个DOM的HTML代码<br />`innerHTML`  ---> DOM内部的HTML代码<br />`innerText`  ---> DOM内部的纯文本内容<br />

<a name="Hwa6x"></a>
### DOM亲属
`firstChild`  --->  指定节点的第一个子节点<br />`lastChild`  --->  指定节点的最后一个子节点<br />`childNodes`  --->  指定节点的子节点的集合<br />`parentNode`  --->  指定节点的DOM树中的父节点<br />

<a name="bNH4z"></a>
### DOM样式
| **属性** | **类型** | **总结** |
| --- | --- | --- |
| `classList` | `DOMTokenList`**类数组**	 | **classList 数组方式存储所有的 class 名称** |
| `style`	 | `CSSStyleDeclaration`	 | **对象或字典的方法存储 CSSStyle** |

<a name="SE1eA"></a>
### DOM数据属性	
HTML提供—种数据属性的标准，利用`data-*`允许我们在标准内于HTML元素中存储额外的信息。例如：段落，字数，分类
```javascript
<article data-parts="3" data-words="1314" data-category="python"></article>

//通过js获取
const article = document.querySelector('article');
console.log(article.dataset);//dataset是个Map对象
```
<a name="HX4yN"></a>
## 


<a name="KcbsN"></a>
## DOM操作	
**1.创建标签节点**

- **创建标签节点 --- document.createElement(tagName)**

此方法用于创建一个由标签名称 tagName 指定的 HTML 元素（元素节点）。

- **继续添加纯文本内容 --- document.createTextNode(string)**


<br />**2.添加新节点**

- **添加新节点 --- appendChild(newNode)**

在所有儿子节点之后添加

- **inserBefore(newNode， referenceNode)**

在某个目标儿子（referenceNode）节点之前添加<br />
<br />**3.设置样式、属性**

- `dom.style`是一个Map对象
- **`setAttribute()`**不仅可以设置`style`，所有HTML属性都可以设置，例如 `id`、`src`、`type`、`disabled`
```javascript
img.setAttribute('style', 'width: 100%; height: 100%;');
//单独设置
dom.style.color = 'xxxx';
```


- 可以通过`classList`获取DOM所有的类，再把样式写成CSS，通过添加或删除class设置属性


<br />**4.innerHTML**

- `innerHTML = ''`清空节点所有后代内容
- 也可通过innerHTML给某个元素添加内容


<br />
<br />
<br />时钟 针移动
```javascript
// 渲染时钟
function render() {
  const oHoure = document.querySelector('#houre');
  const oMinute = document.querySelector('#minute');
  const oSecond = document.querySelector('#second');

  const nowTime = new Date();
  const nowHoure = nowTime.getHours();
  const nowMinute = nowTime.getMinutes();
  const nowSecond = nowTime.getSeconds();

  // 计算旋转度数
  const hourDeg =
    nowHoure * 30 +
    nowMinute * (360 / 12 / 60) +
    nowSecond * (360 / 12 / 60 / 60);
  const minuteDeg = nowMinute * (360 / 60) + nowSecond * (360 / 60 / 60);
  const secondDeg = nowSecond * (360 / 60);

  oHoure.style.transform = `rotate(${hourDeg}deg)`;
  oMinute.style.transform = `rotate(${minuteDeg}deg)`;
  oSecond.style.transform = `rotate(${secondDeg}deg)`;
}

render();

// 每隔1s进行一次渲染
setInterval(render, 1000);
```

<br />
<br />

<a name="FVDAT"></a>
## DOM事件


<a name="GXT1h"></a>
### DOM绑定事件
`addEventListener(eventName, callback)`绑定`eventName`事件<br />

<a name="EP6Jq"></a>
### 常见事件
**焦点事件**<br />focus: 表单组件（Input, Textarea, etc..）获取焦点事件<br />blur: 表单组件（Input, Textarea, etc..）失去焦点事件<br />
<br />**鼠标事件**<br />click: 点击事件<br />dblclick: 双击事件<br />mousedown: 在元素上按下任意鼠标按钮。<br />mouseenter: 指针移到有事件监听的元素内。<br />mouseleave: 指针移出元素范围外（不冒泡）。<br />mousemove: 指针在元素内移动时持续触发。<br />**mouseover**: 指针移到有事件监听的元素或者它的子元素内。<br />**mouseout**: 指针移出元素，或者移到它的子元素上。<br />mouseup: 在元素上释放任意鼠标按键。<br />
<br />**键盘事件**<br />keydown: 键盘按下事件<br />keyup: 键盘释放事件<br />
<br />**视图事件**<br />scroll: 文档滚动事件<br />resize: 窗口放缩事件<br />
<br />**资源**<br />load： 资源加载成功的事件<br />

<a name="Qvzd5"></a>
### 表单元素事件

- **焦点事件**（focus，blur）
- **内容值变化**
   - input --- 只要value值修改就会触发
   - change --- 1. checkbox 值修改以后  2. select 选择后  3. input 内容修改并失去焦点


<br />

<a name="pdr4l"></a>
### 冒泡、捕获、委托

<br />**冒泡**

- 触发子节点的监听事件后，会冒泡触发父亲节点的监听事件，直到html根元素
- 阻止冒泡--- **`e.stopPropagation()`**


<br />**捕获**<br />与冒泡相反，从根HTML节点开始依次移动到当前元素<br />
<br />
<br />**委托**<br />委托其实是**冒泡事件**的一种应用，当想要在**大量子元素中单击任何一个都可以运行一段代码**，可以将事件监听器设置在其**父节点**上，并让子节点上发生的事件冒泡到父节点上，而不是每个子节点单独设置事件监听器。<br />

<a name="BB4mM"></a>
## 网络请求
<a name="5QPWT"></a>
### fetch调用API

- `Promise`是**异步编程**的一种解决方案
- 可通过`.then`触发回调函数
> 解决回调地狱：把**嵌套型**的回调 调整成为**平铺型**的回调

```javascript
fetch(
  'https://www.fastmock.site/mock/b73a1b9229212a9a3749e046b1e70285/f4/f4-11-1-1'
)
  .then(function (response) {
    return response.json(); //返回的是一个 Promise 对象
  })
  .then(function (myJson) {
    console.log(myJson);
  });
```
<a name="jrPj6"></a>
### GET请求
`fetch`在不指定类型时，默认发起`GET请求`<br />
<br />带参数的`API`调用：<br />`https://api6.ipify.org?format=json`<br />

<a name="m4Kat"></a>
### POST请求
加参数**method**<br />`method: 'POST'`<br />
<br />通过`body`属性完成`POST`请求的传参<br />**注意**：在利用 body 传递`json`格式数据时，我们需要在`headers`里面加入`contentType信息`。
```javascript
// 把JSON数据序列化成字符串
const data = JSON.stringify({
  username: 'admin',
  password: '123456'
});
fetch(
  'https://www.fastmock.site/mock/b73a1b9229212a9a3749e046b1e70285/f4/f4-11-4-1',
  {
    method: 'POST',
    body: data,
    headers: {
      'content-type': 'application/json'
    }
  }
)
  .then(function(response) {
    return response.json();
  })
  .then(function(myJson) {
    console.log(myJson);
  });
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

