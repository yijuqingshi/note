# JSP学习

## JSP基本语法


    <%= "yangwei" %>  等价 out.println("yangwei")
    <% %>  JSP脚本  /java代码/
    <%! int a;%> 声明变量
    <%@ page contentType="text/html;charset=UTF-8" language="java" %>
    <%@ page import="java.util.* " %>
    <%@ include file="相对路径" %>  //jsp指令



* JSP表象上是切入了java片段的html页面，本质上是servlet的java类。写好的jsp文件都是在服务器端执行完后将输入返回给客户端的。

* JSP执行的一般流程：客户端请求，服务器端判断是否是修改后的第一次请求，如果是的话，服务器先通过jsp解析器将jsp转换成servlet的java文件，然后再编译成class文件，执行完后将结果返回给客户端。否则将直接执行class文件返回结果。

## JSP内置对象


* request对象 <br>
  类型： javax.servlet.ServletRequest的子类
```
  重要方法

  request.getParameter("name");获取from表单对应的参数值

  <br>request.getParameterValues("name")参数值多个的情况

  <br>request.getParameterNames("")获取参数名称
```

2. session对象 <br>

   类型：HttpSession

   重要方法：
   ```
   session.setAttribute("name","object")
   session.getAttribute("name")
   ```
   说明：session可以保存每一个客户端提交的数据一段特定的时间。

3. application对象<br>

  类型：ServletContext
   ```
   重要方法:
   application.setAttribute()
   application.getAttribute()

   //获取服务器上news文件的硬盘的路径
   application.getRealPath("/news")

   用法与session，request对象一样，但是什么周期与服务器什么周期一样，永远只有一个，所以所有客户端访问都获取同一个application对象
   ```


   * 总结：<br>
   request的生命周期是一次请求，请求响应结果后就销毁，session对象生命周期与浏览器一样，每起一个新的浏览器界面访问就有一个session对象，application对象与服务器什么周期一样，所有浏览器共用一个,所以他们的保存的属性的生命周期各自不同。




### 请求转发与重定向

   * 请求转发的实现方式：
   ```
   Servlet实现方式

   request.getRequestDispatcher("myResult.jsp");
   RequestDispatcher.forward(req,resp);

   Jsp实现方式

   //请求转发至request3.jsp中执行
   <jsp:forward page="request3.jsp"></jsp:forward>  

   ```

* 重定向的实现方式：

    ```
    resp.sendRedirect("myResult.jsp")

    参数说明：
    "/myResult.jsp" 加上/则是相对tomcat根路径开始，相对
    http://127.0.0.1:8080
    没有加/ 则相对请求路径开始

    例如:
    请求路径是
    http://127.0.0.1:8080/demo/request.jsp

    那么myResult.jsp是request.jsp同一个目录下，
    如果是aaa/myResult.jsp 则是
    http://127.0.0.1:8080/demo/aaa/myResult.jsp
   ```
   区别：请求转发能将请求参数与保存进请求里的数据传递给下一个页面。

   原因:请求转发，整个过程在同一个请求里，重定向则是两次请求，第一次请求完后，服务器给客户端返回定向的资源文件路径，客户端再请求定向资源文件。
   RequestDispatcher.forward方法是请求对象的方法，而sendRedirect方法是响应对象的方法。

6. 投票管理系统
    ```
   1.jsp(显示界面给用户填写问题内容，选择个数，问题类型)

   2.servlet处理用户提交，并根据问题的个数，显示选项内容框的jsp

   3.用户提交后处理用户提交数据到servlet中，servlet获取提交信息
   后交给xml工具类进行xml文件构建保存后，转向jsp显示结果。

   4.用户访问servlet后通过xml工具类获取xml数据后，转向jsp显示所有
   问题，用户填完问题后，提交给servlet处理，并更新xml
   ```

## Javabean


### JavaBean特性<br>
```  
  1.JavaBean是一个public类<br>
  2.JavaBean有一个不带参数的构造方法<br>
  3.JavaBean通过set get方法设置获取属性<br>

  主要目的是用反射去操作javabean
```
### Jsp访问javabean语法<br>

```
  1.导入javabean类<br>
  2.声明javabean对象<br>
  3.访问javabean属性

  //导入javabean类<br>
  <%@ page import="com.zyh.yw.User" %>

  //声明javabean对象<br>
  <jsp:useBean id="mUser" class="com.zyh.yw.User" scope="session"/>

  //获取javaBean的name属性
  <jsp:getProperty name="mUser" property="name">

```
### javaBean的生命周期范围<br>

```
  1. socpe = page  //当前页面有效
  2. socpe = request //当前请求
  3. socpe = session //用法与session一样
  4. socpe = application //application一样

  实现原理是将javabean通过 setAttribute方法放置对应的对象中

```
* 作业 js实现客户端验证，servlet实现服务器验证


## EL表达式


EL表达式用于jsp中简化java代码。

### 用法

```
${param.username}

等价

<$
  String username =  request.getParamter("username");
$>
<$= username$>

```
### 内置对象

```
pageScope     类型都是Map
requestScope
sessionScope
applicationScope
param
paramValues
用法
${sessionScope.user.name}
${sessionScope.user["my-name"]} []这种方式能处理特殊字符，或者变量。
等价

((User)session.getAttribute("user")).getName();

```

## 自定义标签库

 ### 自定义JSP标签的步骤

 * 创建标签处理类

  定义标签处理类方法是继承TagSupport类，或者是TagBodySupport
  然后重写doStartTag方法，doEndTag方法
  ```
  public class MyTag extends TagSupport {

      @Override
      public int doStartTag() throws JspException {
          return EVAL_BODY_INCLUDE;
      }

      @Override
      public int doEndTag() throws JspException {
          return EVAL_PAGE;
      }
      //EVAL_BODY_INCLUDE 包括标签内的内容
      //EVAL_PAGE 包括标签后内容
  }

  ```

 * 创建标签库描述文件

   创建MyTag.tld文件，例如
   ```
   <?xml version="1.0" encoding="UTF-8" ?>

   <taglib>
      <short-name>myTag</short-name>
      <uri>/myTag<uri>
      <tag>
        <description>
        Subtag of &lt;choose&gt; that includes its body if its
        condition evalutes to 'true'
        </description>
        <name>mytag</name>
        <tag-class>
          org.apache.taglibs.standard.tag.rt.core.WhenTag
        </tag-class>
      </tag>
    </taglib>
   ```
 * 在JSP文件中引入标签库，然后插入标签，例如："<"mm:hello">"
  ```
  1.在JSP文件中引入标签库
  <@<%@ taglib uri="/myTag" prefix="hello"%>>
  2.插入标签
  <hello:mytag>
    hello
  </hello:mytag>
  ```
