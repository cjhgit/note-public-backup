# Spring

Spring的核心是控制反转（IoC）和面向切面（AOP）


多有的操作，最好基于注解方式的配置。包括@Controller、@Service、@Repository.采用注解+xml配置的方式实现，对于复杂的配置采用XML方式。
单表操作，对数据量不是很大，采用注解方式实现。
多表操作，大数据量批次操作，采用SqlSessionTemplate方式操作。


批量操作（插入、更新、删除)
使用MyBatis API(不推荐)
SqlSessionTemplate
MyBatisPagingItemReade


错误：JasperException: The absolute uri: http://java.sun.com/jsp/jstl/core cannot be resolved in either web.xml or the jar files deployed with this application 解决：jstl.jar 包在ide项目中有，但在tomcat发布的应用WEB-INF/lib下没有，这是工具发布项 目的问题，复制一个jar包过去问题就解决了。

使用maven时，所有的包都应该在pom.xml文件配置，而不是通过MyEclipse的build path直接引用jar包。如果添加了MyEclipse的自带库，maven打包时不会把MyEclipse库打包到war文件。 

错误：Unknown tag (c:forEach) 

解决：<%@ taglib prefix=”c” uri=”http://java.sun.com/jsp/jstl/core” %>   

错误：The superclass “javax.servlet.http.HttpServlet” was not found on the Java Build Path 

解决：添加java EE库   

错误：maven编码 gbk 的不可映射字符 

解决：在pom的/project/build/plugins/下的编译插件声明 中加入下面的配置： Xml代码 收藏代码 <encoding>utf8</encoding>     Apache Tomcat8必备知识 http://blog.csdn.net/chszs/article/details/9852661   JSTL 1.0 的声明是： <%@ taglib prefix=”c” uri=”http://java.sun.com/jstl/core ” %> JSTL1.1以后 的声明是： <%@ taglib prefix=”c” uri=http://java.sun.com/jsp/jstl/core %>   另外,你的 <%@ page isELIgnored=”false” %> 應該是在Servlet2.4以後才需要的吧. 我看你的Tomcat是5.0.28,應該換是Servlet2.3的環境; 去掉試試看.   

错误：ava.lang.IllegalStateException: Web app root system property already set to different value 

解决：两个web应用中定义了相同的webAppRootKey或者都没有定义，则现在就需要为每个web都定义一个webAppRootKey。 <context-param> <param-name>webAppRootKey</param-name> <param-value>app1.root</param-value> </context-param> http://www.2cto.com/kf/201301/181688.html  










http://www.what21.com/programming/java/javaweb-summary/xss3.html
http://blog.csdn.net/happylee6688/article/details/40660797


在Java开发项目中，Spring MVC通常容易受到XSS、SQL注入攻击，那么出现这种情况，我们通常的有以下几种解决方法：
1、在数据进入数据库之前对非法字符进行转义，在更新和显示的时候将非法字符还原；
2、在显示的时候对非法字符进行转义；
如果项目还处在起步阶段，建议使用第二种，直接使用jstl的标签即可解决非法字符的问题。在解析从服务器端获取的数据时执行以下escapeHTML()即可。
附：Javascript方法：
String.prototype.escapeHTML = function () {
return this.replace(/&/g,‘&’).replace(/>/g,‘>’).replace(/
}
如果项目已经开发完成了，又不想大批量改动页面的话，可以采用第一种方法，此时需要借助Spring MVC的@InitBinder以及org.apache.commons.lang.PropertyEditorSupport、org.apache.commons.lang.StringEscapeUtils
注：在使用StringEscapeUtils时需要注意escapeHtml和escapeJavascript方法会把中文字符转换成Unicode编码，如果通过标签或者EL表达式展示时，能够正确还原，但是如果使用类似于Ext这样的前端组件来展示这部分内容时，不能正常还原。
例：
public class StringEscapeEditor extends PropertyEditorSupport {
private boolean escapeHTML;
private boolean escapeJavaScript;
private boolean escapeSQL;
public StringEscapeEditor() { super(); }
public StringEscapeEditor(boolean escapeHTML, booleanescapeJavaScript, boolean escapeSQL) {
super();
this.escapeHTML = escapeHTML;
this.escapeJavaScript = escapeJavaScript;
this.escapeSQL = escapeSQL;
}
@Override
public void setAsText(String text) {
if (text == null) {
setValue(null);
} else {
String value = text;
if (escapeHTML) { value = StringEscapeUtils.escapeHtml(value); }
if (escapeJavaScript) { value =StringEscapeUtils.escapeJavaScript(value); }
if (escapeSQL) { value = StringEscapeUtils.escapeSql(value); }setValue(value); }
}
@Override
public String getAsText() { Object value = getValue(); return value
!= null ? value.toString() :“”;}
}
下面要将这个Editor和Spring的Controller绑定，使服务器端接收到数据之后能够自动转移特殊字符，在@Controller中注册@InitBinder
@InitBinder
public void initBinder(WebDataBinder binder) {
binder.registerCustomEditor(String.class, newStringEscapeEditor(false, false, false));
}