# Servlet接口

每一个Servlet都必须实现Servlet接口，HttpServlet是对Http协议请求的封装。
## Servlet接口方法

```
init(); //初始化

service(); //处理请求

destroy();//销毁

getServletConfig(); //启动配置

getServletInfo()//Servlet信息
```

## GenericServlet类
GenericServlet是通用的无协议的，不特定协议的Servlet。
```
简单的实现了init方法，和destory()方法。
```
## HttpServlet类

httpServlet是对http协议的请求的封装，实现了service方法，并根据客户端请求的方法类型，调用对应的方法。会将请求的ServletRequest,ServletResponse对象强制类型转换成HttpServletRequest,HttpServletResponce对象。

```
doGet();

doPost();

doDelet();
····等
```

## Servlet容器加载Servlet的时刻(初始化阶段)

* Servlet容器启动时自动加载（web.xml的load-on-startup元素控制）

* 启动Servlet容器后，客户端第一次请求Servlet时会加载

* Servlet类文件被更新后，会加载。

*  Servlet的init方法，在生命周期内只调用一次。

## ServletRequest接口(响应客户请求阶段)

HttpServletRequest，HttpServletResponce对象都由Servlet容器创建。

* 封装请求参数

```
getRemoteHost()//远程主机名

getRemoteAddr()//获取远程主机IP

getParameter()//获取客户提交的参数

getRequestDispatcher()//获取请求转发对象

getInputStream()//获取请求输入流
```

## ServletResponse接口(响应客户请求阶段)
* 封装响应参数

```


```
## Servelt销毁阶段(终止阶段)

* Servlet容器，Web应用被终止时，重新加载Servlet实例时会调用Distory方法释放资源。


## Servlet多线程情况的考虑
 * Servlet是单实例的，会处理所有的请求，所以当多个请求访问Servlet
 成员变量时，要考虑多线程的问题，解决办法最好的办法时，用局部变量代替成员变量。


 ## Cookie
服务器端可以向客户端发送多个cookie，也可以获取客户端发送过来的cookie，默认会将Session对象的ID发送给客户端。
```
 Cookie  Cookie = new Cookie(key，value);

 //获取Cookie  request.getCookies();
 //放松Cookie  response.addCookie();

```
