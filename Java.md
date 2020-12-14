# Java

<a name="2sYGq"></a>
# Java


- java编译过程并不生成机器语言，而是生成字节码
   - 源代码--编译器--字节码--解释器（JVM）--exe
- 块注释语法
```java
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
   - 字符串分割，"分割字符串"可以是字符串也可以是特殊符号( . | * 这三个字符如果作为分割符，需要加上\ \ 例如str.split("\ \ |") )
```java
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
   1. 使用valueOf强制转化(String str = String.valueOf(a))

---

<a name="t508d"></a>
## 日期


- 日期类 (import java.time.LocalDate)
- 日期格式类(import java.time.format.DateTimeFormatter)
- 年-月-日 时:分:秒 == yyyy-MM-dd HH:mm:ss
- 日期时间和字符串的转化
```java
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

- 获取日期时间具体的值
```
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

- 字符串转化为日期时间(LocalDate.parse(date))
```
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

- 若字符串日期格式不是yyyy-MM-dd，就得借助DateTimeFormatter<br />(LocalDate.parse(date,df))
```
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

- 时间日期的计算
```
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
- get/size 方法
```java
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

- for( 集合变量的类型 变量名称 : 集合变量 )
```
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
      1. 需要在内存做缓存的值
   - 注意: 为了和变量区分开，所以一般情况下，常量的变量名采用全大写字母来定义，单词之间用_分割
<a name="FtLVv"></a>
## 继承

   - 当父类只有一个有参数的构造函数的时候，子类也必须要具备这个构造函数，或者调用super方法来实现新的构造函数 (super必须在第一行)
```
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
   - 命名规则为XxxServiceImpl，后缀为ServiceImpl的是实现类
```
public class RoleServiceImpl implements RoleService,EchoService{
}
```

- **接口实例化**
   - 接口实例化是通过实现类进行
```
RoleService roleService = new RoleServiceImpl();
```

- **Java常用接口**
   - Map
   - List ( ArrayList的接口 )
<a name="TOrO3"></a>
### Map


```java
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
<br />
<a name="qepgm"></a>
## 对象的关系


<a name="ehmQ1"></a>
### 关联关系（Association）
![image.png](https://cdn.nlark.com/yuque/0/2020/png/2999046/1607331900314-9f66da3c-f33a-458b-9298-e258357bff42.png#align=left&display=inline&height=568&margin=%5Bobject%20Object%5D&name=image.png&originHeight=568&originWidth=423&size=30034&status=done&style=none&width=423)
<a name="l9Gnv"></a>
### 聚合关系（Agggation）

- 一种特殊的关联形式，表示两个对象之间的所属 ( has-a ) 关系。
- 所有者称为**聚合对象**，它的类称为**聚合类**；从属对象称为**被聚合对象**，它的类称为**被聚合类**

例：公司类`Company`和员工类`Employee`是聚合关系，各自拥有各自的生命周期，即使公司倒闭也不影响员工的存在<br />**![image.png](https://cdn.nlark.com/yuque/0/2020/png/2999046/1607331527525-3c810721-4509-4cb6-ab2c-d498e2eef710.png#align=left&display=inline&height=274&margin=%5Bobject%20Object%5D&name=image.png&originHeight=274&originWidth=303&size=12382&status=done&style=none&width=303)**
```java
public class Company {
    private List<Employee> employees;
}

public class Employee {
    private String name;
}
```
<a name="F8yn2"></a>
### 组合关系（Composition）

- 在组合关系中包含对象负责被包含对象的创建以及生命周期，即当包含对象被销毁时被包含对象也会不复存在。

![image.png](https://cdn.nlark.com/yuque/0/2020/png/2999046/1607331656425-7fb54947-f62c-46a4-a3e5-80d23b860758.png#align=left&display=inline&height=282&margin=%5Bobject%20Object%5D&name=image.png&originHeight=282&originWidth=340&size=12613&status=done&style=none&width=340)
```java
public class Car {
    // 实例化一个不可变的属性 engine
    private final Engine engine = new Engine();
}

public class Engine {
    private String type;
}
```
<a name="JpDUj"></a>
### 依赖关系（Dependency）

- 依赖(Dependency)描述的是一个类的引用用作另一个类的方法的参数。

![image.png](https://cdn.nlark.com/yuque/0/2020/png/2999046/1607331752133-ff9eef4d-0621-443f-b925-6d7157ece05b.png#align=left&display=inline&height=263&margin=%5Bobject%20Object%5D&name=image.png&originHeight=263&originWidth=483&size=14521&status=done&style=none&width=483)
<a name="4K2VQ"></a>
### 继承（Inheritance）/实现（Realization）关系

- 继承和实现的UML图是一样的表达了子类继承父类，实现类实现接口的关系，

![image.png](https://cdn.nlark.com/yuque/0/2020/png/2999046/1607331808013-230f0f81-db58-4aa7-84db-4c1a1fdd601b.png#align=left&display=inline&height=298&margin=%5Bobject%20Object%5D&name=image.png&originHeight=298&originWidth=307&size=12946&status=done&style=none&width=307)
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
# 

<br />

<a name="YrwuL"></a>
# 时间复杂度

<br />**O(1) < O(log n) < O(n) < O(nlogn) < O(n) < O(n) < O(2) < O(n!) < O(n)**<br />
<br />
<br />
<br />
<br />冒泡排序相比较而言肯定是较差的。<br />选择排序和插入排序得分情况而定，如果原始数组本身有很多元素按希望的顺序排好序，则选择插入排序(如上面最好极限情况，接近O(N))，否则选择选择排序。<br />
<br />
<br />

<a name="Ps1o3"></a>
# 递归

-  基准条件（递归结束条件）
-  递归公式



-  所以在之后碰到问题以后，我们可以按照如下流程进行思考:
   - 找出基准条件。
   - 思考在基准条件下，会出现什么情况。
   - 思考基准条件前一步的情况，或者函数执行情况。
   - 配合递归公式，继续往前推进。
   - 最后实现完善的代码。



