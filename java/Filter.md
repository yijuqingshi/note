# Filter接口

Servlet过滤器能够对Servlet容器的请求与响应对象进行修改,Servlet过滤器本
身不会生成请求和响应对象，只是做过滤的作用。

## 过滤器的作用

* 过滤器能在Servlet被调用之前修改Request对象的内容，包括Request Header，request的内容

* 过滤器能在Servlet被调用之后修改Response对象的内容，包括Response Header,包括Response的内容

* 过滤的web组件可以是html，jsp,Servlet。


## 创建Servlet过滤器的方法

* 实现Filter接口就是一个过滤器（单实例）

  ```
  init(); FilterConfig参数可以获取web.xml文件里配置的参数
  doFilter();（chain.doFilter）参数FilterChain用于后续过滤器的说明。
  distory();
  ```
* web.xml配置

  ```
  <filter>
       <filter-name>myFilter</filter-name>
       <filter-class>com.zyh.learnweb.servlet.MyFilter</filter-class>
   </filter>

   <filter-mapping>
       <filter-name>myFilter</filter-name>
       //需要过滤的url
       <url-pattern>/*</url-pattern>
   </filter-mapping>
  ```


## 串联过滤器

 * 过滤器的执行流程

 ```

   public void doFilter(ServletRequest,ServletResponse,FilterChain chain)
   {
            //请求时执行的代码
            System.ont.println("过滤请求的代码");

            chain.doFilter(req,resp);//转向下一个过滤组件/或者Servlet
            执行

            //执行完请求之后，会到此处执行响应的过滤代码
            System.out.println("过滤响应的代码");
   }

   单个过滤器执行流程：

   客户端请求---doFilter -- 请求过滤代码 --- chain.doFilter() ---

   --Servlet -- 响应过滤的代码-- 客户端

   串联过滤器执行流程：

   客户端请求---doFilter1-- 请求过滤代码1---chain.doFilter() ---

   ---doFilter2-- 请求过滤代码2 --chain.doFilter()---Servlet---

   ---响应过滤代码2 --- 响应过滤代码1--客户端

   注意配置：Filter1配置在前面，Filter2配置在后
 ```
