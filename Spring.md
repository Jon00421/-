# Spring

<a name="KJ8D3"></a>
# Maven
Maven是一个项目管理和构建自动化工具<br />


| **目录** | **目的** |
| --- | --- |
| ${basedir} | 存放pom.xml 和所有的子目录 |
| ${basedir}pom.xml | **Maven 的项目配置文件** |
| ${basedir}/src/main/java | **项目的 java 源文件** |
| ${basedir}/src/main/resources | 项目的资源，比如 property 文件 |
| ${basedir}/src/test/java | 项目的测试类，比如 JUnit 代码 |
| ${basedir}/src/test/resources | 测试使用的资源 |

${basedir} 代表的事 Java 工程的根路径

<a name="E9vjb"></a>
## Maven 命令

1. `mvn clean compile`

编译命令，Maven 会自动扫描 src/main/java 下的代码并完成编译工作，执行完会在根目录下生成 target/classes 目录（存放所有的 class）<br />

2. `mvn clean package<br />`编译并打包命令,先执行 compile 命令，然后在执行 jar 打包命令，结果会把所有的 java 文件和资源打包成一个`jar`



3. `mvn clean install`

      执行安装命令，先执行 compile 命令，然后在执行 jar 打包命令，然后执行 install 命令安装到本地的 Maven 仓库目录里，这个目录是 `${user_home}/.m2` 

4. `mvn compile exec:java -Dexec.mainClass=${main}`

在 compile 执行完后，执行运行 Java 的命令<br />

<a name="6q8lJ"></a>
## Maven 配置文件 --- pom.xml
一个 Java 项目所有的配置都放置在 POM（Project Object Model） 文件中，大概有如下的行为：

- 定义项目的类型、名字
- 管理依赖关系
- 定制插件的



1. **Maven 坐标**
```xml
<groupId>com.youkeda.course</groupId>
<artifactId>app</artifactId>
<packaging>jar</packaging>
<version>1.0-SNAPSHOT</version>
```

2. **Maven 属性配置**
```xml
 <properties>
    <java.version>1.8</java.version>
    <maven.compiler.source>${java.version}</maven.compiler.source>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.target>${java.version}</maven.compiler.target>
</properties>
```

3. **Maven 依赖**
```xml
<dependencies>
    <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>fastjson</artifactId>
        <version>1.2.62</version>
    </dependency>
</dependencies>
```

4. **Maven 插件**
```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.8.1</version>
        </plugin>
    </plugins>
</build>
```


<a name="TFm0o"></a>
# Spring 依赖注入


<a name="6b3ld"></a>
## Annotation（注解）

1. **Target**

`java.lang.annotation.Target` 自身也是一个注解，它只有一个数组属性，用于设定该注解的目标范围，比如说可以作用于类或者方法等。因为是数组，所以可以同时设定多个范围

- 具体可以作用的类型配置在` java.lang.annotation.ElementType `枚举类中
   - ElementType.TYPE                            --- 作用于类、接口类、枚举类上
   - ElementType.FIELD                           --- 作用于类的属性上
   - ElementType.METHOD                     --- 作用于类的方法上
   - ElementType.PARAMETER                --- 作用于类的参数上



2. ** Rentention**

`java.lang.annotation.Retention `自身也是一个注解，它用于声明该注解的生命周期，简单的来说就是在 Java 编译、运行的哪个环节有效，它的值定义在`java.lang.annotation.RetentionPolicy`枚举类中

   - SOURCE:  纯注释作用
   - CLASS:  在编译阶段有效
   - RUNTIME:  在运行时有效



3. **Documented**

`java.lang.annotation.Documented` 自身也是一个注解，它的作用是将注解中的元素包含到 JavaDoc 文档中，一般情况下，都会添加这个注解的

4. **@interface**

`@interface`就是声明当前的 Java 类型是 Annotation，固定语法，就是这样写就好<br />

5. **Annotation 属性**

Annotation 的属性有点像类的属性一样，它约定了属性的类型(这个类型是基础类型：String、boolean、int、long)，和属性名称（默认名称是 value ，在引用的时候可以省略），default 代表的是默认值。<br />
<br />

<a name="lJ4ty"></a>
## Spring Bean

<br />IoC 容器是 Spring 框架最最核心的组件，没有 IoC 容器就没有 Spring 框架
> IoC（Inversion of Control，控制反转）是面向对象编程中的一种设计原则，可以用来减低计算机代码之间的耦合度


<br />在 Spring 框架当中，主要通过依赖注入DI（Dependency Injection）来实现 IoC。<br />
<br />

- Spring 主要有两种配置元数据的方式，一种是基于** XML**、一种是基于** Annotation **方案的



- `org.springframework.context.ApplicationContext` 接口类定义容器的对外服务，可以通过这个接口从 IoC 容器中得到 Bean 对象。



- Annotation 类型的 IoC 容器对应的类是

`org.springframework.context.annotation.AnnotationConfigApplicationContext`<br />这个类的构造函数有两种

      1.  AnnotationConfigApplicationContext(String ... basePackages) 根据包名实例化
      1.  AnnotationConfigApplicationContext(Class clazz) 根据自定义包扫描行为实例化



- 启动 IoC 容器

`ApplicationContext context = new AnnotationConfigApplicationContext("fm.douban");`<br />
<br />

- Spring 官方声明为 Spring Bean 的注解有如下几种：
   - `org.springframework.stereotype.Service`
   - `org.springframework.stereotype.Component`
   - `org.springframework.stereotype.Controller`
   - `org.springframework.stereotype.Repository`

只要在类上引用这类注解，都可以被 IoC 容器加载<br />

- `@Component`注解是通用的 Bean 注解，其余三个注解都是扩展自Component
- `@Service`正如这个名称一样，代表的是 Service Bean
- `@Controller`作用于 Web Bean
- `@Repository`作用于持久化相关 Bean



<a name="thh7U"></a>
## Spring Resource

- Java 工程中文件的几种情况
   1. 文件在电脑某个位置，比如说 `d:/mywork/a.doc`
   1. 文件在工程目录下，比如说 `mywork/toutiao.png`
   1. 文件在工程的 `src/main/resources` 目录下,我们在 Maven 的知识里介绍过这是 Maven 工程存放文件的地方
<a name="MlJbL"></a>
### classpath
在 Java 内部当中，一般把文件路径称为 classpath，所以读取内部的文件就是从 classpath 内读取，但classpath 指定的文件不能解析成 File 对象，可以解析成 **InputStream**，再借助 Java IO 就可以读取出来了
```xml
添加依赖 commons-io库
<dependency>
  <groupId>commons-io</groupId>
  <artifactId>commons-io</artifactId>
  <version>2.6</version>
</dependency>
```
```java
import java.io.IOException;
import java.io.InputStream;
import org.apache.commons.io.IOUtils;
public class Test {
  public static void main(String[] args) {
    // 读取 classpath 的内容
    InputStream in = Test.class.getClassLoader().getResourceAsStream("data.json");
    // 使用 commons-io 库读取文本
    try {
      String content = IOUtils.toString(in, "utf-8");
      System.out.println(content);
    } catch (IOException e) {
      // IOUtils.toString 有可能会抛出异常，需要我们捕获一下
      e.printStackTrace();
    }
  }
}
```


- 在 Spring 当中定义了一个` org.springframework.core.io.Resource` 类来封装文件，其既可以支持普通的 File 也可以支持 classpath 文件
- 并且在 Spring 中通过` org.springframework.core.io.ResourceLoader` 服务来提供任意文件的读写,你可以在任意的 Spring Bean 中引入 ResourceLoader
```java
@Service
public class FileServiceImpl implements FileService {

    @Autowired
    private ResourceLoader loader;
    
    @Override
    public String getContent(String name) {
        try {
            //通过loader
            InputStream in = loader.getResource(name).getInputStream();
            return IOUtils.toString(in,"utf-8");
        } catch (IOException e) {
           return null;
        }
    }
} 

	//服务调用
    ApplicationContext context = new AnnotationConfigApplicationContext("fm.douban");  
    FileService fileService = context.getBean(FileService.class);

	//查找classpath
    String content = fileService.getContent("classpath:data/urls.txt");

	//查找本地工程目录下文件
    String content2 = fileService.getContent("file:mywork/readme.md");

	//加载远程文件
    String content3 = fileService.getContent("https://www.zhihu.com/question/34786516/answer/822686390");

```


<a name="orfcn"></a>
## Spring Bean 的生命周期（Lifecycle）

<br />![](https://cdn.nlark.com/yuque/0/2021/svg/2999046/1612094874263-a6eb5113-c4a0-4328-aa4c-4aaef4264b5b.svg#align=left&display=inline&height=412&margin=%5Bobject%20Object%5D&originHeight=412&originWidth=162&size=0&status=done&style=none&width=162)<br />
<br />在方法上添加`@PostConstruct`注解，代表该方法在 Spring Bean 启动后会自动执行
```java
import javax.annotation.PostConstruct;

@Service
public class SubjectServiceImpl implements SubjectService {

  @PostConstruct
  public void init(){
      System.out.println("启动啦");
  }

}  
```


<a name="KzWfE"></a>
# Spring MVC
Spring MVC 是 Java Web 的一种实现框架
<a name="huszZ"></a>
## Spring Controller
一般情况下，我们会把 controller 类存放在 `control `子包里，比如这里的 `fm.douban.app.control`<br />

- **Spring Controller  技术的三个核心点**
<a name="NAVwD"></a>
### 1.Bean 的配置： Controller 注解运用
`@Controller`  Spring Controller 一般情况下不需要特意实现接口<br />

<a name="3QTk9"></a>
### 2.网络资源的加载： 加载网页

- 在 Spring Boot 应用中，一般把网页存放在 `src/main/resources/static` 目录下

（访问文件时，路径不需要额外加 `static`）

- 在 controller 中，会自动加载 static 下的html内容



<a name="T70pt"></a>
### 3.网址路由的配置： RequestMapping 注解运用
在需要提供 Web 访问的 方法上添加一个 @RequestMapping 注解就可以完成配置 <br />

```java
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.*;

@Controller
public class HelloControl {
	//当网页为“/hello”时，自动执行所属方法
    @RequestMapping("/hello")
    public String say(){
        return "html/hello.html";
    }

}
```


<a name="3zIZI"></a>
## Get Request
**get请求参数**

- 定义参数
```java
@RequestMapping("/songlist")
    public String index( @RequestParam("id") String id){
        return "html/songList.html";
    }
```
参数 `"id"`  必须要和 URL 的 **param key** 一样<br /> 根据URL中的`"id"`，自动匹配到对应的 `@RequestParam("id")` ，并找到对应的方法执行。

- 获取多个参数

`@RequestParam("id") String id,  @RequestParam("pageNum") int pageNum`<br />
<br />
<br />`@RequestMapping` 用于解析 URL 请求路径，默认是支持所有的 Http Method 的。<br />`@GetMapping` 明确指定 method ，更加安全<br />

- 非必须传递参数

`@RequestParam(name="pageNum",required = false) int pageNum`<br />

<a name="cAuez"></a>
### 输出 JSON 数据（API）
```java
@GetMapping("/api/foos")
@ResponseBody
public String getFoos(@RequestParam("id") String id) {
  return "ID: " + id;
}
```
`@ResponseBody` 的作用是将 controller 的方法返回的对象通过适当的转换器转换为指定的格式之后，写入到 response 对象的 body 区，通常用来返回 JSON 数据或者是 XML 数据

`@ResponseBody`是作用在方法上的，@ResponseBody 表示该方法的返回结果直接写入 HTTP response body 中，一般在异步获取数据时使用【也就是AJAX】。<br />注意：在使用 @RequestMapping后，返回值通常解析为跳转路径，但是加上 @ResponseBody 后返回结果不会被解析为跳转路径，而是直接写入 HTTP response body 中。 比如异步获取 json 数据，加上 @ResponseBody 后，会直接返回 json 数据。@RequestBody 将 HTTP 请求正文插入方法中，使用适合的 HttpMessageConverter 将请求体写入某个对象。
<a name="FykNv"></a>
# Spring Template --- Thymeleaf

<br />**Thymeleaf** 是一个模板框架，它可以支持多种格式的内容动态渲染非常强大，它天然和 HTML 是相融合的。

- 添加Maven依赖
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```

- 数据传递

导入 Model 类 `import org.springframework.ui.Model;`<br />

- 模板文件

 Spring MVC 中的模板文件固定存放在 `src/main/resources/templates`（后缀自动匹配）<br />        在此目录下放置了文件就代表要使用 Thymeleaf<br />

<a name="ubqlz"></a>
## Thymeleaf 变量
`th: `开头的标签属性，那么就代表使用的是 Thymeleaf 语法 <br />
<br />`th:text` 语法的作用就是会动态替换掉 html 标签的内部内容<br />例如： `<span th:text="${msg}">Hello</span>`  （Hello会被替换掉）<br />
<br />`model.addAttribute("msg",str);`

- 第一个参数设置的就是上下文变量名（变量名是可以随便定义）
- 第二参数设置的是变量值（可以是任意的对象）



<a name="QtjhP"></a>
## Thymeleaf 循环
`th:each`
```html
<ul th:each="song : ${songs}">
  <li th:text="${song.name}">歌曲名称</li>
</ul>
```
另一种写法
```html
<ul th:each="song,it: ${songs}">
  <li>
    <span th:text="${it.count}"></span>
    <span th:text="${song.name}"></span>
  </li>
</ul>
```
it 作为可选参数，可通过 it 对象来获取更多关于统计的需求

- `it.index`

当前迭代对象的 index（从 0 开始计算）从 0 开始显示行数

- `it.count`

当前迭代对象的 index（从 1 开始计算）

- `it.size`

被迭代对象的大小，可获取列表长度

- `it.current`

当前迭代变量，等同与上面的 song

- `it.even/odd`

布尔值，当前循环是否是偶数/奇数（从 0 开始计算）

- `it.first`

布尔值，当前循环是否是第一个

- `it.last`

布尔值，当前循环是否是最后一个<br />
<br />

<a name="vU11V"></a>
## Thymeleaf 表达式


<a name="ePPBp"></a>
#### 字符串处理

- `<span th:text="'00:00/'+${totalTime}"></span>`

使用 `'` 包围住 00:00/ 把其变成 Java 字符串，再使用 `+` 拼接成新的字符串了<br />

- `<span th:text="|00:00/${totalTime}|"></span>`

 用 `|` 包围住字符串<br />

<a name="PZtIE"></a>
### 数据转换

<br />**dates / temporals**<br />处理`LocalDate`和`LocalDateTime`类，添加依赖会自动添加一个新的工具类 `temporals`（ `${#工具类}` ）
```xml
<dependency>
  <groupId>org.thymeleaf.extras</groupId>
  <artifactId>thymeleaf-extras-java8time</artifactId>
  <version>3.0.4.RELEASE</version>
</dependency>
```
dates 和 temporals 支持的方法是一样的，只是支持的类型不同，dates 支持的是 Date 类，temporals 支持的是 LocalDate 和 LocalDateTime
```xml
<p th:text="${#temporals.format(dateVar, 'yyyy年MM月dd日 HH时mm分ss秒')}"></p>
<p th:text="${#dates.format(dateVar, 'yyyy年MM月dd日 HH时mm分ss秒')}"></p>
```
**<br />**strings**<br />`#strings` 支持字符串的数据处理<br />

- `${#strings.toUpperCase(name)}`

把字符串改成全大写

- `${#strings.toLowerCase(name)}`

把字符串改成全小写

- `${#strings.arrayJoin(array,',')}`

把字符串数组合并成一个字符串，并以`,`连接，比如`["a","b"]`执行后会变成 `a,b`

- `${#strings.arraySplit(str,',')}`

把字符串分隔成一个数组，并以`,`作为分隔符，比如`a,b`执行后会变成`["a","b"]`；如果`abc`没有匹配到，执行后会变         成`["abc"]`

- `${#strings.trim(str)}`

把字符串去空格，左右空格都会去掉

- `${#strings.length(str)}`

得到字符串的长度，也支持获取集合类的长度

- `${#strings.equals(str1,str2)}`

比较两个字符串是否相等

- `${#strings.equalsIgnoreCase(str1,str2)}`

忽略大小写后比较两个字符串是否相等<br />

> 各内置对象包含哪些方法[https://www.jianshu.com/p/d8bc610c4400](https://www.jianshu.com/p/d8bc610c4400)



<a name="dCPaP"></a>
### 内联表达式
`[[变量]]` 支持我们直接在 HTML 中调用变量<br />例：`<span>Hello [[${msg}]]</span>`<br />`[[]]`是用来替代 `th:text` 的，不能替代所有的`th:`标签<br />

<a name="WwQsH"></a>
## Thymeleaf 条件语句
`th:if`  if 表达式的值是 **ture **的情况下就会执行渲染<br />`<span th:if="${user.sex == 'male'}">男</span>`<br />
<br />`th:if` 条件判断除了判断 boolean 值外，Thymeleaf 还认为如下表达式为 true:

- 值非空
- 值是非0数字
- 值是字符串，但是不是 `false`, `off `or `no`
- 值不是 boolean 值，数字，character 或 字符串


<br />
<br />`th:unless`  表达式的值是 **false **的情况下就会执行渲染<br />`<span th:unless="${user.sex == 'male'}">女</span>`<br />

<a name="ZWqGK"></a>
### strings 逻辑判断
**`isEmpty()`**
```html
//检查字符串变量是否为空（或者为 null)，在检查之前会先执行 trim() 操作，去掉空格
${#strings.isEmpty(name)}
// 数组
${#strings.arrayIsEmpty(name)}
// 集合
${#strings.listIsEmpty(name)}
```

<br />**`contains()`**<br />`${#strings.contains(name,'abc')}`<br />例：`<p th:if="${#strings.contains(str1,'人')}">匹配到人这个字啦</p>`<br />
<br />常用：

- `${#strings.containsIgnoreCase(name,'abc')}`

先忽略大小写字母，然后去判断是否包含指定的字符串

- `${#strings.startsWith(name,'abc')}`

判断字符串是不是以 abc 开头的

- `${#strings.endsWith(name,'abc')}`

判断字符串是不是以 abc 结束的
<a name="Xrbvl"></a>
## Thymeleaf 表单
```java
@Controller
public class BookControl {
  //缓存所有书籍数据
  private static List<Book> books = new ArrayList<>();

  @GetMapping("/book/add.html")
  public String addBookHtml(Model model){
    return "addBook";
  }

  @PostMapping("/book/save")
  public String saveBook(Book book){
    books.add(book);
    return "saveBookSuccess";
  }

}
```
<a name="UN6YK"></a>
### 
<a name="xtFfz"></a>
## Spring Validation


<a name="Yer6M"></a>
### JSR 380
**JSR**是 Java Specification Requests 的缩写，意思是 Java 规范提案。是指向JCP (Java Community Process)提出新增一个标准化技术规范的正式请求。<br />**JSR 380** 其实就是 Bean Validation 2.0 ，这个就是 Bean 验证的规范<br />

- 添加依赖
```xml
<dependency>
  <groupId>jakarta.validation</groupId>
  <artifactId>jakarta.validation-api</artifactId>
  <version>2.0.1</version>
</dependency>
```
<a name="h0g3e"></a>
#### 
<a name="F5hON"></a>
### Validation 注解

- `@NotNull`

不允许为 null 对象

- `@AssertTrue`

是否为 true

- `@Size`

约定字符串的长度

- `@Min`

字符串的最小长度

- `@Max`

字符串的最大长度

- `@Email`

是否是邮箱格式

- `@NotEmpty`

不允许为null或者为空，可以用于判断字符串、集合，比如 Map、数组、List

- `@NotBlank`

不允许为 null 和 空格
> 大多数情况下，我们建议使用 NotEmpty 替代 NotNull、NotBlank



```java
import com.bookstore.model.User;
import org.springframework.stereotype.Controller;
import org.springframework.validation.BindingResult;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;

import javax.validation.Valid;

@Controller
public class UserControl {

    @GetMapping("/user/add.html")
    public String addUser() {
        return "user/addUser";
    }

    @PostMapping("/user/save")
    public String saveUser(@Valid User user, BindingResult errors) {
        if (errors.hasErrors()) {
            // 如果校验不通过，返回用户编辑页面
            return "user/addUser";
        }
        // 校验通过，返回成功页面
        return "redirect:/user/list.html";
    }

}
```

- @Valid 完整的包路径是 `javax.validation.Valid`



- BindingResult 类的路径是 `org.springframework.validation.BindingResult`

BindingResult 对象的 `hasErrors` 方法可以用于判断校验成功还是失败

   - 如果失败，回到添加用户的页面
   - 如果成功，显示成功页面
- `redirect: `这个用于跳转到某一个页面网址，如果是同一个域名，你可以省略域名，直接写 path，比如这里的 `/user/list.html`


<br />
<br />**th:object**
> `th:object` 用于替换对象，这样就不需要每次都编写 `user.xxx` 可以直接操作 `xxx` 了

```html
<form action="/user/save" th:object="${user}" method="POST">
  ...
</form>
```
**th:classappend**
```html
<div th:classappend="${#fields.hasErrors('name')} ? 'error' : ''">
</div>
```
**注意 **`${#fields.hasErrors('key')}` 这个语法是专门为验证场景提供的，这里的 `key` 就是对象的属性名称，比如 User 对象的 name、age、email 等<br />
<br />**th:errors**
```html
<p th:if="${#fields.hasErrors('age')}" th:errors="*{age}"></p>
```
**注意：**这里的 `*`由于我们在 form 中使用了` th:object="${user}"`,所以我们就可以通过 `*{age}` 来获取具体的属性值<br />
<br />**th:field**<br />显示上一次输入的内容
```html
<div th:classappend="${#fields.hasErrors('age')} ? 'error' : ''">
  <label>年龄:</label>
  <input type="text" th:field="*{age}" />
  <p th:if="${#fields.hasErrors('age')}" th:errors="*{age}"></p>
</div>
```


<a name="mGsi2"></a>
## Thymeleaf 布局（Layout）
**layout **解决的是模板复用的问题，例如一些网站的导航，底部是重复使用的，可以做成布局组件直接套用<br />
<br />`th:include + th:replace` 方案<br />
<br />**th:include="::content"**<br />**<br />`::content` 指的是选择器，这个选择器指的就是加载当前页面的 `th:fragment`的值。<br />当页面渲染的时候，布局会合并 content 这个 fragment 内容一起渲染<br />
<br />
<br />**th:replace="layout"<br />**<br />指定布局的名称，一旦声明后，页面会被替换成 layout 的内容，这个`"layout"`指的是 `templates/layout.html`<br />
<br />**th:fragment="content"**<br />fragment是片段的意思，当页面渲染的时候，可以通过选择器指定使用这个片段。在上面 layout.html 文件的 `th:include="::content"` 指定的就是这个值
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
      th:replace="layout">
<div th:fragment="content">
  <h2>用户列表</h2>
    .....  
    .....
</div>
</html>
```

<br />

<a name="fWk6O"></a>
# Spring Boot

- Spring Boot 极大的降低了 Java Web 工程的创建和运行和部署的难度。
- 创建 Spring Boot 的工程  --- [https://start.spring.io/](https://start.spring.io/)
<a name="UrAH0"></a>
## Spring Boot ComponentScan
加 `@SpringBootApplication` **注解**的类是**启动类**，是整个系统的启动入口。<br />
<br />假设 `fm.douban.app.AppApplication` 类是启动类。Spring Boot 框架就会默认**扫描** `fm.douban.app` 包（启动类所在的包）及其所有子包（`fm.douban.app.*`、`fm.douban.app.*.*`）进行**解析**。若不是子包（平级），则不会自动实例化 `Bean`。<br />**解决办法：**<br />为启动类的注解 `@SpringBootApplication` 加一个参数，告知系统需要额外扫描的包：
```java
@SpringBootApplication(scanBasePackages={"fm.douban.app", "fm.douban.service"})
public class AppApplication {
  public static void main(String[] args) {
    SpringApplication.run(AppApplication.class, args);
  }
}
```

- 参数名是：`scanBasePackages`；
- 参数值是一个字符串数组，用于指定**多个**需要额外自动扫描的包。需要把所有的待扫描的包的前缀都写入。


<br />**另一办法：**<br />如果不是 `Spring Boot` 启动类，可以使用独立的注解 `@ComponentScan` ，作用也是一样的，用于指定多个需要额外自动扫描的包。
```java
@ComponentScan({"fm.service", "fm.app"})
public class SpringConfiguration {
  ... ...
}
```
<a name="EGxqX"></a>
## Spring Boot Logger 运用
日志系统的两大优势：<br />

1. 日志系统可以轻松的控制日志是否输出。例如淘宝这样超大型的网站，在开发阶段需要打印出调试信息，但是发布到正式环境就不能打印了，因为每天几十几百亿的访问量，大量调试信息到导致磁盘撑爆。这时候就需要控制日志的输出，而不是修改所有的代码。
2. 日志系统可以灵活的配置日志的细节，例如输出格式，通常在日志输出时，需要自动附带输出日志发生的时间、打印日志的类名等信息，这样能很方便的观察日志分析问题。
<a name="jfbF6"></a>
## 1.配置
修改 `Spring Boot` 系统的标准配置文件： `application.properties`（在项目的 `src/main/resources/` 目录下），增加日志级别配置：<br />`logging.level.root=info`  表示所有日志（`root`）都为 `info` 级别。<br />
<br />也可以为不同的的包定义不同的级别，例如<br />`logging.level.fm.douban.app=info`  就表示 fm.douban.app 包及其子包中的所有的类都输出 info 级别的日志。

| **优先级** | **级别** | **含义和作用** |
| :--- | :--- | :--- |
| 最高 | ERROR | 错误信息日志 |
| 高 | WARN | 暂时不出错但高风险的警告信息日志 |
| 中 | INFO | 一般的提示语、普通数据等不要紧的信息日志 |
| 低 | DEBUG | 进开发阶段需要关注的调试信息日志 |

**级别的作用**<br />`logging.level.root=error` 意味着 不输出 **更低 **优先级的 WARN、INFO、DEBUG 日志， 只输出 ERROR 日志。<br />
<br />`logging.level.root=warn` 意味着 不输出 **更低 **优先级的 INFO、DEBUG 日志， 只输出 WARN 和 **更高 **优先级的 ERROR 日志。以此类推。<br />
<br />在开发阶段配置为 `DEBUG`，在项目发布时调整为 `INFO` 或更高级别，即可做到不改代码而控制只输出关心的日志。<br />

<a name="kdEMG"></a>
## 2.编码


```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.web.bind.annotation.RestController;
import javax.annotation.PostConstruct;

@RestController
public class SongListControl {
    // 定义类变量 LOG 的语句属于固定写法，只需要在不同的类中，
    // 修改 getLogger() 方法参数为当前的类名即可。这样就能识别每段日志的来源。
    private static final Logger LOG = LoggerFactory.getLogger(SongListControl.class);

    @PostConstruct
    public void init(){
        LOG.info("SongListControl 启动啦");  //error()  warn()  info()  debug();
    }
}
```
<a name="Y4wXe"></a>
## 
<a name="KxDNY"></a>
## Spring Boot Properties
`application.properties` 配置文件，固定位置（在项目的` src/main/resources/` 目录下）、固定名字的文件，框架会自动加载并解析这个配置文件<br />

<a name="gNDL3"></a>
## 配置文件格式
每一行是一条配置项：**配置项名称=配置项值**。<br />例如：<br />`logging.level.root=info`<br />`logging.level.fm.douban.app=info`
> 注意：等号两边不要加空格，要写紧凑一些。


<br />为了方便阅读和维护，书写配置文件时推荐遵守如下约定：

- 配置项名称能准确表达作用、含义，以点 . 分割单词，
- 相同前缀的配置项写在一起，
- 不同前缀的配置项之间空一行，



<a name="TyWcb"></a>
## 配置的意义
配置的主要作用，是把**可变**的内容从代码中剥离出来，做到在不修改代码的情况下，方便的修改这些可变的或常变的内容。这个过程称之为避免**硬编码**、做到解**耦**。<br />通常跟项目运行相关的上下文环境，比如 端口号、路径 等可能变化信息，是可变的或常变的内容。

<a name="mLIS5"></a>
## 自定义配置项


```java
// application.properties 配置文件中加入自定义的配置项
song.name=God is a girl

// 项目启动的时候，Spring 系统会自动把 application.properties 配置文件中的 song.name 的值，
// 赋值给 SongListControl 对象实例的 songName 变量。
import org.springframework.beans.factory.annotation.Value;
public class SongListControl {
    @Value("${song.name}")
    private String songName;
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
<br />
<br />
<br />
<br />
<br />

