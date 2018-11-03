# Spring框架学习笔记

## Spring框架学习路径

* Spring的Ioc

* Spring的AOP，AspectJ

* Spring的事务管理

## Spring框架的概述

* Spring是分层的JavaSE/EE full-stack(一站式) 轻量级开源框架

* sun提供的EE的三层结构:web层、业务层、数据访问层（持久层，集成层）

  * Struts2是web层基于MVC设计模式框架.
  * Hibernate是持久的一个ORM的框架.
  <br>
* Spring框架有对三层的一站式解决方案

   * web层:Spring MVC
   * 持久层:JDBC Template
   * 业务层:Spring的Bean管理
   <br>
* Spring的出现是为了取代EJB的臃肿、低效、脱离现实

## Spring的核心
* IOC:（Inverse of Control 反转控制）

  控制反转:将对象的创建权,交由Spring完成.

* AOP : Aspect Oriented Programming 是 面向对象的功能延伸.不是替换面向对象,是用来解决OO中一些问题.



## Spring的版本
* Spring3.x和Spring4.x Spring4需要整合hibernate4.

## Spring优点

* 方便解耦，简化开发

* Spring就是一个大工厂，可以将所有对象创建和依赖关系维护，交给Spring管理

* AOP编程的支持

  * Spring提供面向切面编程，可以方便的实现对程序进行权限拦截、运行监控等功能
* 声明式事务的支持

  * 只需要通过配置就可以完成对事务的管理，而无需手动编程
* 方便程序的测试

  * Spring对Junit4支持，可以通过注解方便的测试Spring程序
* 方便集成各种优秀框架

  * Spring不排斥各种优秀的开源框架，其内部提供了对各种优秀框架（如：Struts、Hibernate、MyBatis、Quartz等）的直接支持

* 降低JavaEE API的使用难度

  * Spring 对JavaEE开发中非常难用的一些API（JDBC、JavaMail、远程调用等），都提供了封装，使这些API应用难度大大降低


  ## Spring体系结构
  * Spring 框架是一个分层架构,它包含一系列的功能要素并被分为大约20个模块。这些模块分为Core Container、Data Access/Integration、Web、AOP（Aspect Oriented Programming)、Instrumentation和测试部分。
