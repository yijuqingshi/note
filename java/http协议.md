 # http协议

* **定义:** http协议是基于请求/响应模式的，无状态的传输协议，属于网络传输协议的应用层。无状态体现在第一次请求后再次请求，服务器端是不知道此请求是不是上次请求的同一个用户。

* **请求格式：** http://192.168.0.1:8080/abs_path <br>
               http://ip:port/统一资源标识符
http请求由三部分组成，分别为请求行，消息报头，请求正文。

* **请求行:**  Method URI HTTP-Version CRLF(回车换行) <br>
               例如：GET /index.html/ HTTP/1.1 CRLF(回车换行)

* **消息报头：**

* **请求正文：**

  http响应由三部分组成，分别为状态行，消息报头，响应正文。

* **状态行：** HTTP-Version Status-Code 状态描述 CRLF
              例如：HTTP/1.1 200 ok CRLF


* 使用telnet服务访问远程主机，执行http协议。
              GET / HTTP/1.1
              Host:127.0.0.1


* 服务器tomcat server.xml配置逻辑路径与物理路径例子

              <Context path="/逻辑路径" docBase="物理路径" reloadable=true>
              例如：<Context path="/helloworld" docBase="E:\project\helloworld\WebRoot"
