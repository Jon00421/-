# Java网络编程

<a name="NNgWe"></a>
# Java网络编程
<a name="3WYps"></a>
## 网络协议（HTTP/HTTPS）
![](https://cdn.nlark.com/yuque/0/2020/jpeg/2999046/1607084630001-6be20edf-5a02-4ba7-8ad0-f4401c17d9cf.jpeg#align=left&display=inline&height=546&margin=%5Bobject%20Object%5D&originHeight=546&originWidth=800&size=0&status=done&style=none&width=800)<br />

<a name="HSQad"></a>
## URL
`Uniform Resource Locato` 统一资源定位符<br />![](https://cdn.nlark.com/yuque/0/2020/png/2999046/1607044314350-63ed75da-83b4-44f0-91e8-abe4f3cbfdd1.png#align=left&display=inline&height=470&margin=%5Bobject%20Object%5D&originHeight=470&originWidth=1648&size=0&status=done&style=none&width=1648)

- **端口号**
   - `HTTP`协议默认端口号`80`
   - `HTTPS`协议默认端口号`443 `
- **路径**
   - 相对路径  ： 不是以`/` 开头的路径  
   - 绝对路径
   - 默认路径   ： 没有输入路径时，表示请求网站的默认页面，那么服务器就会返回一个默认页面给浏览器。至于具体默认页面是什么页面，是由服务器决定的，通常服务器默认的页面是首页。
<a name="rZq5Q"></a>
## JSON
JavaScript Object Notation（JavaScript 对象表示法）是目前最常用的**执行**对象序列化的方式。
<a name="sowJo"></a>
### 
<a name="o9ev4"></a>
### JSON格式化工具
JSON格式化工具[http://www.ab173.com/json/jsonviewernew.php](http://www.ab173.com/json/jsonviewernew.php)
<a name="XD8bi"></a>
### <br />
<a name="7iVoX"></a>
### JSON语法规则：

- 数据用 `名称:值` （也叫键值对）表示
   - 名称（键）必须是字符串
   - 键、值之间用冒号 “`:`” 分隔。
- 多条数据之间，用逗号 “`,`” 分隔
- 注意符号都是半角，不要因为输入法的原因输入全角了



<a name="O2A3T"></a>
### 
<a name="AMnjX"></a>
### JSON值的类型

- 范例
```json
{
    "name": "韦小宝",    //字符串（在双引号中）
    "age": 26,           //数字（整数或浮点数）
    "height": 182.4,  
    "birthday": "1670-7-28",
    "isRich": true,      //逻辑值（true或false）
    "wifes": ["阿珂", "双儿", "建宁公主", "苏荃", "沐剑屏", "曾柔", "方怡"], // 数组（中括号中）
    "firstMaster": {         // 对象（大括号中）
      "name": "陈近南",
      "birthday": "1634-12-1"
    }
}
```


<a name="RtMyQ"></a>
### FastJSON
`FastJSON` 是一个Java语言编写的高性能、功能完善、完全支持[官方](http://json.org/)标准的 `JSON` 库。<br />使用 `FastJson` 来操作 json 以及完成对象序列化、反序列化的操作，会非常方便。<br />

<a name="E7plz"></a>
#### 使用 FastJSON 序列化对象

- 引入依赖
```java
<!-- 在下列地址查询最新的版本：https://mvnrepository.com/artifact/com.alibaba/fastjson -->
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>fastjson</artifactId>
    <version>1.2.62</version>
</dependency>
```

- `**import**``**com**``.alibaba``.fastjson``.JSON``;`
```json
public static void main(String<[] args) {
    Building b = new Building();
    b.setName("创业大厦");
    b.setAddress("天宁兰陵兰陵路26号 ");
    String content = JSON.toJSONString(b); 
    System.out.println(content);
}
```
调用 `JSON.toJSONString(dog)` 方法，把 `Building` 对象转换为 JSON 格式的**字符串**返回。<br />
<br />

<a name="LYwY0"></a>
#### 使用 FastJSON 反序列化对象
```java
public static void main(String[] args) {
    
    // 转换为一个具体的对象 
    Building b2 = JSON.parseObject(content, Building.class); //第一个参数是字符串内容 第二个参数是目标类

    String name = b2.getName(); //转换为具体的对象后，就可以使用对象的属性和方法了，例如调用 b2.getName(); 取值。
    System.out.println(name); 
    // 特殊情况下，java系统里没有具体对象的 class ，可以反序列化为 Map 
    Map bInfo = JSON.parseObject(content, Map.class); 
    String name2 = (String) bInfo.get("name"); 
    //String name2 = bInfo.get("name").toString();
    
    System.out.println(name2);
}
```
当 JSON 格式是 `{}` 时，表示对象，可以反序列化为具体的对象或者 `Map`（具体对象得类似Map）不然无法对应<br />
<br />当 JSON 格式是 `[]` 表示数组，Java 中一般不直接使用数组，而是更方便的 `List`<br />
<br />
<br />
<br />

<a name="FTGcj"></a>
## API调用

- API全称Application Programming Interface，应用程序接口，API一般是指一些预先定义的函数,目的是可以为开发人员快速访问某一程序，而无需了解和访问源码，或理解它内部工作机制的细节。
- 简单的讲，`API`可以快速调用某个程序。本质上就是一个`URL`，开头也是`http`(或`https` )，只是返回的内容有明显的区别，没有大量多余的字符，`API`返回的内容统称为`数据`
- `URL` 的 路径（英文称作`path`）部分就是函数，而函数的参数就等同于 `URL` 的参数（英文称作`paramter`或简称`param`）。
<a name="QjtBw"></a>
### 

- 常说的 `API` 有两种：
   1.  调用别的代码接口；
   1.  调用一个 `URL`（需要发 `HTTP` 请求）。

这两种都是 `API` ，在网络编程的场景下，`API` 经常指的是第二种。无论哪一种，简言之，都是触发一个功能，取得相应的结果
<a name="eScZa"></a>
### 


<a name="EFXoK"></a>
### Get请求 - 无参数（抓取网站内容）

- 首先，我们需要安装一个库: `okhttp3`，这是一个非常流行的 `HTTP` 库，可以简单、快速的实现 `HTTP `调用
- 安装`okhttp3`的方式是在`pom.xml`文件中增加依赖
- 唯一的`<dependencies>`标签中，包含多个`<dependency>`标签，每一个`<dependency>`标签表示一个依赖库。书写时要注意嵌套顺序
```java
<!-- https://mvnrepository.com/artifact/com.squareup.okhttp3/okhttp -->
<dependencies>
      <dependency>
        <groupId>com.squareup.okhttp3</groupId>    
        <artifactId>okhttp</artifactId>    
        <version>4.1.0</version>    
      </dependency>  
</dependencies>


```


```java
package com.youkeda.test.http;

import java.io.IOException;
import okhttp3.Call;
import okhttp3.OkHttpClient;
import okhttp3.Request;

public class GetPage {

  /**
   * 根据输入的url，读取页面内容并返回
   */
  public String getContent(String url) {
    // okHttpClient 实例
    OkHttpClient okHttpClient = new OkHttpClient();
    // 定义一个request
    Request request = new Request.Builder().url(url).build();
    // 使用client去请求
    Call call = okHttpClient.newCall(request);
    // 返回结果字符串
    String result = null;
    try {
      // 获得返回结果
      result = call.execute().body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }

  public static void main(String[] args) {
    GetPage getPage = new GetPage();
    String url = "https://www.ustc.edu.cn/";
    String content = getPage.getContent(url);
  
    System.out.println("call " + url + " , content=" + content);
  }
}

```


<a name="apzTn"></a>
### Get请求 - 有参数

- 与无参数的请求区别在`URL`包不包含参数
- ` String url = "https://api.apiopen.top/getJoke?page=1&count=2&type=video";`
<a name="QuWEy"></a>
### post()方法

<br />`okhttp3`库也支持`POST`操作。调用`API`属于`GET`操作。不同的是，`POST`操作时，数据不是放在`URL`中的，而是放在表单中提交的。所以需要构建一个`FormBody`表单对象<br />

```java
package com.youkeda.test.http;

import java.io.IOException;
import java.util.Map;
import java.util.HashMap;
import okhttp3.Call;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.FormBody;
import okhttp3.FormBody.Builder;

public class FormPoster {

  /**
   * 向指定的 url 提交数据
   */
  public String postContent(String url, Map<String, String> formData) {
    // okHttpClient 实例
    OkHttpClient okHttpClient = new OkHttpClient();

    //post方式提交的数据
    Builder builder = new FormBody.Builder();
    // 放入表单数据
    for (String key : formData.keySet()) {
      builder.add(key, formData.get(key));
    }
    // 构建 FormBody 对象
    FormBody formBody = builder.build();
    // 指定 post 方式提交FormBody
    Request request = new Request.Builder().url(url).post(formBody).build();

    // 使用client去请求
    Call call = okHttpClient.newCall(request);
    // 返回结果字符串
    String result = null;
    try {
      // 获得返回结果
      result = call.execute().body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }

  public static void main(String[] args) {
    String url = "https://gitee.com/login";
    Map<String, String> formData = new HashMap();
    formData.put("user[login]", "13587975120");

    FormPoster poster = new FormPoster();
    String content = poster.postContent(url, formData);
  
    System.out.println("API调用结果");
    System.out.println(content);
  }
}
```
<a name="91qsF"></a>
### 


<a name="WCUR1"></a>
#### POST JSON数据

<br />跟表单数据提交方法一样，也是调用`post()`方法，只是参数不再使用`FormBody`对象，而是使用`RequestBody`<br />

```java
<!-- JSON 操作库 -->
      <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>fastjson</artifactId>
        <version>1.2.62</version>
      </dependency> 
```


```java
package com.youkeda.test.http;

import com.alibaba.fastjson.JSON;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import okhttp3.Call;
import okhttp3.MediaType;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.RequestBody;

public class JsonPoster {

  // 定义提交数据的类型
  public static final MediaType JSON_TYPE = MediaType.parse("application/json; charset=utf-8");

  /**
   * 向指定的 url 提交数据，以 json 的方式
   */
  public String postContent(String url, Map<String, String> datas) {
    // okHttpClient 实例
    OkHttpClient okHttpClient = new OkHttpClient();

    // 数据对象转换成 json 格式字符串
    String param = JSON.toJSONString(datas);
    //post方式提交的数据
    RequestBody requestBody = RequestBody.create(JSON_TYPE, param);
    Request request = new Request.Builder().url(url).post(requestBody).build();

    // 使用client去请求
    Call call = okHttpClient.newCall(request);
    // 返回结果字符串
    String result = null;
    try {
      // 获得返回结果
      result = call.execute().body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }

  public static void main(String[] args) {
    String url = "https://www.fastmock.site/mock/3d95acf3f26358ef032d8a23bfdead99/api/posts";
    Map<String, String> datas = new HashMap();
    datas.put("name", "张飞");
    datas.put("secondName", "翼德");

    JsonPoster poster = new JsonPoster();
    String content = poster.postContent(url, datas);

    System.out.println("API调用结果");
    System.out.println(content);
  }
}
```

<br />
<br />

<a name="pQ1z8"></a>
### Response


<a name="DsTAo"></a>
#### `HTTP`状态码

- 200表示请求成功
- 404表示出错
```java
import okhttp3.Response;

// 执行请求
Response rep = call.execute();
// 获取响应状态码
int code = rep.code();
// 获取响应内容
String content = rep.body().string();
```


<a name="UOVf2"></a>
#### 非文本文件

<br />请求图片、`excel`等各种非字符文本文件时，需要使用`response.body().bytes();`获取返回内容
```java
	  Response response = okHttpClient.newCall(request).execute();
      byte[] bytes = response.body().bytes();  
      System.out.println("图片大小为：" + bytes.length + " 字节");
```


<a name="gKb4O"></a>
#### 解析JSON对象
对于返回值为`JSON`格式的`API`，需要解析调用结果，
```json
{
  "code": 0,
  "data": {
    "ip": "117.89.35.58",
    "country": "中国",
    "area": "",
    "region": "江苏",
    "city": "南京",
    "county": "XX",
    "isp": "电信",
    "country_id": "CN",
    "area_id": "",
    "region_id": "320000",
    "city_id": "320100",
    "county_id": "xx",
    "isp_id": "100017"
  }
}
```
```java
Map contentObj = JSON.parseObject(content, Map.class);
Map dataObj = (Map)contentObj.get("data");
String city = dataObj.get("city").toString();
```


<a name="AZggX"></a>
### HTTP header
<a name="Lj0pT"></a>
#### User - Agent
`User-Agent`是存放在`Headers` 中的一种数据信息。作用是，在指定`URL`发送请求的时候，告诉服务端当前用户的浏览器类型、版本，甚至操作系统、CPU等非隐私的`技术信息`<br />
<br />`win7 + chorome` 的模拟环境：<br />`Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/14.0.835.163 Safari/535.1`
<a name="sZJx9"></a>
#### Referer
图片防盗链<br />解决办法：要把`Referer`信息设置为图片原始使用的网站
<a name="VLzUf"></a>
#### Host
`Host`请求头指明了请求将要发送到的服务器主机名和端口号。<br />如果没有包含端口号，会自动使用被请求服务的默认端口（比如HTTPS URL使用443端口，HTTP URL使用80端口）<br />
<br />`Host`的值一定是一个域名且不带协议头<br />

```java
    // 定义一个request
    Request request = new Request.Builder()
        .url(url)
        .addHeader("User-Agent", "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36")
        .addHeader("Referer", "https://www.douban.com/")
        .addHeader("Host", "www.douban.com")
        .build();
```

<br />

<a name="NjLFC"></a>
## 下载文件、图片


- `Java`中写文件分三个步骤
   -     `创建对象`  --》 `写入内容`  --》 `关闭写入操作`
<a name="gdgAL"></a>
### 写入文本文件

- `File`是文件类，`Filewriter`是用来给文件写入内容的类。
```java
import java.io.File;
import java.io.FileWriter;

// 文件对象
File file = new File("foo.txt");

// 写入内容
FileWriter fileWritter = new FileWriter(file.getName());
fileWritter.write(content);

// 关闭
fileWritter.close();
```


<a name="3Otia"></a>
### 写入二进制文件（excel、图片）

- 与写入文本内容不同，写入二进制内容，需要用`FileoutputStream`
- 需要刷新并关闭！！！
```java
//假设文件数据的变量是byte[] data;
import java.io.File;
import java.io.FileOutputStream;

// 文件对象
File file = new File("china-city-list.xlsx");

// 写文件
FileOutputStream fos = new FileOutputStream(file);
fos.write(data);

// 必须刷新并关闭
fos.flush();
fos.close();
```

<br />

<a name="H9pL0"></a>
### 解析excel


<a name="QvME2"></a>
#### 依赖库`easyexcel`
```java
<dependency>
  <groupId>com.alibaba</groupId>
  <artifactId>easyexcel</artifactId>
  <version>2.1.6</version>
</dependency>
```
<a name="aekQl"></a>
#### 调用库

- `excel`文件是多`sheet`模式的，每个`sheet` 实际上是一个表格，表格又分为行和列
   - 所以解析路径为`sheet->行->列`      `0,0,0`表示`第一个sheet`、`第一行`、`第一列`



- Map
```java
import com.alibaba.excel.EasyExcel;
import java.util.Map;
import java.util.List;

// EasyExcel.read("file")方法读取文件  
// 用.sheet(0)方法解析第一个工作表
// doReadSync() 表示同步方式读取文件内容，返回一个内容集合List
List<Map<Integer, String>> sheetDatas = EasyExcel.read("xzq_201907.xlsx").sheet(0).doReadSync();
// List 中每个元素表示一行
for (Map<Integer, String> rowData : sheetDatas) {
  // Map 中用序号指代每一列
  for (Integer index : rowData.keySet()) {
    // 列值
    String columnValue = rowData.get(index);
  }
}
```


<a name="0XnE1"></a>
#### 自定义类

- 自定义的类要多调用一个方法`.head(DemoData.class)`，DemoData就是自定义的类
   - 一个DemoData表示一行数据，类内每个属性表示一列的各个值



- Map更灵活，自定义类更直观易理解。
   - 一般列数不多（不超过10个）、不会变化，用自定义类



- DemoData属性定义的顺序必须与列顺序保持一致



<a name="bS1Qo"></a>
## cookie


- 如果`API`、`网页`、`文件`等内容需要登录才能访问，就需要`cookie`
- 所谓cookie，是存储在客户端浏览器中的一段文本内容。以`key=value` (数据名称、数据值) 的格式存储一条数据;多条数据之间用分号;(英文半角)分开。
- 由于各种浏览器都对cookie大小和数量有限制，所以cookie目前的核心功能是存储登录数据;额外可以存储一些小数据，比如是否登录=true;昵称=张三这样的内容不大的数据。
- 弊端是`cookie`是存放在客户端浏览器的，是临时的。


<br />

<a name="wXjOb"></a>
## session
```java
package com.youkeda.test.http;

import java.io.IOException;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import okhttp3.Cookie;
import okhttp3.CookieJar;
import okhttp3.FormBody;
import okhttp3.FormBody.Builder;
import okhttp3.HttpUrl;
import okhttp3.OkHttpClient;
import okhttp3.Request;

public class PageLoginer {

  // 用 CookieJar 实现 cookie 的存储，便于登录后请求其它 URL 可以复用
  private static final OkHttpClient okHttpClient = new OkHttpClient.Builder()
      .cookieJar(new CookieJar() { //匿名类
        private final HashMap<String, List<Cookie>> cookieStore = new HashMap<>();

        @Override
        public void saveFromResponse(HttpUrl url, List<Cookie> cookies) {
          cookieStore.put("mtime.com", cookies);
          System.out.println("[saveFromResponse]url.host()=" + url.host());
        }

        @Override
        public List<Cookie> loadForRequest(HttpUrl url) {
          System.out.println("[loadForRequest]url.host()=" + url.host());
          List<Cookie> cookies = cookieStore.get("mtime.com");
          return cookies != null ? cookies : new ArrayList<>();
        }
      })
      .build();

  public String postContent(String url, Map<String, String> formData) {
    //post方式提交的数据
    Builder builder = new FormBody.Builder();
    // 放入表单数据
    for (String key : formData.keySet()) {
      builder.add(key, formData.get(key));
    }
    // 构建 FormBody 对象
    FormBody formBody = builder.build();
    // 指定 post 方式提交FormBody
    Request request = new Request.Builder()
        .url(url)
        .post(formBody)
        .addHeader("User-Agent",
            "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36")
        .addHeader("Referer",
            "https://passport.mtime.com/member/signin/?redirectUrl=http%3A%2F%2Fwww.mtime.com%2F")
        .addHeader("Host", "passport.mtime.com")
        .build();

    // 返回结果字符串
    String result = null;
    try {
      result = okHttpClient.newCall(request).execute().body().string();
    } catch (IOException e) {
      System.out.println("request " + url + " error . ");
      e.printStackTrace();
    }
    return result;
  }

  public static void main(String[] args) {
    // 登录页面 url
    String url = "https://passport.mtime.com/member/signinLogin";
    // 登录表单数据
    Map<String, String> formData = new HashMap();
    formData.put("loginEmailText", "13777467803");
    formData.put("loginPasswordText", "aa787bc9cc97ba5d27cc042ecffe1489");
    formData.put("isvcode", "true");
    formData.put("isAutoSign", "false");

    PageLoginer asker = new PageLoginer();
    String content = asker.postContent(url, formData);

    System.out.println(content);
  }
}
```

<br />

<a name="UMMrV"></a>
### 复用session

<br />

```java
package com.youkeda.test.http;

import java.io.IOException;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;
import okhttp3.Cookie;
import okhttp3.CookieJar;
import okhttp3.FormBody;
import okhttp3.FormBody.Builder;
import okhttp3.HttpUrl;
import okhttp3.OkHttpClient;
import okhttp3.Request;

public class PageLoginer {

  // 用 CookieJar 实现 cookie 的存储，便于登录后请求其它 URL 可以复用
  private static final OkHttpClient okHttpClient = new OkHttpClient.Builder()
      .cookieJar(new CookieJar() {
        private final HashMap<String, List<Cookie>> cookieStore = new HashMap<>();

        @Override
        public void saveFromResponse(HttpUrl url, List<Cookie> cookies) {
          cookieStore.put("mtime.com", cookies);
          //System.out.println("[saveFromResponse]url.host()=" + url.host());
        }

        @Override
        public List<Cookie> loadForRequest(HttpUrl url) {
          //System.out.println("[loadForRequest]url.host()=" + url.host());
          List<Cookie> cookies = cookieStore.get("mtime.com");
          return cookies != null ? cookies : new ArrayList<>();
        }
      })
      .build();

  /**
   * 向指定的 URL 提交数据，并返回提交后的结果
   */
  public String postContent(String url, Map<String, String> formData) {
    //post方式提交的数据
    Builder builder = new FormBody.Builder();
    // 放入表单数据
    for (String key : formData.keySet()) {
      builder.add(key, formData.get(key));
    }
    // 构建 FormBody 对象
    FormBody formBody = builder.build();
    // 指定 post 方式提交FormBody
    Request request = new Request.Builder()
        .url(url)
        .post(formBody)
        .addHeader("User-Agent",
            "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36")
        .addHeader("Referer",
            "https://passport.mtime.com/member/signin/?redirectUrl=http%3A%2F%2Fwww.mtime.com%2F")
        .addHeader("Host", "passport.mtime.com")
        .build();

    return doExcute(request);
  }

  /**
   * 根据输入的url，读取页面内容并返回
   */
  public String getContent(String url) {
    // 定义一个request
    Request request = new Request.Builder()
        .url(url)
        .addHeader("User-Agent",
            "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36")
        .addHeader("Host", "my.mtime.com")
        .build();

    return doExcute(request);
  }

  private String doExcute(Request request) {
    // 返回结果字符串
    String result = null;
    try {
      result = okHttpClient.newCall(request).execute().body().string();
    } catch (IOException e) {
      // 抓取异常
      System.out.println("request " + request.url() + " error . ");
      e.printStackTrace();
    }

    return result;
  }

  public static void main(String[] args) {
    PageLoginer asker = new PageLoginer();

    // 完成登录
    String url = "https://passport.mtime.com/member/signinLogin";
    // 登录表单数据
    Map<String, String> formData = new HashMap();
    formData.put("loginEmailText", "13777467803");
    formData.put("loginPasswordText", "aa787bc9cc97ba5d27cc042ecffe1489");
    formData.put("isvcode", "true");
    formData.put("isAutoSign", "false");
    String content = asker.postContent(url, formData);
    System.out.println("login result:");
    System.out.println(content);

    // 请求我的订单
    String myOrderUrl = "http://my.mtime.com/account/ecommerce/orderList/";
    String myOrderContent = asker.getContent(myOrderUrl);
    System.out.println("orderList result:");
    System.out.println(myOrderContent);
    
  }
}
```


<a name="qNQIq"></a>
## JavaMail邮件发送

- 引入依赖
```java
<dependency>
 <groupId>javax.mail</groupId>
 <artifactId>mail</artifactId>
 <version>1.4</version>
</dependency>
```


```java
package com.youkeda.email;

import java.security.Security;
import java.util.Properties;
import javax.mail.Authenticator;
import javax.mail.Message;
import javax.mail.PasswordAuthentication;
import javax.mail.Session;
import javax.mail.Transport;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;
import com.sun.net.ssl.internal.ssl.Provider;

public class Mail {

  public static void main(String[] args) {
    try {
      // 设置SSL连接、邮件环境
      Security.addProvider(new Provider());
      final String SSL_FACTORY = "javax.net.ssl.SSLSocketFactory";
      Properties props = System.getProperties();
      props.setProperty("mail.smtp.host", "smtp.qq.com");
      props.setProperty("mail.smtp.socketFactory.class", SSL_FACTORY);
      props.setProperty("mail.smtp.socketFactory.fallback", "false");
      props.setProperty("mail.smtp.port", "465");
      props.setProperty("mail.smtp.socketFactory.port", "465");
      props.setProperty("mail.smtp.auth", "true");

      // 建立邮件会话
      Session session = Session.getDefaultInstance(props, new Authenticator() {
        // 身份认证
        protected PasswordAuthentication getPasswordAuthentication() {
          return new PasswordAuthentication("xxxx@qq.com", "xxxx"); // 账户 授权码
        }
      });

      // 建立邮件对象
      MimeMessage message = new MimeMessage(session);
      // 设置邮件的发件人、收件人、主题
      // 附带发件人名字
      message.setFrom(new InternetAddress("xxxx@qq.com"));  //发件人
      message.setRecipients(Message.RecipientType.TO, "xxxx@qq.com"); // 收件人
      message.setSubject("hello");   // 主题
      // 文本部分
      message.setContent("hello world", "text/html;charset=UTF-8"); //  内容
      message.saveChanges();
      // 发送邮件
      Transport.send(message);
      // 打印成功信息
      System.out.println("发送成功");
    } catch (Exception e) {
      e.printStackTrace();
    }
  }
}

```
