# HttpSession接口

## Session的定义

Session用于跟踪用户的状态，Session指的是在一段时间内，单个客户与Web服务器的一连串相关的交互过程。

## Session的运行机制

* 当一个会话开始时，Servlet容器将创建一个HttpSession对象，在HttpSession对象中可以存放客户端的状态信息（例如购物车）

* Servlet容器为每一个HttpSession对象分配一个唯一的标志符，称为SessionID。

* 每次客户发送请求时，Servlet容器可以从HttpServletRequest对象中读取SessionID,然后根据SessionID找到HttpSession对象，从而获取客户状态信息。


## HttpSession的重要方法
```
getid()//获取sessionID,由Servlet容器随机生成的字符串。

invalidate()// 使HttpSession无效。

isNew() //是否是新产生的Session

setMaxInactiveInterval()设置session不活动的最大存活时间

```

## Session的声明周期

* 当客户第一次访问Web应用时，创建Session对象。（创建）

* 接着访问Web应用的其他不同网页时，始终处于同一个Session（存活）

* 调用invalidate方法或者超过不活动的最大的时间（销毁）

## Session的实际项目开发的应用

* 保存用户登录信息，做权限管理，验证user是否登录
