# Listener接口

 * Listener种类
 ```
 ServletContextListener  //监听服务器初始化和销毁

 HttpSessionListener //监听Seesion的创建与销毁

 HttpSessionAttributeListener //监听session的属性增加与删除等

 ServletContextAttributeListener //监听Context的属性变化。

 ```
 * 用法

 ```
  自定义监听器实现上述接口，配置在web.xml文件里

  public class MyListener implments ServletContextListener{

      public void contextInitialized(ServletContextEvent sce)
      {

      }

      public void contextDestroyed(ServletContextEvent sce)
      {

      }
  }

  web.xml配置

  <listener/>
    <listener-class>com.zyh.learnweb.servlet.Listener</listener-class>
  </listener>

 ```
