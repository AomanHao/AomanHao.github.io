---
title: Java面试之九阴真经
date: 2018-07-15 11:55:00
tags: [笔面试, Java]
---


Java面试相关

<!--more-->

谈谈final, finally, finalize的区别： 
final：：：修饰符（关键字）如果一个类被声明为final，意味着它不能再派生出新的子类，不能作为父类被继承。因此一个类不能既被声明为 abstract的，又被声明为final的。将变量或方法声明为final，可以保证它们在使用中不被改变。被声明为final的变量必须在声明时给定初值，而在以后的引用中只能读取，不可修改。被声明为final的方法也同样只能使用，不能重载 
finally：：：再异常处理时提供 finally 块来执行任何清除操作。如果抛出一个异常，那么相匹配的 catch 子句就会执行，然后控制就会进入 finally 块（如果有的话）。 
finalize：：：方法名。Java 技术允许使用 finalize() 方法在垃圾收集器将对象从内存中清除出去之前做必要的清理工作。这个方法是由垃圾收集器在确定这个对象没有被引用时对这个对象调用的。它是在 Object 类中定义的，因此所有的类都继承了它。子类覆盖 finalize() 方法以整理系统资源或者执行其他清理工作。finalize() 方法是在垃圾收集器删除对象之前对这个对象调用的。

Anonymous Inner Class (匿名内部类) 是否可以extends(继承)其它类，是否可以implements(实现)interface(接口)：
匿名的内部类是没有名字的内部类。不能extends(继承) 其它类，但一个内部类可以作为一个接口，由另一个内部类实现。

&和&&的区别： 
&是位运算符。&&是布尔逻辑运算符。

HashMap和Hashtable的区别： 
都属于Map接口的类，实现了将惟一键映射到特定的值上。 
HashMap 类没有分类或者排序。它允许一个 null 键和多个 null 值。 
Hashtable 类似于 HashMap，但是不允许 null 键和 null 值。它也比 HashMap 慢，因为它是同步的。

Collection 和 Collections的区别：
Collections是个java.util下的类，它包含有各种有关集合操作的静态方法。 
Collection是个java.util下的接口，它是各种集合结构的父接口。

GC是什么? 为什么要有GC? (基础)： 
GC是垃圾收集器。Java 程序员不用担心内存管理，因为垃圾收集器会自动进行管理。要请求垃圾收集，可以调用下面的方法之一： 
System.gc() 
Runtime.getRuntime().gc()。

String s = new String("xyz");创建了几个String Object： 
两个对象，一个是“xyx”,一个是指向“xyx”的引用对象s。

Math.round(11.5)等於多少? Math.round(-11.5)等於多少： 
Math.round(11.5)返回（long）12，Math.round(-11.5)返回（long）-11。

short s1 = 1; s1 = s1 + 1;有什么错? short s1 = 1; s1 += 1;有什么错： 
short s1 = 1; s1 = s1 + 1;有错，s1是short型，s1+1是int型,不能显式转化为short型。可修改为s1 =(short)(s1 + 1) 。short s1 = 1; s1 += 1正确。

sleep() 和 wait() 有什么区别： 
sleep()方法是使线程停止一段时间的方法。在sleep 时间间隔期满后，线程不一定立即恢复执行。这是因为在那个时刻，其它线程可能正在运行而且没有被调度为放弃执行，除非(a)“醒来”的线程具有更高的优先级 
(b)正在运行的线程因为其它原因而阻塞。 
wait()是线程交互时，如果线程对一个同步对象x 发出一个wait()调用，该线程会暂停执行，被调对象进入等待状态，直到被唤醒或等待时间到。

数组有没有length()这个方法? String有没有length()这个方法： 
数组没有length()这个方法，有length的属性。 
String有有length()这个方法。

Overload和Override的区别。Overloaded的方法是否可以改变返回值的类型： 
方法的重写Overriding和重载Overloading是Java多态性的不同表现。重写Overriding是父类与子类之间多态性的一种表现，重载Overloading是一个类中多态性的一种表现。如果在子类中定义某方法与其父类有相同的名称和参数，我们说该方法被重写 (Overriding)。子类的对象使用这个方法时，将调用子类中的定义，对它而言，父类中的定义如同被“屏蔽”了。如果在一个类中定义了多个同名的方法，它们或有不同的参数个数或有不同的参数类型，则称为方法的重载(Overloading)。Overloaded的方法是可以改变返回值的类型。

Set里的元素是不能重复的，那么用什么方法来区分重复与否呢? 是用==还是equals()? 它们有何区别：
Set里的元素是不能重复的，那么用iterator()方法来区分重复与否。equals()是判读两个Set是否相等。 
equals()和==方法决定引用值是否指向同一对象equals()在类中被覆盖，为的是当两个分离的对象的内容和类型相配的话，返回真值。

给我一个你最常见到的runtime exception： 
 
ArithmeticException, ArrayStoreException, BufferOverflowException, BufferUnderflowException, CannotRedoException, CannotUndoException, ClassCastException, CMMException, ConcurrentModificationException, DOMException, EmptyStackException, IllegalArgumentException, IllegalMonitorStateException, IllegalPathStateException, IllegalStateException, ImagingOpException, IndexOutOfBoundsException, MissingResourceException, NegativeArraySizeException, NoSuchElementException, NullPointerException, ProfileDataException, ProviderException, RasterFormatException, SecurityException, SystemException, UndeclaredThrowableException, UnmodifiableSetException, UnsupportedOperationException。
 
error和exception有什么区别： 
error 表示恢复不是不可能但很困难的情况下的一种严重问题。比如说内存溢出。不可能指望程序能处理这样的情况。 
exception 表示一种设计或实现问题。也就是说，它表示如果程序运行正常，从不会发生的情况。

List, Set, Map是否继承自Collection接口： 
List，Set是。
Map不是。

abstract class和interface有什么区别： 
　　声明方法的存在而不去实现它的类被叫做抽象类（abstract class），它用于要创建一个体现某些基本行为的类，并为该类声明方法，但不能在该类中实现该类的情况。不能创建abstract 类的实例。然而可以创建一个变量，其类型是一个抽象类，并让它指向具体子类的一个实例。不能有抽象构造函数或抽象静态方法。Abstract 类的子类为它们父类中的所有抽象方法提供实现，否则它们也是抽象类为。取而代之，在子类中实现该方法。知道其行为的其它类可以在类中实现这些方法。
　　接口（interface）是抽象类的变体。在接口中，所有方法都是抽象的。多继承性可通过实现这样的接口而获得。接口中的所有方法都是抽象的，没有一个有程序体。接口只可以定义static final成员变量。接口的实现与子类相似，除了该实现类不能从接口定义中继承行为。当类实现特殊接口时，它定义（即将程序体给予）所有这种接口的方法。然后，它可以在实现了该接口的类的任何对象上调用接口的方法。由于有抽象类，它允许使用接口名作为引用变量的类型。通常的动态联编将生效。引用可以转换到接口类型或从接口类型转换，instanceof 运算符可以用来决定某对象的类是否实现了接口。

接口是否可继承接口? 抽象类是否可实现(implements)接口? 抽象类是否可继承实体类(concrete class)： 
　　接口可以继承接口。抽象类可以实现(implements)接口，抽象类是否可继承实体类，但前提是实体类必须有明确的构造函数。

启动一个线程是用run()还是start()： 
　　启动一个线程是调用start()方法，使线程所代表的虚拟处理机处于可运行状态，这意味着它可以由JVM调度并执行。这并不意味着线程就会立即运行。run()方法可以产生必须退出的标志来停止一个线程。

构造器Constructor是否可被override： 
　　构造器Constructor不能被继承，因此不能重写Overriding，但可以被重载Overloading。

try {}里有一个return语句，那么紧跟在这个try后的finally {}里的code会不会被执行，什么时候被执行，在return前还是后： 
　　会执行，在return前执行。

两个对象值相同(x.equals(y) == true)，但却可有不同的hash code，这句话对不对： 
　　不对，有相同的hash code。

当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递： 
　　是值传递。Java 编程语言只由值传递参数。当一个对象实例作为一个参数被传递到方法中时，参数的值就是对该对象的引用。对象的内容可以在被调用的方法中改变，但对象的引用是永远不会改变的。

swtich是否能作用在byte上，是否能作用在long上，是否能作用在String上：
　　switch（expr1）中，expr1是一个整数表达式。因此传递给 switch 和 case 语句的参数应该是 int、 short、 char 或者 byte。long,string 都不能作用于swtich。

编程题: 写一个Singleton出来：
　　Singleton模式主要作用是保证在Java应用程序中，一个类Class只有一个实例存在。
　　一般Singleton模式通常有几种种形式：
　　第一种形式：定义一个类，它的构造函数为private的，它有一个static的private的该类变量，在类初始化时实例话，通过一个public的getInstance方法获取对它的引用,继而调用其中的方法。
 
public class Singleton { 
　　private Singleton(){} 
　　//在自己内部定义自己一个实例，是不是很奇怪？ 
　　//注意这是private 只供内部调用 
　　private static Singleton instance = new Singleton(); 
　　//这里提供了一个供外部访问本class的静态方法，可以直接访问　　 
　　public static Singleton getInstance() { 
　　　　return instance; 　　 
　　 } 
} 
  
　　第二种形式：
 
public class Singleton { 
　　private static Singleton instance = null; 
　　public static synchronized Singleton getInstance() { 
　　//这个方法比上面有所改进，不用每次都进行生成对象，只是第一次　　　 　 
　　//使用时生成实例，提高了效率！ 
　　if (instance==null) 
　　　　instance＝new Singleton(); 
return instance; 　　} 
} 
 
其他形式：
　　定义一个类，它的构造函数为private的，所有方法为static的。
　　一般认为第一种形式要更加安全些。

Hashtable和HashMap的区别： 
　　Hashtable继承自Dictionary类，而HashMap是Java1.2引进的Map interface的一个实现 
　　HashMap允许将null作为一个entry的key或者value，而Hashtable不允许 
　　还有就是，HashMap把Hashtable的contains方法去掉了，改成containsvalue和containsKey。因为contains方法容易让人引起误解。 
　　最大的不同是，Hashtable的方法是Synchronize的，而HashMap不是，在 
多个线程访问Hashtable时，不需要自己为它的方法实现同步，而HashMap 
就必须为之提供外同步。 
Hashtable和HashMap采用的hash/rehash算法都大概一样，所以性能不会有很大的差异

作用域public,private,protected,以及不写时的区别： 
作用域 当前类 同一package 子孙类 其他package 
public √ √ √ √ 
protected √ √ √ × 
friendly √ √ × × 
private √ × × × 
不写时默认为friendly。

ArrayList和Vector的区别,HashMap和Hashtable的区别： 
答：就ArrayList与Vector主要从二方面来说. 
一.同步性:Vector是线程安全的，也就是说是同步的，而ArrayList是线程序不安全的，不是同步的 
二.数据增长:当需要增长时,Vector默认增长为原来一培，而ArrayList却是原来的一半 
就HashMap与HashTable主要从三方面来说。 
一.历史原因:Hashtable是基于陈旧的Dictionary类的，HashMap是Java 1.2引进的Map接口的一个实现 
二.同步性:Hashtable是线程安全的，也就是说是同步的，而HashMap是线程序不安全的，不是同步的 
三.值：只有HashMap可以让你将空值作为一个表的条目的key或value。

char型变量中能不能存贮一个中文汉字?为什么： 
答：是能够定义成为一个中文的，因为java中以unicode编码，一个char占16个字节，所以放一个中文是没问题的。

介绍JAVA中的Collection FrameWork(包括如何写自己的数据结构)： 
答：Collection FrameWork如下： 
 
Collection 
├List 
│├LinkedList 
│├ArrayList 
│└Vector 
│　└Stack 
└Set 
Map 
├Hashtable 
├HashMap 
└WeakHashMap 
 
Collection是最基本的集合接口，一个Collection代表一组Object，即Collection的元素（Elements） 
Map提供key到value的映射。

jsp有哪些内置对象?作用分别是什么： 
答:JSP共有以下9种基本内置组件（可与ASP的6种内部组件相对应）： 
　request 用户端请求，此请求会包含来自GET/POST请求的参数 
response 网页传回用户端的回应 
pageContext 网页的属性是在这里管理 
session 与请求有关的会话期 
application servlet 正在执行的内容 
out 用来传送回应的输出 
config servlet的构架部件 
page JSP网页本身 
exception 针对错误网页，未捕捉的例外。

jsp有哪些动作?作用分别是什么：
答:JSP共有以下6种基本动作 
jsp:include：在页面被请求的时候引入一个文件。 
jsp:useBean：寻找或者实例化一个JavaBean。 
jsp:setProperty：设置JavaBean的属性。 
jsp:getProperty：输出某个JavaBean的属性。 
jsp:forward：把请求转到一个新的页面。 
jsp:plugin：根据浏览器类型为Java插件生成OBJECT或EMBED标记。

JSP中动态INCLUDE与静态INCLUDE的区别： 
答：动态INCLUDE用jsp:include动作实现 
 
<jsp:include page="included.jsp" flush="true" />
 
它总是会检查所含文件中的变化，适合用于包含动态页面，并且可以带参数 
静态INCLUDE用include伪码实现,定不会检查所含文件的变化，适用于包含静态页面 
 
<%@ include file="included.htm" %>。
 
两种跳转方式分别是什么?有什么区别： 
答：有两种，分别为： 
 
<jsp:include page="included.jsp" flush="true"> 
<jsp:forward page= "nextpage.jsp"/> 
 
前者页面不会转向include所指的页面，只是显示该页的结果，主页面还是原来的页面。执行完后还会回来，相当于函数调用。并且可以带参数.后者完全转向新页面，不会再回来。相当于go to 语句。

### Servlet的生命周期： 
答:servlet有良好的生存期的定义，包括加载和实例化、初始化、处理请求以及服务结束。这个生存期由javax.servlet.Servlet接口的init,service和destroy方法表达。

### JAVA SERVLET API中forward() 与redirect()的区别： 
答:前者仅是容器中控制权的转向，在客户端浏览器地址栏中不会显示出转向后的地址；后者则是完全的跳转，浏览器将会得到跳转的地址，并重新发送请求链接。这样，从浏览器的地址栏中可以看到跳转后的链接地址。所以，前者更加高效，在前者可以满足需要时，尽量使用forward()方法，并且，这样也有助于隐藏实际的链接。在有些情况下，比如，需要跳转到一个其它服务器上的资源，则必须使用sendRedirect()方法。

### Servlet的基本架构： 
 ```
public class ServletName extends HttpServlet { 
public void doPost(HttpServletRequest request, HttpServletResponse response) throws 
ServletException, IOException { 
} 
public void doGet(HttpServletRequest request, HttpServletResponse response) throws 
ServletException, IOException { 
} 
}
 ```

### 可能会让你写一段Jdbc连Oracle的程序,并实现数据查询： 
答:程序如下： 
```
package hello.ant; 
import java.sql.*; 
public class jdbc 
{ 
String dbUrl="jdbc:oracle:thin:@127.0.0.1:1521:orcl"; 
String theUser="admin"; 
String thePw="manager"; 
Connection c=null; 
Statement conn; 
ResultSet rs=null; 
public jdbc() 
{ 
try{ 
Class.forName("oracle.jdbc.driver.OracleDriver").newInstance(); 
c = DriverManager.getConnection(dbUrl,theUser,thePw); 
conn=c.createStatement(); 
}catch(Exception e){ 
e.printStackTrace(); 
} 
} 
public boolean executeUpdate(String sql) 
{ 
try 
{ 
conn.executeUpdate(sql); 
return true; 
} 
catch (SQLException e) 
{ 
e.printStackTrace(); 
return false; 
} 
} 
public ResultSet executeQuery(String sql) 
{ 
rs=null; 
try 
{ 
rs=conn.executeQuery(sql); 
} 
catch (SQLException e) 
{ 
e.printStackTrace(); 
} 
return rs; 
} 
public void close() 
{ 
try 
{ 
conn.close(); 
c.close(); 
} 
catch (Exception e) 
{ 
e.printStackTrace(); 
} 
} 
public static void main(String[] args) 
{ 
ResultSet rs; 
jdbc conn = new jdbc(); 
rs=conn.executeQuery("select * from test"); 
try{ 
while (rs.next()) 
{ 
System.out.println(rs.getString("id")); 
System.out.println(rs.getString("name")); 
} 
}catch(Exception e) 
{ 
e.printStackTrace(); 
} 
} 
}
 ```
### Class.forName的作用?为什么要用： 
答：调用该访问返回一个以字符串指定类名的类的对象。

### Jdo是什么： 
答:JDO是Java对象持久化的新的规范，为java data object的简称,也是一个用于存取某种数据仓库中的对象的标准化API。JDO提供了透明的对象存储，因此对开发人员来说，存储数据对象完全不需要额外的代码（如JDBC API的使用）。这些繁琐的例行工作已经转移到JDO产品提供商身上，使开发人员解脱出来，从而集中时间和精力在业务逻辑上。另外，JDO很灵活，因为它可以在任何数据底层上运行。JDBC只是面向关系数据库（RDBMS）JDO更通用，提供到任何数据底层的存储功能，比如关系数据库、文件、XML以及对象数据库（ODBMS）等等，使得应用可移植性更强。

### xml有哪些解析技术?区别是什么： 
答:有DOM,SAX,STAX等 
DOM:处理大型文件时其性能下降的非常厉害。这个问题是由DOM的树结构所造成的，这种结构占用的内Java程序员面试之九阴真经 - wyf0931 - 河伯的地盘存较多，而且DOM必须在解析文件之前把整个文档装入内存,适合对XML的随机访问SAX:不现于DOM,SAX是事件驱动型的XML解析方式。它顺序读取XML文件，不需要一次全部装载整个文件。当遇到像文件开头，文档结束，或者标签开头与标签结束时，它会触发一个事件，用户通过在其回调事件中写入处理代码来处理XML文件，适合对XML的顺序访问 
STAX:Streaming API for XML (StAX)。

### 你在项目中用到了xml技术的哪些方面?如何实现的： 
答:用到了数据存贮，信息配置两方面。在做数据交换平台时，将不能数据源的数据组装成XML文件，然后将XML文件压缩打包加密后通过网络传送给接收者，接收解密与解压缩后再同XML文件中还原相关信息进行处理。在做软件配置时，利用XML可以很方便的进行，软件的各种配置参数都存贮在XML文件中。

### 用jdom解析xml文件时如何解决中文问题?如何解析： 
答:看如下代码,用编码方式加以解决 
 ```
package test; 
import java.io.*; 
public class DOMTest 
{ 
private String inFile = "c:\people.xml"; 
private String outFile = "c:\people.xml"; 
public static void main(String args[]) 
{ 
new DOMTest(); 
} 
public DOMTest() 
{ 
try 
{ 
javax.xml.parsers.DocumentBuilder builder = 
javax.xml.parsers.DocumentBuilderFactory.newInstance().newDocumentBuilder(); 
org.w3c.dom.Document doc = builder.newDocument(); 
org.w3c.dom.Element root = doc.createElement("老师"); 
org.w3c.dom.Element wang = doc.createElement("王"); 
org.w3c.dom.Element liu = doc.createElement("刘"); 
wang.appendChild(doc.createTextNode("我是王老师")); 
root.appendChild(wang); 
doc.appendChild(root); 
javax.xml.transform.Transformer transformer = 
javax.xml.transform.TransformerFactory.newInstance().newTransformer(); 
transformer.setOutputProperty(javax.xml.transform.OutputKeys.ENCODING, "gb2312"); 
transformer.setOutputProperty(javax.xml.transform.OutputKeys.INDENT, "yes"); 
 
 
transformer.transform(new javax.xml.transform.dom.DOMSource(doc), 
new 
 
javax.xml.transform.stream.StreamResult(outFile)); 
} 
catch (Exception e) 
{ 
System.out.println (e.getMessage()); 
} 
} 
}
```
### 编程用JAVA解析XML的方式： 
答:用SAX方式解析XML，XML文件如下： 
 ```
<?xml version="1.0" encoding="gb2312"?> 
<person> 
<name>王小明</name> 
<college>信息学院</college> 
<telephone>6258113</telephone> 
<notes>男,1955年生,博士，95年调入海南大学</notes> 
</person> 
 ```
### 事件回调类SAXHandler.java 
 ```
import java.io.*; 
import java.util.Hashtable; 
import org.xml.sax.*; 
public class SAXHandler extends HandlerBase 
{ 
private Hashtable table = new Hashtable(); 
private String currentElement = null; 
private String currentValue = null; 
public void setTable(Hashtable table) 
{ 
this.table = table; 
} 
public Hashtable getTable() 
{ 
return table; 
} 
public void startElement(String tag, AttributeList attrs) 
throws SAXException 
{ 
currentElement = tag; 
} 
public void characters(char[] ch, int start, int length) 
throws SAXException 
{ 
currentValue = new String(ch, start, length); 
} 
public void endElement(String name) throws SAXException 
{ 
if (currentElement.equals(name)) 
table.put(currentElement, currentValue); 
} 
} 
 ```
### JSP内容显示源码,SaxXml.jsp: 
 ```
<HTML> 
<HEAD> 
<TITLE>剖析XML文件people.xml</TITLE> 
</HEAD> 
<BODY> 
<%@ page errorPage="ErrPage.jsp" 
contentType="text/html;charset=GB2312" %> 
<%@ page import="java.io.*" %> 
<%@ page import="java.util.Hashtable" %> 
<%@ page import="org.w3c.dom.*" %> 
<%@ page import="org.xml.sax.*" %> 
<%@ page import="javax.xml.parsers.SAXParserFactory" %> 
<%@ page import="javax.xml.parsers.SAXParser" %> 
<%@ page import="SAXHandler" %> 
<% 
File file = new File("c:\people.xml"); 
FileReader reader = new FileReader(file); 
Parser parser; 
SAXParserFactory spf = SAXParserFactory.newInstance(); 
SAXParser sp = spf.newSAXParser(); 
SAXHandler handler = new SAXHandler(); 
sp.parse(new InputSource(reader), handler); 
Hashtable hashTable = handler.getTable(); 
out.println("<TABLE BORDER=2><CAPTION>教师信息表</CAPTION>"); 
out.println("<TR><TD>姓名</TD>" + "<TD>" + 
(String)hashTable.get(new String("name")) + "</TD></TR>"); 
out.println("<TR><TD>学院</TD>" + "<TD>" + 
(String)hashTable.get(new String("college"))+"</TD></TR>"); 
out.println("<TR><TD>电话</TD>" + "<TD>" + 
(String)hashTable.get(new String("telephone")) + "</TD></TR>"); 
out.println("<TR><TD>备注</TD>" + "<TD>" + 
(String)hashTable.get(new String("notes")) + "</TD></TR>"); 
out.println("</TABLE>"); 
%> 
</BODY> 
</HTML>
 ```
### EJB与JAVA BEAN的区别： 
答:Java Bean 是可复用的组件，对Java Bean并没有严格的规范，理论上讲，任何一个Java类都可以是一个Bean。但通常情况下，由于Java Bean是被容器所创建（如Tomcat）的，所以Java Bean应具有一个无参的构造器，另外，通常Java Bean还要实现Serializable接口用于实现Bean的持久性。Java Bean实际上相当于微软COM模型中的本地进程内COM组件，它是不能被跨进程访问的。Enterprise Java Bean 相当于DCOM，即分布式组件。它是基于Java的远程方法调用（RMI）技术的，所以EJB可以被远程访问（跨进程、跨计算机）。但EJB必须被布署在诸如Webspere、WebLogic这样的容器中，EJB客户从不直接访问真正的EJB组件，而是通过其容器访问。EJB容器是EJB组件的代理，EJB组件由容器所创建和管理。客户通过容器来访问真正的EJB组件。

### EJB的基本架构： 
答:一个EJB包括三个部分: 
Remote Interface 接口的代码 
 ```
package Beans; 
import javax.ejb.EJBObject; 
import java.rmi.RemoteException; 
public interface Add extends EJBObject 
{ 
//some method declare 
} 
 
 ```
### Home Interface 接口的代码 
```
package Beans; 
import java.rmi.RemoteException; 
import jaax.ejb.CreateException; 
import javax.ejb.EJBHome; 
public interface AddHome extends EJBHome 
{ 
//some method declare 
} 
 
 ```
### EJB类的代码 
```
package Beans; 
import java.rmi.RemoteException; 
import javax.ejb.SessionBean; 
import javx.ejb.SessionContext; 
public class AddBean Implements SessionBean 
{ 
//some method declare 
}
 ```
### MVC的各个部分都有那些技术来实现?如何实现： 
答:MVC是Model－View－Controller的简写。"Model" 代表的是应用的业务逻辑（通过JavaBean，EJB组件实现）， "View" 是应用的表示面（由JSP页面产生），"Controller" 是提供应用的处理过程控制（一般是一个Servlet），通过这种设计模型把应用逻辑，处理过程和显示逻辑分成不同的组件实现。这些组件可以进行交互和重用。

### J2EE是什么： 
答:Je22是Sun公司提出的多层(multi-diered),分布式(distributed),基于组件(component-base)的企业级应用模型(enterpriese application model).在这样的一个应用系统中，可按照功能划分为不同的组件，这些组件又可在不同计算机上，并且处于相应的层次(tier)中。所属层次包括客户层(clietn tier)组件,web层和组件,Business层和组件,企业信息系统(EIS)层。

### WEB SERVICE名词解释。JSWDL开发包的介绍。JAXP、JAXM的解释。SOAP、UDDI,WSDL解释： 
答：Web Service描述语言WSDL 
SOAP即简单对象访问协议(Simple Object Access Protocol)，它是用于交换XML编码信息的轻量级协议。 
UDDI 的目的是为电子商务建立标准；UDDI是一套基于Web的、分布式的、为Web Service提供的、信息注册中心的实现标准规范，同时也包含一组使企业能将自身提供的Web Service注册，以使别的企业能够发现的访问协议的实现标准。

### STRUTS的应用(如STRUTS架构) ：
答：Struts是采用Java Servlet/JavaServer Pages技术，开发Web应用程序的开放源码的framework。 采用Struts能开发出基于MVC(Model-View-Controller)设计模式的应用构架。 Struts有如下的主要功能： 
一.包含一个controller servlet，能将用户的请求发送到相应的Action对象。 
二.JSP自由tag库，并且在controller servlet中提供关联支持，帮助开发员创建交互式表单应用。 
三.提供了一系列实用对象：XML处理、通过Java reflection APIs自动处理JavaBeans属性、国际化的提示和消息。

### 开发中都用到了那些设计模式?用在什么场合：
答：每个模式都描述了一个在我们的环境中不断出现的问题，然后描述了该问题的解决方案的核心。通过这种方式，你可以无数次地使用那些已有的解决方案，无需在重复相同的工作。主要用到了MVC的设计模式。用来开发JSP/Servlet或者J2EE的相关应用。简单工厂模式等。

### 存储过程和函数的区别：
存储过程是用户定义的一系列sql语句的集合，涉及特定表或其它对象的任务，用户可以调用存储过程，而函数通常是数据库已定义的方法，它接收参数并返回某种类型的值并且不涉及特定用户表。

### 事务是什么：
事务是作为一个逻辑单元执行的一系列操作，一个逻辑工作单元必须有四个属性，称为 ACID（原子性、一致性、隔离性和持久性）属性，只有这样才能成为一个事务：
原子性：
事务必须是原子工作单元；对于其数据修改，要么全都执行，要么全都不执行。
一致性：
事务在完成时，必须使所有的数据都保持一致状态。在相关数据库中，所有规则都必须应用于事务的修改，以保持所有数据的完整性。事务结束时，所有的内部数据结构（如 B 树索引或双向链表）都必须是正确的。
隔离性：
由并发事务所作的修改必须与任何其它并发事务所作的修改隔离。事务查看数据时数据所处的状态，要么是另一并发事务修改它之前的状态，要么是另一事务修改它之后的状态，事务不会查看中间状态的数据。这称为可串行性，因为它能够重新装载起始数据，并且重播一系列事务，以使数据结束时的状态与原始事务执行的状态相同。
持久性：
事务完成之后，它对于系统的影响是永久性的。该修改即使出现系统故障也将一直保持。

### 游标的作用？如何知道游标已经到了最后：
游标用于定位结果集的行，通过判断全局变量@@FETCH_STATUS可以判断是否到了最后，通常此变量不等于0表示出错或到了最后。

触发器分为事前触发和事后触发，这两种触发有和区别。语句级触发和行级触发有何区别：
事前触发器运行于触发事件发生之前，而事后触发器运行于触发事件发生之后。通常事前触发器可以获取事件之前和新的字段值。
语句级触发器可以在语句执行前或后执行，而行级触发在触发器所影响的每一行触发一次。

### bean 实例的生命周期：
         对于Stateless Session Bean、Entity Bean、Message Driven Bean一般存在缓冲池管理，而对于Entity Bean和Statefull Session Bean存在Cache管理，通常包含创建实例，设置上下文、创建EJB Object（create）、业务方法调用、remove等过程，对于存在缓冲池管理的Bean，在create之后实例并不从内存清除，而是采用缓冲池调度机制不断重用实例，而对于存在Cache管理的Bean则通过激活和去激活机制保持Bean的状态并限制内存中实例数量。

### remote接口和home接口主要作用：
         remote接口定义了业务方法，用于EJB客户端调用业务方法
         home接口是EJB工厂用于创建和移除查找EJB实例。

### 客服端调用EJB对象的几个基本步骤：
一、  设置JNDI服务工厂以及JNDI服务地址系统属性。
二、  查找Home接口。
三、  从Home接口调用Create方法创建Remote接口。
四、  通过Remote接口调用其业务方法。

### 什么时候用assert： 
断言是一个包含布尔表达式的语句，在执行这个语句时假定该表达式为 true。如果表达式计算为 false，那么系统会报告一个 AssertionError。它用于调试目的： 
```
assert(a > 0); // throws an AssertionError if a <= 0 
```
### 断言可以有两种形式： 
assert Expression1 ; 
assert Expression1 : Expression2 ; 
Expression1 应该总是产生一个布尔值。 
Expression2 可以是得出一个值的任意表达式。这个值用于生成显示更多调试信息的 String 消息。 
断言在默认情况下是禁用的。要在编译时启用断言，需要使用 source 1.4 标记： 
javac -source 1.4 Test.java 
要在运行时启用断言，可使用 -enableassertions 或者 -ea 标记。 
要在运行时选择禁用断言，可使用 -da 或者 -disableassertions 标记。 
要系统类中启用断言，可使用 -esa 或者 -dsa 标记。还可以在包的基础上启用或者禁用断言。 
可以在预计正常情况下不会到达的任何位置上放置断言。断言可以用于验证传递给私有方法的参数。不过，断言不应该用于验证传递给公有方法的参数，因为不管是否启用了断言，公有方法都必须检查其参数。不过，既可以在公有方法中，也可以在非公有方法中利用断言测试后置条件。另外，断言不应该以任何方式改变程序的状态。

### 是否可以继承String类： 
String类是final类故不可以继承。

### 面向对象的特征有哪些方面：

抽象：抽象就是忽略一个主题中与当前目标无关的那些方面，以便更充分地注意与当前目标有关的方面。抽象并不打算了解全部问题，而只是选择其中的一部分，暂时不用部分细节。抽象包括两个方面，一是过程抽象，二是数据抽象。

继承：继承是一种联结类的层次模型，并且允许和鼓励类的重用，它提供了一种明确表述共性的方法。对象的一个新类可以从现有的类中派生，这个过程称为类继承。新类继承了原始类的特性，新类称为原始类的派生类（子类），而原始类称为新类的基类（父类）。派生类可以从它的基类那里继承方法和实例变量，并且类可以修改或增加新的方法使之更适合特殊的需要。

封装：封装是把过程和数据包围起来，对数据的访问只能通过已定义的界面。面向对象计算始于这个基本概念，即现实世界可以被描绘成一系列完全自治、封装的对象，这些对象通过一个受保护的接口访问其他对象。

多态性：多态性是指允许不同类的对象对同一消息作出响应。多态性包括参数化多态性和包含多态性。多态性语言具有灵活、抽象、行为共享、代码共享的优势，很好的解决了应用程序函数同名问题。

### String是最基本的数据类型吗：

基本数据类型包括byte、int、char、long、float、double、boolean和short。

java.lang.String类是final类型的，因此不可以继承这个类、不能修改这个类。为了提高效率节省空间，我们应该用StringBuffer类。

### String 和StringBuffer的区别：

JAVA平台提供了两个类：String和StringBuffer，它们可以储存和操作字符串，即包含多个字符的字符数据。这个String类提供了数值不可改变的字符串。而这个StringBuffer类提供的字符串进行修改。当你知道字符数据要改变的时候你就可以使用StringBuffer。典型地，你可以使用StringBuffers来动态构造字符数据。

### 说出ArrayList,Vector, LinkedList的存储性能和特性：

ArrayList和Vector都是使用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据快而插入数据慢，Vector由于使用了synchronized方法（线程安全），通常性能上较ArrayList差，而LinkedList使用双向链表实现存储，按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入速度较快。

同步和异步有何异同，在什么情况下分别使用他们？举例说明。

如果数据将在线程间共享。例如正在写的数据以后可能被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就是共享数据，必须进行同步存取。当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。

### heap和stack有什么区别：

栈是一种线形集合，其添加和删除元素的操作应在同一段完成。栈按照后进先出的方式进行处理。堆是栈的一个组成元素。

EJB与JAVA BEAN的区别:

java Bean 是可复用的组件，对Java Bean并没有严格的规范，理论上讲，任何一个Java类都可以是一个Bean。但通常情况下，由于Java Bean是被容器所创建（如Tomcat）的，所以Java Bean应具有一个无参的构造器，另外，通常Java Bean还要实现Serializable接口用于实现Bean的持久性。Java Bean实际上相当于微软COM模型中的本地进程内COM组件，它是不能被跨进程访问的。Enterprise Java Bean 相当于DCOM，即分布式组件。它是基于Java的远程方法调用（RMI）技术的，所以EJB可以被远程访问（跨进程、跨计算机）。但EJB必须被布署在诸如Webspere、WebLogic这样的容器中，EJB客户从不直接访问真正的EJB组件，而是通过其容器访问。EJB容器是EJB组件的代理，EJB组件由容器所创建和管理。客户通过容器来访问真正的EJB组件。

Static Nested Class 和 Inner Class的不同:

Static Nested Class是被声明为静态（static）的内部类，它可以不依赖于外部类实例被实例化。而通常的内部类需要在外部类实例化后才能实例化。

Java的接口和C++的虚类的相同和不同处:

由于Java不支持多继承，而有可能某个类或对象要使用分别在几个类或对象里面的方法或属性，现有的单继承机制就不能满足要求。与继承相比，接口有更高的灵活性，因为接口中没有任何实现代码。当一个类实现了接口以后，该类要实现接口里面所有的方法和属性，并且接口里面的属性在默认状态下面都是public static,所有方法默认情况下是public.一个类可以实现多个接口。

你所知道的集合类都有哪些？主要方法:

最常用的集合类是 List 和 Map。 List 的具体实现包括 ArrayList 和 Vector，它们是可变大小的列表，比较适合构建、存储和操作任何类型对象的元素列表。 List 适用于按数值索引访问元素的情形。 Map 提供了一个更通用的元素存储方法。 Map 集合类用于存储元素对（称作“键”和“值”），其中每个键映射到一个值。

JSP的内置对象及方法:

request表示HttpServletRequest对象。它包含了有关浏览器请求的信息，并且提供了几个用于获取cookie, header, 和session数据的有用的方法,response表示HttpServletResponse对象，并提供了几个用于设置送回 浏览器的响应的方法（如cookies,头信息等）. 

out对象是javax.jsp.JspWriter的一个实例，并提供了几个方法使你能用于向浏览器回送输出结果。 pageContext表示一个javax.servlet.jsp.PageContext对象。它是用于方便存取各种范围的名字空间、servlet相关的对象的API，并且包装了通用的servlet相关功能的方法。 

session表示一个请求的javax.servlet.http.HttpSession对象。Session可以存贮用户的状态信息  applicaton 表示一个javax.servle.ServletContext对象。这有助于查找有关servlet引擎和servlet环境的信息  config表示一个javax.servlet.ServletConfig对象。该对象用于存取servlet实例的初始化参数。  page表示从该页面产生的一个servlet实例。

线程的基本概念、线程的基本状态以及状态之间的关系：

线程指在程序执行过程中，能够执行程序代码的一个执行单位，每个程序至少都有一个线程，也就是程序本身。Java中的线程有四种状态分别是：运行、就绪、挂起、结束。 

JSP的常用指令：
 
<%@page language=”java” contenType=”text/html;charset=gb2312” session=”true” buffer=”64kb” autoFlush=”true” isThreadSafe=”true” info=”text” errorPage=”error.jsp” isErrorPage=”true” isELIgnored=”true” pageEncoding=”gb2312” import=”java.sql.*”%>
 
isErrorPage(是否能使用Exception对象)，isELIgnored(是否忽略表达式) <%@include file=”filename”%><%@taglib prefix=”c”uri=”http://……”%>

四种会话跟踪技术：

cookie,url重写,session,隐藏域。

简述逻辑操作(&,|,^)与条件操作(&&,||)的区别：

区别主要答两点：a.条件操作只能操作布尔型的,而逻辑操作不仅可以操作布尔型,而且可以操作数值型b.逻辑操作不会产生短路。
Request对象的主要方法：

setAttribute(String name,Object)：设置名字为name的request的参数值

getAttribute(String name)：返回由name指定的属性值

getAttributeNames()：返回request对象所有属性的名字集合，结果是一个枚举的实例

getCookies()：返回客户端的所有Cookie对象，结果是一个Cookie数组

getCharacterEncoding()：返回请求中的字符编码方式

getContentLength()：返回请求的Body的长度

getHeader(String name)：获得HTTP协议定义的文件头信息

getHeaders(String name)：返回指定名字的request Header的所有值，结果是一个枚举的实例

getHeaderNames()：返回所以request Header的名字，结果是一个枚举的实例

getInputStream()：返回请求的输入流，用于获得请求中的数据

getMethod()：获得客户端向服务器端传送数据的方法

getParameter(String name)：获得客户端传送给服务器端的有name指定的参数值

getParameterNames()：获得客户端传送给服务器端的所有参数的名字，结果是一个枚举的实例

getParameterValues(String name)：获得有name指定的参数的所有值

getProtocol()：获取客户端向服务器端传送数据所依据的协议名称

getQueryString()：获得查询字符串

getRequestURI()：获取发出请求字符串的客户端地址

getRemoteAddr()：获取客户端的IP地址

getRemoteHost()：获取客户端的名字

getSession([Boolean create])：返回和请求相关Session

getServerName()：获取服务器的名字

getServletPath()：获取客户端所请求的脚本文件的路径

getServerPort()：获取服务器的端口号

removeAttribute(String name)：删除请求中的一个属性

J2EE是技术还是平台还是框架：

J2EE本身是一个标准，一个为企业分布式应用的开发提供的标准平台。

J2EE也是一个框架，包括JDBC、JNDI、RMI、JMS、EJB、JTA等技术。

编写 java文件的注意事项：

在记事本中编写java文件，在保存时一定要把文件名和扩展名用双引号括起来，否则将默认保存为文本文件，如果要保存的java 文件名为Program1.java,则在保存时在文件名文本框中一定要输入”Program1.java”。

如何编译java程序：

单击开始|运行命令，在命令行上输入cmd，按回车键（在 window98中输入command，按回车键），即可打开一个命令窗口，将目录转换到编写java源程序所在的目录，输入javac filename.java

如何执行java程序：

同样在命令窗口中输入java filename。

简述synchronized和java.util.concurrent.locks.Lock的异同:

主要相同点：Lock能完成synchronized所实现的所有功能主要不同点：Lock有比synchronized更精确的线程语义和更好的性能。synchronized会自动释放锁，而Lock一定要求程序员手工释放，并且必须在finally从句中释放。

EJB的角色和三个对象：

一个完整的基于EJB的分布式计算结构由六个角色组成，这六个角色可以由不同的开发商提供，每个角色所作的工作必须遵循Sun公司提供的EJB规范，以保证彼此之间的兼容性。这六个角色分别是EJB组件开发者（Enterprise Bean Provider） 、应用组合者（Application Assembler）、部署者（Deployer）、EJB 服务器提供者（EJB Server Provider）、EJB 容器提供者（EJB Container Provider）、系统管理员（System Administrator）三个对象是Remote（Local）接口、Home（LocalHome）接口，Bean类

EJB容器提供的服务：

主要提供声明周期管理、代码产生、持续性管理、安全、事务管理、锁和并发行管理等服务。

EJB规范规定EJB中禁止的操作有哪些： 

1. 不能操作线程和线程API(线程API指非线程对象的方法如notify,wait等)，

2. 不能操作awt，

3. 不能实现服务器功能，

4. 不能对静态属生存取，

5. 不能使用IO操作直接存取文件系统，

6. 不能加载本地库.，

7. 不能将this作为变量和返回，

8. 不能循环调用。

remote接口和home接口主要作用：

remote接口定义了业务方法，用于EJB客户端调用业务方法。home接口是EJB工厂用于创建和移除查找EJB实例

bean 实例的生命周期对于：

Stateless Session Bean、Entity Bean、Message Driven Bean一般存在缓冲池管理，而对于Entity Bean和Statefull Session Bean存在Cache管理，通常包含创建实例，设置上下文、创建EJB Object（create）、业务方法调用、remove等过程，对于存在缓冲池管理的Bean，在create之后实例并不从内存清除，而是采用缓冲池调度机制不断重用实例，而对于存在Cache管理的Bean则通过激活和去激活机制保持Bean的状态并限制内存中实例数量。

EJB的激活机制：

以Stateful Session Bean 为例：其Cache大小决定了内存中可以同时存在的Bean实例的数量，根据MRU或NRU算法，实例在激活和去激活状态之间迁移，激活机制是当客户端调用某个EJB实例业务方法时，如果对应EJB Object发现自己没有绑定对应的Bean实例则从其去激活Bean存储中（通过序列化机制存储实例）回复（激活）此实例。状态变迁前会调用对应的ejbActive和ejbPassivate方法。

EJB的几种类型：

会话（Session）Bean ，实体（Entity）Bean 消息驱动的（Message Driven）Bean  ；

会话Bean又可分为有状态（Stateful）和无状态（Stateless）两种；

实体Bean可分为Bean管理的持续性（BMP）和容器管理的持续性（CMP）两种

如何给weblogic指定大小的内存：

在启动Weblogic的脚本中（位于所在Domian对应服务器目录下的startServerName），增加set MEM_ARGS=-Xms32m -Xmx200m，可以调整最小内存为32M，最大200M

如何设定的weblogic的热启动模式(开发模式)与产品发布模式：

可以在管理控制台中修改对应服务器的启动模式为开发或产品模式之一。或者修改服务的启动文件或者commenv文件，增加set PRODUCTION_MODE=true。

如何启动时不需输入用户名与密码：

修改服务启动文件，增加 WLS_USER和WLS_PW项。也可以在boot.properties文件中增加加密过的用户名和密码.

在weblogic管理制台中对一个应用域(或者说是一个网站,Domain)进行jms及ejb或连接池等相关信息进行配置后,实际保存在什么文件中?保存在此Domain的config.xml文件中，它是服务器的核心配置文件。

说说weblogic中一个Domain的缺省目录结构?比如要将一个简单的helloWorld.jsp放入何目录下,然的在浏览器上就可打入http://主机:端口号//helloword.jsp就可以看到运行结果了? 又比如这其中用到了一个自己写的javaBean该如何办：

Domain目录\服务器目录\applications，将应用目录放在此目录下将可以作为应用访问，如果是Web应用，应用目录需要满足Web应用目录要求，jsp文件可以直接放在应用目录中，Javabean需要放在应用目录的WEB-INF目录的classes目录中，设置服务器的缺省应用将可以实现在浏览器上无需输入应用名。

在weblogic中发布ejb需涉及到哪些配置文件：

不同类型的EJB涉及的配置文件不同，都涉及到的配置文件包括ejb-jar.xml,weblogic-ejb-jar.xmlCMP实体Bean一般还需要weblogic-cmp-rdbms-jar.xml 

如何在weblogic中进行ssl配置与客户端的认证配置或说说j2ee(标准)进行ssl的配置：

缺省安装中使用DemoIdentity.jks和DemoTrust.jks  KeyStore实现SSL，需要配置服务器使用Enable SSL，配置其端口，在产品模式下需要从CA获取私有密钥和数字证书，创建identity和trust keystore，装载获得的密钥和数字证书。可以配置此SSL连接是单向还是双向的。

如何查看在weblogic中已经发布的EJB：

可以使用管理控制台，在它的Deployment中可以查看所有已发布的EJB

CORBA是什么?用途是什么：

CORBA 标准是公共对象请求代理结构(Common Object Request Broker Architecture)，由对象管理组织 (Object Management Group，缩写为 OMG)标准化。它的组成是接口定义语言(IDL), 语言绑定(binding:也译为联编)和允许应用程序间互操作的协议。 其目的为：用不同的程序设计语言书写在不同的进程中运行，为不同的操作系统开发。

说说你所熟悉或听说过的j2ee中的几种常用模式?及对设计模式的一些看法：

  Session Facade Pattern：使用SessionBean访问EntityBean；Message Facade Pattern：实现异步调用；EJB Command Pattern：使用Command JavaBeans取代SessionBean，实现轻量级访问；Data Transfer Object Factory：通过DTO Factory简化EntityBean数据提供特性；Generic Attribute Access：通过AttibuteAccess接口简化EntityBean数据提供特性；Business Interface：通过远程（本地）接口和Bean类实现相同接口规范业务逻辑一致性；ＥＪＢ架构的设计好坏将直接影响系统的性能、可扩展性、可维护性、组件可重用性及开发效率。项目越复杂，项目队伍越庞大则越能体现良好设计的重要性。

说说在weblogic中开发消息Bean时的persistent与non-persisten的差别：

persistent方式的MDB可以保证消息传递的可靠性,也就是如果EJB容器出现问题而JMS服务器依然会将消息在此MDB可用的时候发送过来，而non－persistent方式的消息将被丢弃。

常用的设计模式？说明工厂模式： 

Java中的23种设计模式：Factory（工厂模式），Builder（建造模式）， Factory Method（工厂方法模式），Prototype（原始模型模式），Singleton（单例模式）， Facade（门面模式），Adapter（适配器模式）， Bridge（桥梁模式）， Composite（合成模式），Decorator（装饰模式）， Flyweight（享元模式）， Proxy（代理模式），Command（命令模式）， Interpreter（解释器模式）， Visitor（访问者模式），Iterator（迭代子模式）， Mediator（调停者模式）， Memento（备忘录模式），Observer（观察者模式），State（状态模式），Strategy（策略模式），Template Method（模板方法模式）， Chain Of Responsibleity（责任链模式）。

工厂模式：工厂模式是一种经常被使用到的模式，根据工厂模式实现的类可以根据提供的数据生成一组类中某一个类的实例，通常这一组类有一个公共的抽象父类并且实现了相同的方法，但是这些方法针对不同的数据进行了不同的操作。首先需要定义一个基类，该类的子类通过不同的方法实现了基类中的方法。然后需要定义一个工厂类，工厂类可以根据条件生成不同的子类实例。当得到子类的实例后，开发人员可以调用基类中的方法而不必考虑到底返回的是哪一个子类的实例。

请对以下在J2EE中常用的名词进行解释(或简单描述):

web容器：给处于其中的应用程序组件（JSP，SERVLET）提供一个环境，使JSP,SERVLET直接更容器中的环境变量接口交互，不必关注其它系统问题。主要有WEB服务器来实现。例如：TOMCAT,WEBLOGIC,WEBSPHERE等。该容器提供的接口严格遵守J2EE规范中的WEB APPLICATION 标准。我们把遵守以上标准的WEB服务器就叫做J2EE中的WEB容器。EJB容器：Enterprise java bean 容器。更具有行业领域特色。他提供给运行在其中的组件EJB各种管理功能。只要满足J2EE规范的EJB放入该容器，马上就会被容器进行高效率的管理。并且可以通过现成的接口来获得系统级别的服务。例如邮件服务、事务管理。JNDI：（Java Naming & Directory Interface）JAVA命名目录服务。主要提供的功能是：提供一个目录系统，让其它各地的应用程序在其上面留下自己的索引，从而满足快速查找和定位分布式应用程序的功能。JMS：（Java Message Service）JAVA消息服务。主要实现各个应用程序之间的通讯。包括点对点和广播。JTA：（Java Transaction API）JAVA事务服务。提供各种分布式事务服务。应用程序只需调用其提供的接口即可。JAF：（Java Action FrameWork）JAVA安全认证框架。提供一些安全控制方面的框架。让开发者通过各种部署和自定义实现自己的个性安全控制策略。RMI/IIOP:（Remote Method Invocation /internet对象请求中介协议）他们主要用于通过远程调用服务。例如，远程有一台计算机上运行一个程序，它提供股票分析服务，我们可以在本地计算机上实现对其直接调用。当然这是要通过一定的规范才能在异构的系统之间进行通信。RMI是JAVA特有的。

一个“.java”源文件中是否可以包括多个类（不是内部类）？有什么限制：

可以。必须只有一个类名与文件名相同。

MVC的各个部分都有那些技术来实现?如何实现：

 MVC是Model－View－Controller的简写。"Model" 代表的是应用的业务逻辑（通过JavaBean，EJB组件实现）， "View" 是应用的表示面（由JSP页面产生），"Controller" 是提供应用的处理过程控制（一般是一个Servlet），通过这种设计模型把应用逻辑，处理过程和显示逻辑分成不同的组件实现。这些组件可以进行交互和重用。

java中有几种方法可以实现一个线程？用什么关键字修饰同步方法? stop()和suspend()方法为何不推荐使用：

有两种实现方法，分别是继承Thread类与实现Runnable接口用synchronized关键字修饰同步方法反对使用stop()，是因为它不安全。它会解除由线程获取的所有锁定，而且如果对象处于一种不连贯状态，那么其他线程能在那种状态下检查和修改它们。结果很难检查出真正的问题所在。suspend()方法容易发生死锁。调用suspend()的时候，目标线程会停下来，但却仍然持有在这之前获得的锁定。此时，其他任何线程都不能访问锁定的资源，除非被“挂起”的线程恢复运行。对任何线程来说，如果它们想恢复目标线程，同时又试图使用任何一个锁定的资源，就会造成死锁。所以不应该使用suspend()，而应在自己的Thread类中置入一个标志，指出线程应该活动还是挂起。若标志指出线程应该挂起，便用wait()命其进入等待状态。若标志指出线程应当恢复，则用一个notify()重新启动线程。

java中有几种类型的流？JDK为每种类型的流提供了一些抽象类以供继承，请说出他们分别是哪些类：

字节流，字符流。字节流继承于InputStream \ OutputStream，字符流继承于InputStreamReader \ OutputStreamWriter。在java.io包中还有许多其他的流，主要是为了提高性能和使用方便。

java中会存在内存泄漏吗，请简单描述：

会。如：int i,i2;  return (i-i2);   //when i为足够大的正数,i2为足够大的负数。结果会造成溢位，导致错误。

java中实现多态的机制是什么：

方法的重写Overriding和重载Overloading是Java多态性的不同表现。重写Overriding是父类与子类之间多态性的一种表现，重载Overloading是一个类中多态性的一种表现。

垃圾回收器的基本原理是什么？垃圾回收器可以马上回收内存吗？有什么办法主动通知虚拟机进行垃圾回收：

对于GC来说，当程序员创建对象时，GC就开始监控这个对象的地址、大小以及使用情况。通常，GC采用有向图的方式记录和管理堆(heap)中的所有对象。通过这种方式确定哪些对象是"可达的"，哪些对象是"不可达的"。当GC确定一些对象为"不可达"时，GC就有责任回收这些内存空间。可以。程序员可以手动执行System.gc()，通知GC运行，但是Java语言规范并不保证GC一定会执行。

静态变量和实例变量的区别：

static i = 10; //常量； class A a;  a.i =10;//可变

什么是java序列化，如何实现java序列化：

序列化就是一种用来处理对象流的机制，所谓对象流也就是将对象的内容进行流化。可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决在对对象流进行读写操作时所引发的问题。序列化的实现：将需要被序列化的类实现Serializable接口，该接口没有需要实现的方法，implements Serializable只是为了标注该对象是可被序列化的，然后使用一个输出流(如：FileOutputStream)来构造一个ObjectOutputStream(对象流)对象，接着，使用ObjectOutputStream对象的writeObject(Object obj)方法就可以将参数为obj的对象写出(即保存其状态)，要恢复的话则用输入流。

是否可以从一个static方法内部发出对非static方法的调用：

不可以,如果其中包含对象的method()；不能保证对象初始化.

写clone()方法时，通常都有一行代码，是什么：

Clone 有缺省行为，super.clone();他负责产生正确大小的空间，并逐位复制。

在JAVA中，如何跳出当前的多重嵌套循环：

用break; return 方法。

List、Map、Set三个接口，存取元素时，各有什么特点：

List 以特定次序来持有元素，可有重复元素。Set 无法拥有重复元素,内部排序。Map 保存key-value值，value可多值。

J2EE是什么：

J2EE是Sun公司提出的多层(multi-diered),分布式(distributed),基于组件(component-base)的企业级应用模型(enterpriese application model).在这样的一个应用系统中，可按照功能划分为不同的组件，这些组件又可在不同计算机上，并且处于相应的层次(tier)中。所属层次包括客户层(clietn tier)组件,web层和组件,Business层和组件,企业信息系统(EIS)层。

UML方面：

标准建模语言UML。用例图,静态图(包括类图、对象图和包图),行为图,交互图(顺序图,合作图),实现图。

说出一些常用的类，包，接口，请各举5个常用的类：

常用的类：BufferedReader  BufferedWriter  FileReader  FileWirter  String  Integer；

常用的包：java.lang  java.awt  java.io  java.util  java.sql；

常用的接口：Remote  List  Map  Document  NodeList 

开发中都用到了那些设计模式?用在什么场合:

每个模式都描述了一个在我们的环境中不断出现的问题，然后描述了该问题的解决方案的核心。通过这种方式，你可以无数次地使用那些已有的解决方案，无需在重复相同的工作。主要用到了MVC的设计模式。用来开发JSP/Servlet或者J2EE的相关应用。简单工厂模式等。

jsp有哪些动作?作用分别是什么：

 JSP共有以下6种基本动作：

 jsp:include：在页面被请求的时候引入一个文件。 

jsp:useBean：寻找或者实例化一个JavaBean。 

jsp:setProperty：设置JavaBean的属性。 

jsp:getProperty：输出某个JavaBean的属性。 

jsp:forward：把请求转到一个新的页面。 

jsp:plugin：根据浏览器类型为Java插件生成OBJECT或EMBED标记。

Anonymous Inner Class (匿名内部类) 是否可以extends(继承)其它类，是否可以implements(实现)interface(接口)： 

可以继承其他类或完成其他接口，在swing编程中常用此方式。

应用服务器与WEB SERVER的区别：

应用服务器：Weblogic、Tomcat、Jboss； WEB SERVER：IIS、 Apache

BS与CS的联系与区别：

C/S是Client/Server的缩写。服务器通常采用高性能的PC、工作站或小型机，并采用大型数据库系统，如Oracle、Sybase、Informix或 SQL Server。客户端需要安装专用的客户端软件。B/Ｓ是Brower/Server的缩写，客户机上只要安装一个浏览器（Browser），如Netscape Navigator或Internet Explorer，服务器安装Oracle、Sybase、Informix或 SQL Server等数据库。在这种结构下，用户界面完全通过WWW浏览器实现，一部分事务逻辑在前端实现，但是主要事务逻辑在服务器端实现。浏览器通过Ｗeb Server 同数据库进行数据交互。

C/S 与 B/S 区别： 

１． 硬件环境不同: C/S 一般建立在专用的网络上, 小范围里的网络环境, 局域网之间再通过专门服务器提供连接和数据交换服务；　B/S 建立在广域网之上的, 不必是专门的网络硬件环境,例与电话上网, 租用设备. 信息自己管理. 有比C/S更强的适应范围, 一般只要有操作系统和浏览器就行 

２． 对安全要求不同 ：C/S 一般面向相对固定的用户群, 对信息安全的控制能力很强. 一般高度机密的信息系统采用C/S 结构适宜. 可以通过B/S发布部分可公开信息.B/S 建立在广域网之上, 对安全的控制能力相对弱, 可能面向不可知的用户。

３． 对程序架构不同 ：　C/S 程序可以更加注重流程, 可以对权限多层次校验, 对系统运行速度可以较少考虑.　B/S 对安全以及访问速度的多重的考虑, 建立在需要更加优化的基础之上. 比C/S有更高的要求 B/S结构的程序架构是发展的趋势, 从MS的.Net系列的BizTalk 2000 Exchange 2000等, 全面支持网络的构件搭建的系统. SUN 和IBM推的JavaBean 构件技术等,使 B/S更加成熟. 

４． 软件重用不同： C/S 程序可以不可避免的整体性考虑, 构件的重用性不如在B/S要求下的构件的重用性好.　B/S 对的多重结构,要求构件相对独立的功能. 能够相对较好的重用.就入买来的餐桌可以再利用,而不是做在墙上的石头桌子 。

５． 系统维护不同  ：C/S 程序由于整体性, 必须整体考察, 处理出现的问题以及系统升级. 升级难. 可能是再做一个全新的系统，　B/S 构件组成,方面构件个别的更换,实现系统的无缝升级. 系统维护开销减到最小.用户从网上自己下载安装就可以实现升级. 

６． 处理问题不同 ：C/S 程序可以处理用户面固定, 并且在相同区域, 安全要求高需求, 与操作系统相关. 应该都是相同的系统，B/S 建立在广域网上, 面向不同的用户群, 分散地域, 这是C/S无法作到的. 与操作系统平台关系最小. 

７． 用户接口不同： C/S 多是建立的Window平台上,表现方法有限,对程序员普遍要求较高，B/S 建立在浏览器上, 有更加丰富和生动的表现方式与用户交流. 并且大部分难度减低,减低开发成本. 

８．信息流不同 ：　C/S 程序一般是典型的中央集权的机械式处理, 交互性相对低，B/S 信息流向可变化,        B-B B-C B-G等信息、流向的变化, 更像交易中心。

EJB2.0有哪些内容?分别用在什么场合? EJB2.0和EJB1.1的区别：

答：规范内容包括Bean提供者，应用程序装配者，EJB容器，EJB配置工具，EJB服务提供者，系统管理员。这里面，EJB容器是EJB之所以能够运行的核心。EJB容器管理着EJB的创建，撤消，激活，去活，与数据库的连接等等重要的核心工作。JSP,Servlet,EJB,JNDI,JDBC,JMS.....

CORBA是什么?用途是什么： 

答：CORBA 标准是公共对象请求代理结构(Common Object Request Broker Architecture)，由对象管理组织 (Object Management Group，缩写为 OMG)标准化。它的组成是接口定义语言(IDL), 语言绑定(binding:也译为联编)和允许应用程序间互操作的协议。 其目的为： 用不同的程序设计语言书写 在不同的进程中运行 为不同的操作系统开发 

应该对oracle有所了解，对一些数据库的名词，应该知道词的解释:

分页一 前提  希望最新的纪录在开头给你的表建立查询： 表：mytable  
 
查询：create or replace view as mytable_view from mytable order by id desc 其中，最好使用序列号create sequence mytable_sequence 来自动增加你的纪录id号  二 源程序  <%String sConn="你的连接"  

Class.forName("oracle.jdbc.driver.OracleDriver");  Connection conn=DriverManager.getConnection(sConn,"你的用户名","密码");  

Statement stmt=conn.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE,ResultSet.CONCUR_UPDATABLE);  

Statement stmtcount=conn.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE,ResultSet.CONCUR_UPDATABLE);  

ResultSet rs=stmt.executeQuery("select * from mytable_view");  String sqlcount="select count(*) from mytable_view";  ResultSet rscount=stmtcount.executeQuery(sqlcount);  int pageSize=你的每页显示纪录数；  int rowCount=0; //总的记录数  while (rscount  int pageCount; //总的页数  int currPage; //当前页数  

String strPage;  strPage=request.getParameter("page");  if (strPage==null){  currPage=1;  }  else{  

currPage=Integer.parseInt(strPage);  if (currPage<1) currPage=1;  }  pageCount=(rowCount+pageSize-1)/pageSize;  if (currPage>pageCount) currPage=pageCount;  int thepage=(currPage-1)*pageSize;  

int n=0;  rs.absolute(thepage+1);  while (n<(pageSize)&&!rs  %>  <%rs.close();  rscount.close();  stmt.close();  stmtcount.close();  conn.close();  %>  //下面是 第几页等  
```
<form name="sinfo" method="post" action="sbinfo_index.jsp?condition=<%=condition%>&type=<%=type%>" onSubmit="return testform(this)">  第<%=currPage%>页 共<%=pageCount%>页 共<%=rowCount%>条  

<%if(currPage>1){%><a href="sbinfo_index.jsp?condition=<%=condition%>&type=<%=type%>">首页</a><%}%>  

<%if(currPage>1){%><a href="sbinfo_index.jsp?page=<%=currPage-1%>&condition=<%=condition%>&type=<%=type%>">上一页</a><%}%>  <%if(currPage<pageCount){%><a href="sbinfo_index.jsp?page=<%=currPage+1%>&condition=<%=condition%>&type=<%=type%>">下一页</a><%}%>  

<%if(pageCount>1){%><a href="sbinfo_index.jsp?page=<%=pageCount%>&condition=<%=condition%>&type=<%=type%>">尾页</a><%}%>  跳到<input type="text" name="page" size="4" style="font-size:9px">页  

<input type="submit" name="submit" size="4" value="GO" style="font-size:9px">  </form>  
 ```
Java 的通信编程，编程题(或问答)，用JAVA SOCKET编程，读服务器几个字符，再写入本地显示： 

答:Server端程序:
 ```
 package test; import java.net.*; import java.io.*; public class Server { private ServerSocket ss; private Socket socket; 

private BufferedReader in; private PrintWriter out; public Server() { try { ss=new ServerSocket(10000); while(true) { socket = ss.accept(); 

String RemoteIP = socket.getInetAddress().getHostAddress(); String RemotePort = ":"+socket.getLocalPort(); System.out.println("A client come in!IP:"+RemoteIP+RemotePort); in = new BufferedReader(new InputStreamReader(socket.getInputStream())); String line = in.readLine(); System.out.println("Cleint send is :" + line); out = new PrintWriter(socket.getOutputStream(),true); out.println("Your Message Received!"); out.close(); in.close(); socket.close(); } }catch (IOException e) { out.println("wrong"); } } public static void main(String[] args) { new Server(); } } 
 
 
Client端程序: package test; import java.io.*; import java.net.*; public class Client { Socket socket; BufferedReader in; PrintWriter out; public Client() { try { System.out.println("Try to Connect to 127.0.0.1:10000"); socket = new Socket("127.0.0.1",10000); System.out.println("The Server Connected!"); System.out.println("Please enter some Character:"); BufferedReader line = new BufferedReader(new InputStreamReader(System.in)); out = new PrintWriter(socket.getOutputStream(),true); 
```
Out
 
文件读写的基本类：

答：File Reader 类和FileWriter类分别继承自Reader类和Writer类。FileReader类用于读取文件，File Writer类用于将数据写入文件，这两各类在使用前，都必须要调用其构造方法创建相应的对象，然后调用相应的read()或 write()方法。

托普集团程序员面试试一、选择题(每题1分，共20分)

1． 下列那种语言是面向对象的（C）

A. C          B. PASCAL        C. C++          D. FORTRAN77

2．在 Windows9x 下，可以进入 MS-D0S 方式。当在 DOS 提示符下键入 ( B ) 命令后，系统将退出 MS-DOS方式，返回到 WIndows 方式。 A. CLOSE   B. EXIT       C. QUIT        D. RETURN

3．下面哪些是面向对象的基本特性：( ABC)A 多态      B 继承       C 封装         D 接口

4．在C++中经常要进行异常处理，下面哪些是异常处理常用到的关键词：(ABC)

    A try         B catch       C throw         D break E contiue

5．数据库技术中的“脏数据',是指（C）的数据。A.错误B.回返C.未提交D.未提交的随后又被撤消

6．TCP/IP是一种（A,B）A.标准       B.协议       C.语言        D.算法

7． 下面有关计算机操作系统的叙述中，不正确的是(B ) A 操作系统属于系统软件 B 操作系统只负责管理内存储器，而不管理外存储器 C  UNIX 是一种操作系统 D 计算机的处理器、内存等硬件资源也由操作系统管理

8．微机上操作系统的作用是( D) A 解释执行源程序          B 编译源程序 

C 进行编码转换            D 控制和管理系统资源

9．下列存储器中存取速度最快的是( A) A 内存 B 硬盘 C 光盘 D 软盘

10．在计算机中，—个字节是由多少个二进制位组成的(B ) A. 4        B. 8        C. 16         D. 24

11. 存储16×16点阵的一个汉字信息，需要的字节数为( A )A 32        B 64        C 128        D 256

12. 以下选项中合法的字符常量是（BC）A."B"       B. '\010'     C. 68         D. D

13. 假定x和y为double型，则表达式x=2,y=x+3/2的值是（D）A. 3.500000  B. 3 C. 2.000000    D. 3.000000

14. 以下合法的赋值语句是（BCD）//In C++ ,choice D also is correct, but in C language, D is wrong.

A. x=y=100  B. d--;      C. x+y;        D. c=int(a+b);

15. 设正x、y均为整型变量，且x=10 y=3，则以下语句pprintf("%d,%d\n",x--,--y); 的输出结果是（D）

A.10,3      B. 9,3       C. 9,2         D.10,2

16. x、y、z被定义为int型变量，若从键盘给x、y、z输入数据，正确的输入语句是（B）

A .INPUT x、y、z;  B. scanf("%d%d%d",&x,&y,&z);C. scanf("%d%d%d",x,y,z);     D. read("%d%d%d",&x,&y,&z);

17.以下数组定义中不正确的是（D）A) int a[2][3];            B) int b[][3]={0,1,2,3};C) int c[100][100]={0};    D) int d[3][]={{1,2},{1,2,3},{1,2,3,4}};

18. 以下程序的输出结果是（A）main(){ int a[4][4]={{1,3,5},{2,4,6},{3,5,7}};

printf("%d%d%d%d\n",a[0][3],a[1][2],a[2][1],a[3][0];

}A) 0650     B) 1470      C) 5430     D) 输出值不定

19 以下程序的输出结果是（B）main(){char st[20]= "hello\0\t\\\";printf(%d %d \n",strlen(st),sizeof(st));

}A) 9 9        B) 5 20       C) 13 20      D) 20 20

20. 当调用Windows API函数InvalidateRect,将会产生什么消息（A）A:WM_PAINT           B:WM_CREATE   C:WM_NCHITTEST      D:WM_SETFOCUS

二、填空题(每题3分，共30分)

1．请列举当前一些当前流行的数据库引擎,SQL SERVER,ORACLE,BDE,Microsoft Jet。

2． 为了将当前盘当前目录中的所有文本文件（扩展名为.TXT）的内容打印输出，正确的单条DOS命令为COPY  *.TXT  PRN。

3． 计算机网络分为局域网和广域网，因特网属于广域网。

4. 设y是int型变量，请写出判断y为奇效的关系表达y%2！=0。

5. 设有以下程序:main(){ int n1,n2;scanf("%d",&n2);while(n2!=0){ n1=n2%10;n2=n2/10;printf("%d",n1);}}

程序运行后，如果从键盘上输入1298；则输出结果为8921。

6．以下程序运行后的输出结果是:9876  876

main(){ char s[ ]="9876",*p;for ( p=s ; p<s+2 ; p++) printf("%s\n", p);}

7．以下函数的功能是：求x的y次方，请填空。double fun( double x, int y){ int i;double z;for(i=1, z=x; i<y;i++) z=z*  x  ;return z;}

8．以下程序段打开文件后，先利用fseek函数将文件位置指针定位在文件末尾，然后调用ftell函数返回当前文件位置指针的具体位置，从而确定文件长度，请填空。FILE *myf; long f1;myf=  fopen  ("test.t","rb");

fseek(myf,0,SEEK_END); f1=ftell(myf);fclose(myf);printf("%d\n",f1);

9. 以下程序输出的最后一个值是120。

int ff(int n){ static int f=l;f=f*n;return f;}main(){ int i;for(I=1;I<=5;I++ printf("%d\n",ff(i));)

10. 以下程序运行后的输出结果是52  main(){ int i=10, j=0;do{ j=j+i; i--;while(i>2);printf("%d\n",j);}

三、判断题(每题2分，共20分)

  1：动态链结库不能静态调用。     错误         

  2：UDP是面向无连接的网络连接     正确       

  3：ASP是一种数据库引擎           错误       

  4：队列是先进后出。                错误  

  5：Weblogic是分布式应用服务器。        正确 

  6：TCP,UDP都是传输层的协议。       正确   

  7: 两个线程不能共存于同一地址空间       错误

  8: JAVA是一种跨平台的开发工具           正确

  9．在WINDOWS操作系统中对外设是以文件的方式进行管理   正确

  10. 虚拟内存实际是创建在硬盘上的  正确

四、问答题(每题10分，共30分)

１． 写出从数据库表Custom中查询No、Name、Num1、Num2并将Name以姓名显示、计算出的和以总和显示的SQL。

SELECT  No ,  Name  AS  ‘姓名’ ，Num1 ，Num2，（Num1+Num2） AS  ‘总和’

FROM Custom

2. 何为“事务处理”，谈谈你对它的理解

事务处理是指一个单元的工作，这些工作要么全做，要么全部不做。作为一个逻辑单元，必须具备四个属性：自动性、一致性、独立性和持久性。自动性是指事务必须是一个自动的单元工作，要么执行全部数据的修改，要么全部数据的修改都不执行。一致性是指当事务完成时，必须使所有数据都具有一致的状态。在关系型数据库中，所有的规则必须应用到事务的修改上，以便维护所有数据的完整性。所有的内部数据结构，在事务结束之后，必须保证正确。独立性是指并行事务的修改必须与其他并行事务的修改相互独立。一个事务看到的数据要么是另外一个事务修改这些事务之前的状态，要么是第二个事务已经修改完成的数据，但是这个事务不能看到正在修改的数据。

3. 常用的数据结构有哪些？请枚举一些。（不少于5个）

链表、堆栈、二叉树、队列、图、堆，集合。

4. 什么是OOP？什么是类？请对比类和对象实例之间的关系。

OOP是Object_oriented Programming(面向对象编程)的缩写。这主要是为了区别于以前的面向过程的程序设计！指的是用对象的观点来组织与构建系统，它综合了功能抽象和数据抽象，这样可以减少数据之间的耦合性和代码的出错几率。使用面向对象编程技术可以使得软件开发者按照现实世界里人们思考问题的模式编写代码,可以让软件开发者更好地利用代码直接表达现实中存在的对象,将问题空间直接映射到解空间!类：即class 在面向对象的程序设计中，专门用“类”来表示用户定义的抽象数据类型（user_defined abstract type）。它将具有相同状态、操作和访问机制的多个对象进行了抽象。类具有继承、数据隐藏和多态三种主要特性。利用类的这三种特性可以更好地表示现实世界中事物。类是同一类对象实例的共性的抽象，对象是类的实例化。对象通常作为计算机模拟思维，表示真实世界的抽象，一个对象就像一个软件模块，可以为用户提供一系列的服务--可以改变对象的状态、测试、传递消息等。类定义了对象的实现细节或数据结构。类是静态的，对象是动态的，对象可以看作是运行中的类。类负责产生对象，可以将类当成生产对象的工厂（Object factory）.

5. 有一组数字（3，10，6，8，98，22），请编程排序（升降序皆可），语言不限，算法不限，但须注明是何种算法。//下面使用简单的冒泡法进行排序！

 

#include "iostream.h"  template<class type>  class CBubble{

private: type *pArray; int size;public:CBubble(type a[],int sizeArray);void sort();void display();};

template <class type> CBubble<type>::CBubble(type a[],int sizeArray)

{ pArray=a; size=sizeArray/sizeof(type);}

template<class type>void CBubble<type>::sort(){  type temp;  for(int i=0;i<size-1;i++) for(int j=0;j<size-1-i;j++) if(pArray[j]>pArray[j+1])//升序{temp=pArray[j+1];pArray[j+1]=pArray[j];pArray[j]=temp;}}

template<class type>void CBubble<type>::display(){for(int i=0;i<size;i++)cout<<pArray[i]<<endl;}

void main(void){int a[]={3,10,6,8,98,22};CBubble<int> intData(a,sizeof(a));cout<<"The original data are :"<<endl;intData.display();intData.sort();cout<<"After sorting ,the data are:"<<endl;intData.display();

}

 

SQLhttp://www.jactiongroup.net/reference/html/index.html  //书
http://blog.csdn.net/hbuzhang/archive/2004/12/07/207202.aspx //书

connection connconn.setAuto(false)//表示手动提交conn.commit// 提交conn.rollback();//事务回滚

 
-内联接
use pubsselect a.au_fname, a.au_lname, p.pub_name  from authors a inner join publishers p on a.city = p.city order by p.pub_name asc, a.au_lname asc,   a.au_fname asc
--左外联接

use pubs  select a.au_fname, a.au_lname, p.pub_name  from authors a left join publishers p

on a.city = p.city  order by p.pub_name asc,  a.au_lname asc,   a.au_fname asc

-使用子查询

USE pubs  GO  SELECT distinct pub_name  FROM publishers  WHERE pub_id IN  (SELECT pub_idFROM titlesWHERE type = 'business')  GO

--如果平均价格少于 $30，WHILE 循环就将价格加倍，然后选择最高价。

--如果最高价少于或等于 $50，WHILE 循环重新启动并再次将价格加倍。

--该循环不断地将价格加倍直到最高价格超过 $50 
`
 USE pubs  GO

WHILE (SELECT AVG(price) FROM titles) < $30

BEGIN

   UPDATE titles

      SET price = price * 2

   SELECT MAX(price) FROM titles

   IF (SELECT MAX(price) FROM titles) > $50

      BREAK

   ELSE

      CONTINUE

END
 
 

--如果平均价格少于 $30，WHILE 循环就将价格加倍，然后选择最高价。

--如果最高价少于或等于 $50，WHILE 循环重新启动并再次将价格加倍。

--该循环不断地将价格加倍直到最高价格超过 $50

USE pubs

GO

WHILE (SELECT AVG(price) FROM titles) < $30

BEGIN

   UPDATE titles

      SET price = price * 2

   SELECT MAX(price) FROM titles

   IF (SELECT MAX(price) FROM titles) > $50

      BREAK

   ELSE

      CONTINUE

END

CREATE PROCEDURE au_info 

   @lastname varchar(40), 

   @firstname varchar(20) 

AS 

SELECT au_lname, au_fname, title, pub_name

   FROM authors a INNER JOIN titleauthor ta

      ON a.au_id = ta.au_id INNER JOIN titles t

      ON t.title_id = ta.title_id INNER JOIN publishers p

      ON t.pub_id = p.pub_id

   WHERE  au_fname = @firstname

      AND au_lname = @lastname

GO

EXECUTE au_info 'Dull', 'Ann'--或者

EXECUTE au_info @lastname = 'Dull', @firstname = 'Ann'

--创建存储过程

CREATE PROCEDURE titles_sum @TITLE varchar(40),@SUM money OUTPUT

AS

SELECT @SUM = SUM(price)

FROM titles

WHERE title LIKE @TITLE

GO

DECLARE @TOTALCOST money

EXECUTE titles_sum 'The%', @TOTALCOST OUTPUT

select @TOTALCOST

go

CREATE PROCEDURE Oakland_authors

AS 

SELECT au_fname, au_lname, address, city, zip

FROM authors

WHERE city = 'Oakland'

and state = 'CA'

ORDER BY au_lname, au_fname

GO

--sp_helptext Oakland_authors

ALTER PROCEDURE Oakland_authors

AS 

SELECT au_fname, au_lname, address, city, zip

FROM authors

WHERE state = 'CA'

ORDER BY au_lname, au_fname

GO

--sp_helptext Oakland_authors

--提交事务后，所有书籍支付的版税增加 10%。

begin transaction MyTransaction

update roysched

set royalty = royalty * 1.10

commit transaction MyTransaction

--rollback transaction MyTransaction

select royalty from roysched

--select @@trancount

--1.创建试验实验表

create table temptrigger

( id_temp varchar(2) not null primary key,

  temp_name varchar(10) null,

  temp_age int null)go

insert temptrigger values('01','张三','10') 

insert temptrigger values('02','李四','11') 

insert temptrigger values('03','王五','12') 

insert temptrigger values('04','赵六','11') 

select * from temptrigger  go

--2.创建insert , update触发器

create trigger temptrigger_modify

on temptrigger

for insert,update

as

begin

  if (select temp_age from inserted) > 15

    begin

      rollback transaction

      print '年龄不能超过15岁！'

    end

end

--insert temptrigger values('04','大朋','17') 

--insert temptrigger values('05','大朋','17') 

--insert temptrigger values('05','大朋','14') 

--update temptrigger set temp_age='18' where id_temp = '01'

--update temptrigger set temp_age='9' where id_temp = '01'

-3.创建delete 触发器：

drop trigger temptrigger_delete

create trigger temptrigger_delete

on temptrigger

for delete

as

begin

  print @@rowcount

  if @@rowcount > 1

  begin

    rollback transaction

    print '一次删除记录不能多于1条'

  end

end
 
 
--delete from temptrigger

--delete from temptrigger where id_temp='01'

--创建聚集索引create clustered index clindx_titleid  on roysched(title_id)--sp_help roysched

--创建非聚集索引create nonclustered index unclindx_titleid  on roysched(title_id)--sp_help roysched

--查看索引统计dbcc show_statistics(roysched,titleidind)

--更新索引统计update statistics authors

--重建索引dbcc dbreindex('roysched',unclindx_titleid)

--删除索引drop index roysched.unclindx_titleid-sp_help roysched

1--创建ssn(社会保险号)的基于varchar的自定义数据类型。

--用于存储11位社会保险号（999-99-999）的列。该列不能为null：

use pubs  exec sp_addtype ssn , 'varchar(11)' , 'NOT NULL'

--查看创建的数据类型--sp_help ssn

--使用创建的数据类型create table mytable( myid varchar(2) primary key, myssn ssn)  
4-删除创建的数据类型--drop table mytable--exec sp_droptype ssn
 

?批是包含一个或多个 Transact-SQL 语句的组，从应用程序一次性地发送到 Microsoft SQL Server 执行。批作为一个整体执行，以GO命令结束。批处理是客户端作为一个单元发出的一个或多个 SQL 语句的集合。每个批处理编译为一个执行计划。

触发器：

触发器是在对表进行插入、更新或删除操作时自动执行的存储过程?触发器通常用于强制业务规则?触发器可以确保数据的完整性和一致性

事务：

是用户定义的一个操作序列，这些操作要么全做要么全不做，是一个不可分割的工作单位(构成单一逻辑工作单元的操作集合)如果某一事务成功，则在该事务中进行的所有数据更改均会提交，成为数据库中的永久组成部分。

如果事务遇到错误且必须取消或回滚，则所有数据更改均被清除

?锁 ：

是在多用户环境中对数据访问的限制封锁就是事务 T 在对某个数据对象（如表、记录等）操作之前，先向系统发出请求，对其加锁。加锁后事务 T 就对该数据对象有了一定的控制，在事务T释放它的锁之前，其它的事务不能更新此数据对象。（锁蕴含的基本概念是用户需要对表的排它访问）?从程序员的角度看：分为乐观锁和悲观锁。乐观锁：完全依靠数据库来管理锁的工作。悲观锁：程序员自己管理数据或对象上的锁处理。

子查询：

一个 SELECT 语句嵌套在另一个 SELECT 语句中。

索引：

是一个数据库对象，它是某个表中一列或若干列值的集合和相应的指向表中物理标识这些值的数据页的逻辑指针清单,然后根据指定的排序次序排列这些指针 —优点提高查询执行的速度。  强制实施数据的唯一性。  提高表之间联接的速度。 缺点 存储索引要占用磁盘空间。数据修改需要更长的时间，因为索引也要更新。 

?视图?：

是一种虚拟表，通常是作为来自一个或多个表 的行或列的子集创建的。?视图本质上讲，就是保存在数据库中的select查询?视图并不是数据库中存储的数据值的集合。?对最终用户的好处– 结果更容易理解– 获得数据更容易

?对开发人员的好处– 限制数据检索更容易– 维护应用程序更方便

存储过程：

使用一个名称存储的预编译T-SQL语句和流程控制语句的集合?由数据库开发人员或数据库管理员编写

?用来执行管理任务或应用复杂的业务规则  优点?执行速度更快?首次运行时，进行优化和编译得到执行计划并将该计划存储在系统表中，以后直接运行。?实现多个程序共享应用程序逻辑?组件式编程?能够屏蔽数据库的结构，实现更高的安全性

?减少网络流通量

数据库设计和建模必要性：

好的数据库结构有利于：-节省数据的存储空间-能够保证数据的完整性-方便进行数据库应用系统的开发?设计不好的数据库结构将导致-数据冗余、存储空间浪费-内存空间浪费

不管数据库的大小和复杂程度如何，可以用下列基本步骤来设计数据库：

–收集信息–标识对象–设计数据模型–标识每个对象 存储的信息类型–标识对象之间的关系

数据模型：

是一种标识实体类型及其实体间联系的模型。典型的数据模型由网状模型、层次模型和关系模型。


什么是规范化：

从关系数据库的表中，除去冗余数据的过程称为规范化。—精简数据库的结构—从表中删除冗余的列—标识所有依赖于其它数据的数据

三级范式：


第一范式的定义： 如果一个表中没有重复组（即行与列的交叉点上只有一个值，而不是一组值），则这个表属于第一范式（常记成1NF）。简而言之："每一字段只存储一个值"。例如:职工号，姓名，电话号码组成一个表（一个人可能有一个办公室电话 和一个家里电话号码） 


第二范式的定义：如果一个表属于1NF，任何属性只依赖于关键字，则这个表属于第二范式（常记成2NF ）。简而言之：必须先符合1NF的条件，且每一行都能被唯一的识别。 

第三范式的定义：将1NF转换成2NF的方法是添加主键。学号,课程名,成绩

第三范式的定义：如果一个表属于2NF，且不包含传递依赖性，则这个表是第三范式（常记成3NF）。满足3NF的表中不包含传递依赖。简而言之：没有一个非关键属性依赖于另一个非关键属性。学号，课程号，成绩，学分学号，姓名，所在系，系名称，系地址.

什么是类与对象：

所谓对象就是真实世界中的实体，对象与实体是一一对应的，也就是说现实世界中每一个实体都是一个对象，它是一种具体的概念。

类是具备某些共同特征的实体的集合，它是一种抽象的概念，用程序设计的语言来说，类是一种抽象的数据类型，它是对所具有相同特征实体的抽象。

属性与方法：

不同对象具有相同特点，就可能抽象为一定的类，那么这些特点基本上可以分为两类，一类是描述对象静态状态的，就是对象的属性，在程序设计中，可以称之为变量；另一类是描述对象的动作，就是对象的方法，在程序设计中我们称之为函数。属性和方法是一个对象所具备的两大基本要素，也是我们后面编程工作的核心。

什么是封装：

只要有足够的方法，就没必要直接去操作对象属性，只要调用这些方法就可以实现要完成的任务，这种现象称为封装，它通过对象方法对其属性的操作把对象属性封装在一个对象内部，对象与外界打交道全部通过其自身的方法来实现，有效的把对象属性隐藏在对象内部。

编写 java文件的注意事项：

在记事本中编写java文件，在保存时一定要把文件名和扩展名用双引号括起来，否则将默认保存为文本文件，如果要保存的java 文件名为Program1.java,则在保存时在文件名文本框中一定要输入”Program1.java”。

如何编译java程序：

单击开始|运行命令，在命令行上输入cmd，按回车键（在 window98中输入command，按回车键），即可打开一个命令窗口，将目录转换到编写java源程序所在的目录，输入`javac filename.java`

如何执行java程序：

同样在命令窗口中输入`java filename，`

基本数据类型：

Java的数据类型可以划分为4大类：整数，浮点数，字符型，布尔型。其中整数可以划分为：byte,short,int,long.浮点数可以划分为float,double
```
