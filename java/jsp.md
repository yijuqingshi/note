# JSP学习

* JSP基本语法
          <%= "yangwei" %>  等价 out.println("yangwei")
          <% %>  JSP脚本  /java代码/
          <%! int a;%> 声明变量
          <%@ page contentType="text/html;charset=UTF-8" language="java" %>
          <%@ include file="相对路径" %>

* JSP表象上是切入了java片段的html页面，本质上是servlet的java类。写好的jsp文件都是在服务器端执行完后将输入返回给客户端的。

* JSP执行的一般流程：客户端请求，服务器端判断是否是修改后的第一次请求，如果是的话，服务器先通过jsp解析器将jsp转换成servlet的java文件，然后再编译成class文件，执行完后将结果返回给客户端。否则将直接执行class文件返回结果。

* JSP内置对象


1. request对象 <br>  类型： javax.servlet.ServletRequest的子类

  重要方法：request.getParameter("name");获取from表单对应的参数值
  <br>request.getParameterValues("name")参数值多个的情况
  <br>request.getParameterNames("")获取参数名称


2. session对象 <br> 类型：HttpSession

   重要方法：setAttribute("name","object") getAttribute("name")

   说明：session可以保存每一个客户端提交的数据一段特定的时间。

3. session.setAttribute方法与request.setAttribute的区别   
   request.getAttribute方法保存的值只能在一次请求中可以获取，而session.setAttribute方法保存的值能保存到关闭浏览器之前都能获取到。

4. application对象<br> 类型：ServletContext

   重要方法 setAttribute() getAttribute() 用法与session，request对象一样，但是什么周期与服务器什么周期一样，永远只有一个，所以所有客户端访问都获取同一个application对象

   application.getRealPath("/news") //获取服务器上news文件的硬盘的路径


   * 总结：request的什么周期是一次请求，请求结果就销毁，session对象什么周期与浏览器一样，每起一个新的浏览器界面访问就对象一个session对象，application对象与服务器什么周期一样，所有浏览器共用一个。


  *  <jsp:forward page="request3.jsp"></jsp:forward>  //请求转发至request.jsp中执行

5. 请求转发与重定向的区别

   请求转发的实现方式： request.getRequestDispatcher("myResult.jsp");
   RequestDispatcher.forward(req,resp);

   重定向的实现方式：resp.sendRedirect("myResult.jsp")

   //参数说明： "/myResult.jsp" 加上/则是相对tomcat根路径开始，相对http://127.0.0.1:8080 没有加/ 则相对请求路径
   <br> 例如 请求路径是 http://127.0.0.1:8080/demo/request.jsp，那么myResult.jsp是request.jsp同一个目录下，如果是aaa/myResult.jsp 则是
   http://127.0.0.1:8080/demo/aaa/myResult.jsp

   区别1：请求转发能将请求参数与保存进请求的数据传递给下一个页面。
   <br>原因:请求转发，整个过程在同一个请求里，重定向是两次请求，第一次请求完后，服务器给客户端返回定向的资源文件路径，客户端再请求定向资源文件。
   RequestDispatcher.forward方法是请求对象的方法，而sendRedirect方法是响应对象的方法。

6. 投票管理系统

7. JavaScropt获取元素对象的值的方式：<br>

   var username = document.getElementById("username")<br>
   var elements = document.getElementsByName("username")<br>