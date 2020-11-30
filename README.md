## Git命令
- 查看是否生成SSH~~:
     
        cat ~/.ssh/id_rsa.pub 
    
- 生成SSH:
    
        ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    
- 告诉git你的名字邮箱
    
        git config --global user.name "your_name"
         git config --global user.email "your_email@example.com"
    
- 克隆仓库

        git clone 仓库地址（SSH地址）
    
- git提交三部曲

       1. git add (git add -A)
       2. git commit (git commit -m "本次提交的修改的备注")
       3. git push
          1. 第1次提交到本分支  （git push origin main）
          2. 第2-n次提交到本分支 （git push）
          3. 提交到其他分支  （git push origin b）

- 代码冲突

        git pull（抓取远程仓库的内容，协同开发时，每一次提交之前，git pull）
    
## Java

- java编译过程并不生成机器语言，而是生成字节码

     - 源代码--编译器--字节码--解释器（JVM）--exe
  
- 块注释语法

      /**
    
       *我是块注释
       
       */

#### 字符串常用方法 

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

     -  字符串替换，执行后会得到一个新的字符串，原始字符串不会改变(若新值为空格，则可实现删除功能)

- **split("分割字符串")**

    - 字符串分割，"分割字符串"可以是字符串也可以是特殊符号( . | * 这三个字符如果作为分割符，需要加上\ \ 例如str.split("\ \ |") )

     
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

- **toUpperCase()/toLowerCase()**

   - 大小写转化


- **equals("被比较的字符串")**

    - 字符串比较

-  **将字符串变成数字**

    -  Integer.parseInt("字符串")

- **数字转化为字符串**
  1. 使用空字符串加数字(String str = "" + a)
  2. 使用valueOf强制转化(String str = String.valueOf(a))



---
#### 日期


- 日期类 (import java.time.LocalDate)
 
 
- 日期格式类(import java.time.format.DateTimeFormatter)


- 年-月-日 时:分:秒 == yyyy-MM-dd HH:mm:ss


- 日期时间和字符串的转化


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


- 获取日期时间具体的值

    
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


- 字符串转化为日期时间(LocalDate.parse(date))
   
   
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

- 若字符串日期格式不是yyyy-MM-dd，就得借助DateTimeFormatter
  (LocalDate.parse(date,df))


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


- 时间日期的计算


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
    


- 两个日期时间的判断
  
  -  isBefore(LocalDate) / isAfter(LocalDate) 返回值为boolean


---


#### ArrayList语法


- ArrayList<Java 对象类型> strs = new ArrayList<>();


    这里的 Java 对象类型可以是任意的对象类型，
    比如 String、Integer、House 等，
    这里的 <> 是 Java 泛型的规范,记住这个语法就行了


- add()


- get/size 方法


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


- for( 集合变量的类型 变量名称 : 集合变量 )

    

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
