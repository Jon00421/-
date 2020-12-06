# README

<a name="8T83Y"></a>
# Git命令


- 查看是否生成SSH~~:```git
  cat ~/.ssh/id_rsa.pub
```

- 生成SSH:```git
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- 告诉git你的名字邮箱```git
  git config --global user.name "your_name"
   git config --global user.email "your_email@example.com"
```

- 克隆仓库```git
  git clone 仓库地址（SSH地址）
```

- git提交三部曲```git
 1. git add (git add -A)
 2. git commit (git commit -m "本次提交的修改的备注")
 3. git push
    1. 第1次提交到本分支  （git push origin main）
    2. 第2-n次提交到本分支 （git push）
    3. 提交到其他分支  （git push origin b）
```

- 代码冲突```git
  git pull（抓取远程仓库的内容，协同开发时，每一次提交之前，git pull）
```




<a name="2sYGq"></a>
# Java


- java编译过程并不生成机器语言，而是生成字节码
   - 源代码--编译器--字节码--解释器（JVM）--exe
- 块注释语法```java
/**

 *我是块注释
 
 */
```




<a name="Jl5V2"></a>
## 字符串常用方法

---

- **charAt(index)**
   - 取出字符串中下标为index的字
- **trim()**
   - 清除字符串左右两边空格
- **indexOf("字符串",("开始索引值"))**
   - indexOf查找字符串方法接受一个String字符串，返回查找从开始索引值后第一个匹配到的int类型坐标
- **substring(开始索引,(结束索引))**
   - 字符串拼接substring 取出开始索引至结束索引的内容
- **startsWith("字符串")/endsWith("字符串")**
   - 字符串开始和结束内容判断
- **replaceAll("要替换的值","新值")**
   - 字符串替换，执行后会得到一个新的字符串，原始字符串不会改变(若新值为空格，则可实现删除功能)
- **split("分割字符串")**
   - 字符串分割，"分割字符串"可以是字符串也可以是特殊符号( . | * 这三个字符如果作为分割符，需要加上\ \ 例如str.split("\ \ |") )```java
public static void main(String[] args){
   String text = "姓名|年龄|性别\n张三|20|男\n李四|18|男\n小花|18|女";

 // 使用 split 进行换行符的分割，得到一个新的数组对象
 String[] data = text.split("\n");

 // 因为第一行是标题不是数据，所以我们需要把长度-1
 // (注意要使用小括号包围，因为要先计算长度再组合字符串)
 System.out.println("共有:"+(data.length-1)+" 条记录");

 // 忽略第一行标题数据，所以我们把 i 设为1，从第二条记录开始
 for(int i=1;i<data.length;i++){
   // 使用 \\| 进行字符串分割，得到一个新数组对象
   String[] lines = data[i].split("\\|");
   System.out.println("姓名:"+lines[0]+" 年纪:"+lines[1]+" 性别:"+lines[2]);
 }
}


  //结果
  共有:3 条记录
  姓名:张三 年纪:20 性别:男
  姓名:李四 年纪:18 性别:男
  姓名:小花 年纪:18 性别:女
```

- **toUpperCase()/toLowerCase()**
   - 大小写转化
- **equals("被比较的字符串")**
   - 字符串比较
- **将字符串变成数字**
   - Integer.parseInt("字符串")
- **数字转化为字符串**
   1. 使用空字符串加数字(String str = "" + a)
   2. 使用valueOf强制转化(String str = String.valueOf(a))

---

<a name="t508d"></a>
## 日期


- 日期类 (import java.time.LocalDate)
- 日期格式类(import java.time.format.DateTimeFormatter)
- 年-月-日 时:分:秒 == yyyy-MM-dd HH:mm:ss
- 日期时间和字符串的转化```java
  import java.time.LocalDate;
  import java.time.format.DateTimeFormatter;
  
  public class DateTest6 {
  
    public static void main(String[] args) {
  
      LocalDate time = LocalDate.now();
  
      // 创建一个格式化方式
      DateTimeFormatter df = DateTimeFormatter.ofPattern("yyyy/MM/dd");
      // 执行时间的格式化处理，得到期望格式的时间字符串
      String timeStr = df.format(time);
      // 打印时间
      System.out.println(timeStr);
  
    }
  }
```

- 获取日期时间具体的值```
   import java.time.LocalDate;

   public class DateTest7 {

     public static void main(String[] args) {

       LocalDate time = LocalDate.now();

       // 得到当前时间所在年
       int year = time.getYear();

       // 得到当前时间所在月
       int month = time.getMonth().getValue();

       // 得到当前时间在这个月中的天数
       int day = time.getDayOfMonth();

       // 得到当前时间所在星期数
       int dayOfWeek = time.getDayOfWeek().getValue();

     }
    }
```

- 字符串转化为日期时间(LocalDate.parse(date))```
   import java.time.LocalDate;

   public class DateTest8 {

     public static void main(String[] args) {
       // 定义一个时间字符串，日期是2019年1月1日
       String date = "2019-01-01";

       // 把字符串转化位 LocalDate 对象，并得到字符串匹配的日期
       LocalDate date2 = LocalDate.parse(date);
       // 打印出日期
       System.out.println(date2.toString());
     }
}
```

- 若字符串日期格式不是yyyy-MM-dd，就得借助DateTimeFormatter<br />(LocalDate.parse(date,df))```
   import java.time.LocalDate;
   import java.time.format.DateTimeFormatter;

   public class DateTest81 {

     public static void main(String[] args) {
       // 定义一个时间字符串，日期是2019年1月1日
       String date = "2019/01/01";

       DateTimeFormatter df = DateTimeFormatter.ofPattern("yyyy/MM/dd");

       // 把字符串转化位 LocalDate 对象，并得到字符串匹配的日期
       LocalDate date2 = LocalDate.parse(date,df);
       // 打印出日期
       System.out.println(date2.toString());
     }
}
```

- 时间日期的计算```
   import java.time.LocalDate;

   public class DateTest10 {

     public static void main(String[] args) {

       LocalDate now = LocalDate.now();
       System.out.println("当前：" + now.toString());

       System.out.println("加法运算");
       System.out.println("加1天：" + now.plusDays(1));
       System.out.println("加1周：" + now.plusWeeks(1));
       System.out.println("加1月：" + now.plusMonths(1));
       System.out.println("加1年：" + now.plusYears(1));

       System.out.println("减法运算");
       System.out.println("减1天：" + now.minusDays(1));
       System.out.println("减1周：" + now.minusWeeks(1));
       System.out.println("减1月：" + now.minusMonths(1));
       System.out.println("减1年：" + now.minusYears(1));

     }

 }
```

- 两个日期时间的判断
   - isBefore(LocalDate) / isAfter(LocalDate) 返回值为boolean

---

<a name="971si"></a>
## ArrayList语法


- ArrayList<Java 对象类型> strs = new ArrayList<>();<br />这里的 Java 对象类型可以是任意的对象类型，<br />比如 String、Integer、House 等，<br />这里的 <> 是 Java 泛型的规范,记住这个语法就行了
- add()
- get/size 方法```java
   import java.util.ArrayList;

   public class ArrayListTest1{

     public static void main(String[] args){

       // 创建一个 ArrayList 存储字符串集合
       ArrayList<String> strs = new ArrayList<>();

       // 添加数据到 ArrayList 实例里
       strs.add("张三");
       strs.add("李四");

       // 获取集合的长度
       int size = strs.size();

       // 使用 for 循环迭代每一条记录
       for(int i=0;i<size;i++){
          // 根据索引获取值，值的类型是 String
          String str = strs.get(i);
          System.out.println(str);
       }

     }

    }
```

- for( 集合变量的类型 变量名称 : 集合变量 )```
  ArrayList<String> strs = new ArrayList<>();
  
  for(String str : strs){
    System.out.println(str);
  }
  //区别在于 遍历集合的时候是否能得到i值
   for(int i=0;i<size;i++){
      // 根据索引获取值，值的类型是 String
      String str = strs.get(i);
      System.out.println(str);
  }
```

<a name="rWJ3i"></a>
## UML(Unified Modeling Language 统一建模语言)

   - 正方形 -- private
   - 圆形 -- public
   - 菱形 -- protected
<a name="KZnuM"></a>
## 对象的特性

   - 万物皆对象
   - 每个对象都是唯一的
   - 对象具备属性和方法
<a name="YA43r"></a>
## 访问控制修饰符



| 修饰符 | 同类 | 同包 | 不同的包 |
| --- | --- | --- | --- |
| public | 有权限 | 有权限 | 有权限 |
| protected | 有权限 | 有权限 | 无权限 |
| default | 有权限 | 有权限 | 无权限 |
| private | 有权限 | 无权限 | 无权限 |



<a name="6eFKK"></a>
## 常量 (静态常量)

   - 常量和实例变量的区别在于不需要通过实例化才能得到变量，而可以直接获取或者操作变量。它的语法也非常简单，借助static 关键字就可以。
   - 一般使用常量的场景
      1. 常用的字符串值
      2. 需要在内存做缓存的值
   - 注意: 为了和变量区分开，所以一般情况下，常量的变量名采用全大写字母来定义，单词之间用_分割
<a name="FtLVv"></a>
## 继承

   - 当父类只有一个有参数的构造函数的时候，子类也必须要具备这个构造函数，或者调用super方法来实现新的构造函数 (super必须在第一行)```
   //如果需要定义新的构造函数
   public class JavaFile extends CustomFile{

   private String packageName;

   // 声明一个构造函数
   public JavaFile(String filePath,String packageName){
     super(filePath);//调用父类
     this.packageName = packageName;
   }

   public String getPackageName(){
       return this.packageName;
   }

 }
```

<a name="sCODA"></a>
## 接口

   - 定义接口名称遵循XxxService  以Service结尾的类名称代表接口
- **接口实现类**
   - 接口定义的方法在实现类里必须要全部实现，并且方法签名要一模一样(同样的方法名称、参数、返回值)
   - 修饰符必须是public
   - 实现类可以实现多个接口
   - 实现类包名在service命名为impl
   - 命名规则为XxxServiceImpl，后缀为ServiceImpl的是实现类```
public class RoleServiceImpl implements RoleService,EchoService{
}
```

- **接口实例化**
   - 接口实例化是通过实现类进行```
RoleService roleService = new RoleServiceImpl();
```

- **Java常用接口**
   - Map
   - List ( ArrayList的接口 )
<a name="TOrO3"></a>
### Map


<a name="XF22j"></a>
### ```java
   import java.util.Map;
   import java.util.HashMap;

   // key value 得是 Java 类型
   Map<key,value> map = new HashMap<>();   

   map.put(key,value) //数据存储 
   map.get(key)  //数据获取
   int size = map.size(); //集合大小

   void clear( )
   从此映射中移除所有映射关系（可选操作）。

   boolean containsKey(Object k)
   如果此映射包含指定键的映射关系，则返回 true。

   boolean containsValue(Object v)
   如果此映射将一个或多个键映射到指定值，则返回 true。

   Set entrySet( )
   返回此映射中包含的映射关系的 Set 视图。

   boolean equals(Object obj)
   比较指定的对象与此映射是否相等。

   Object get(Object k)
   返回指定键所映射的值；如果此映射不包含该键的映射关系，则返回 null。

   boolean isEmpty( )
   如果此映射未包含键-值映射关系，则返回 true。

   Set keySet( )
   返回此映射中包含的键的 Set 视图。

   Object put(Object k, Object v)
   将指定的值与此映射中的指定键关联（可选操作）。

   void putAll(Map m)
   从指定映射中将所有映射关系复制到此映射中（可选操作）。

   Object remove(Object k)
   如果存在一个键的映射关系，则将其从此映射中移除（可选操作）。

   Collection values( )
   返回此映射中包含的值的 Collection 视图。
```



<a name="CVfSm"></a>
### 接口的默认方法

<br />在接口的方法中使用了default 关键字，这个时候实现类如果没有自己的实现逻辑，就可以不用覆盖默认方法。
```java
public interface Vehicle {
   default void print(){
      System.out.println("我是一辆车!");
   }
}
```
<a name="P8cSi"></a>
## 异常

   - IOException<br />操作输入流和输出流时可能出现的异常,这个以后我们会经常遇到
   - ArithmeticException<br />数学异常。如果把整数除以o，就会出现这种异常
   - NullPointerException<br />空指针异常。当引用变量为null时，试图访问对象的属性或方法，就会出现这种异常
   - ArraylndexOutOfBoundsException<br />下标越界异常,一般出现在数组
   - ClassCastException<br />当类型转化失败的时候就会出现该异常
   - IllegalArgumentException,<br />非常参数异常，可以用来检查方法的参数是否合法


<br />这些异常都是继承于Exception，所以你也可以直接用一个Exception捕获所有的异常s<br />

- **异常的捕获**
```java
      public class ExceptionTest8 {

          public static void main(String[] args) {
              int num = 0;
              try {
                  num = getInt(null);
              } catch (Exception e) {
                  System.out.println(e.getMessage());
                  //e.getMessage()获取异常的字符串消息，这个指我们在new
                  Exception("姓名不能为空")时候出传入的。

              }
              System.out.println(num);
          }
      
          public static int getInt(String str) throws Exception {
              if (str == null) {
                  throw new Exception("姓名不能为空");
              }
              return Integer.parseInt(str);
          }
      }
```

- **自定义异常**
```
    public class ParamNullException extends Exception {
    // 若不创建空参构造函数，直接创建单参函数，也会报错
    public ParamNullException() {
  
    }
    // 若不创建构造函数，执行newParamNullException会报错
    public ParamNullException(String msg) {
      super(msg);
    }
  }
```

- **异常的作用域**
   - 作用域的提升，简单的来说就是把代码块的变量在代码块之前先定义



- **finally**
```java
      public void work() throws LeaveEarlyException {
          try {
            开门
            工作 8个小时 // 可能会抛出异常 DiseaseException
            关门
      
          } catch (DiseaseException e){
            throw new LeaveEarlyException();
          } finally{  //执行finally内语句
            关门
          }
      }
```

<br />

<a name="FSekl"></a>
## 内部类

<br />创建在一个class内，InnerTool称为内部类；Outer称为外部类。<br />

```java
public class OuterUtil {

    public class InnerTool { // 内部类
        public int add(int a,int b){
            return a+b;
        }
    }

    private InnerTool tool = new InnerTool(); 	// 实例化只能在Outer内部完成

}
```


<a name="SkHWK"></a>
### 访问实例内部类

<br />当 InnerTool 类的访问控制修饰符是 public ，可以被外部访问，先实例化外部类 OuterUtil，在实例化 InnerTool<br />**( 实例内部类不能有静态变量 )**
```java
OuterUtil.InnerTool tool = new OuterUtil().new InnerTool();
```

<br />

<a name="1l7y7"></a>
### 静态内部类

<br />添加 static 关键字声明为静态内部类后，可以直接调用这个内部类，无需先实例化外部类。<br />

```java
package com.youkeda.test;

import com.youkeda.util.OuterUtil;

// 静态内部类是需要单独 import 的
import com.youkeda.util.OuterUtil.InnerTool;

public class OuterUtilTest {
    
   public static void main(String[] args){
       
       InnerTool tool = new InnerTool();
       int sum = tool.add(1,2);
       System.out.println(sum);
   }
}
```


<a name="cHnVW"></a>
### 局部内部类
在方法内部定义一个类
```java
public class Tester {
    public void test(){
        class B{
            int a;
        }
        B b = new B();
    }
}
```

<br />

<a name="6jkwk"></a>
### 匿名类

<br />本质上它就是一个局部内部类，不同的是匿名类只用于类的实例化，而不是声明。（类似于简写的实现类）

```java
//实现接口或者继承父类
public class ATest {

  public static void main(String[] args){
    A a = new A(){
       public void method(){
         System.out.println("执行内部类");
       }
    };
    a.method();
  }

}
```


<a name="Tc8ri"></a>
## 集合


<a name="wVfSN"></a>
### List和数组的互换

<br />`static List asList(T... a)`   ( T是泛型类型、`...`是可变参数的一种声明 )<br />
<br />类似`static <T> List<T> asList(T[] a)`<br />asList 方法是把任意的相同对象实例转变成 List<br />
<br />**注意：Arrays.asList()参数必须是对象数组（例如 **`**Integer[] **`**），对于基本类型（例如  `int[]`）不能用**<br />

```java
import java.util.Arrays;
import java.util.List;
public class ArraysMain {
  public static void main(String[] args) {
    // 数字数组
    Integer[] intArr = { 10, 20, 15, 22, 35 };
    // 转化数组为 list
    List<Integer> lists = Arrays.asList(intArr);
    System.out.println("集合的长度是: " + lists.size());
  }
}
```


<a name="SbFyC"></a>
#### List 转为数组
   `toArray()`
```java
import java.util.List;
import java.util.ArrayList;
public class List2ArrayTest {
    public static void main(String[] args)
    {
        List<Integer> al = new ArrayList<Integer>();
        al.add(10);
        al.add(20);
        al.add(30);
        al.add(40);
        // 转化为数组
       Integer[] arr = al.toArray(new Integer[]{});
        for (Integer x : arr) {
          System.out.println(x + " ");
        }
    }
}
```


<a name="8fBD3"></a>
#### List转字符串
`String.join("split",list)`<br />

```java
import java.util.*;
public class Array2StringTest {
    public static void main(String args[]) {
        // 创建字符串集合
        List<String> list = Arrays.asList("Geeks", "ForGeeks", "GeeksForGeeks");
        // 转化集合为字符串， 使用 `,` 分割
        String string = String.join(",", list);
        // 打印结果
        System.out.println("字符串是: " + string);
    }
}
     //结果："字符串是: Geeks,ForGeeks,GeeksForGeeks"

```


<a name="budDf"></a>
### 排序

<br />`Array.sort()`  将数组从小到大(升序)的顺序排序<br />
<br />`Array.toString()`  将数组转化为字符串<br />
<br />**自定义排序**<br />`static <T> void sort(T[] a, Comparator< super T> c):`<br />
<br />`java.util.Comparator` 是一个接口，用于声明比较规则，一般配合排序使用
```java
public interface Comparator<T> {
  //返回值是 int，我们根据返回值 >0、=0、<0 进行重新排序
  int compare(T o1, T o2);
}
```
**
```java
import java.util.*;
public class ArraysSortTest3 {
      public static void main(String[] args) {       
            Integer[] intArr = { 10, 20, 15, 22, 35 };

            // 自定义排序
            Arrays.sort(intArr, new Comparator<Integer>(){
                public int compare(Integer o1, Integer o2){

                    return o1-o2; // 判断 o1<o2，执行升序排序
                    
                    // return o2-o1;  判断 o2>o1，执行降序排序
                }
            });

            System.out.println("Integer Array: "
                               + Arrays.toString(intArr));
        }
    
}
```


<a name="AJEVX"></a>
### 集合的排序

<br />借助`java.util.Collections`的sort方法<br />
<br />`static <T> void sort(List<T> list, Comparator<? super T> c)`<br />

```java
import java.util.*;
public class ListSortTest {
  public static void main (String[] args) {
    List<Student> ar = new ArrayList<Student>();
    ar.add(new Student(111, "bbbb", "london"));
    ar.add(new Student(131, "aaaa", "nyc"));
    ar.add(new Student(121, "cccc", "jaipur"));
    System.out.println("原始集合");
    for (int i=0; i<ar.size(); i++) {
      System.out.println(ar.get(i));
    }
    // 实现升序排序 核心代码
    Collections.sort(ar, new Comparator<Student>(){
      public int compare(Student a, Student b) {
        // 第一个参数的学号 > 第二个参数的学号
        return a.getRollNo() - b.getRollNo();// 升序
          
        //return b.getRollNo() - a.getRollNo(); 降序
      }
    });
    System.out.println("\n排序后的集合");
    for (int i=0; i<ar.size(); i++) {
      System.out.println(ar.get(i));
    }
  }
}
```

<br />
<br />

<a name="rvjsW"></a>
### 集合操作


<a name="2B1ln"></a>
#### 删除remove

<br />`List.remove(int index)`<br />
<br />` // 删除第4条记录         list.remove(3);`
<a name="5II2n"></a>
#### 合并addAll
`List1.addAll(List list2)`<br />
<br />`// 合并 list2 到 list1 集合中         list1.addAll(list2);`<br />

<a name="Zu9jh"></a>
#### 截取subList

<br />`subList(int begin,int end)`(左闭右开)<br />
<br />`//截取list[2]至list[3]`<br />` List<String> arrlist2 = list.subList(2, 4);`<br />
<br />
<br />

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
   - 名称（键）必须是字符串<br />
   - 键、值之间用冒号 “`:`” 分隔。<br />
- 多条数据之间，用逗号 “`,`” 分隔<br />
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
```java
package com.youkeda.test.http;

import java.io.IOException;
import okhttp3.Call;
import okhttp3.OkHttpClient;
import okhttp3.Request;

public class ApiAsker {

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
    ApiAsker apiAsker = new ApiAsker();
    String url = "https://api.apiopen.top/getJoke?page=1&count=2&type=video";
    String content = apiAsker.getContent(url);
  
    System.out.println("API调用结果");
    System.out.println(content);
  }
}

```
<a name="xAOLc"></a>
### 
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


<a name="ompOC"></a>
### POST JSON数据

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
String city = (String)dataObj.get("city");
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
<br />`Host`的值一定是一个域名且不带协议头

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
   -     `创建对象`  --》 `写入内容`  --》 `关闭写入操作`
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



<a name="KSyAN"></a>
### 
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

