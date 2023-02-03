---
title: Spring
category: Java
---

### 1、Spring

------

##### 1.1、简介(用于面试)

- 2002年首次推出了Spring框架的雏形
- “不要重复发明轮子（Don't Reinvent Wheel）”,意思是企业中任何一项工作实际上都有人做过，软件领域中有的功能或者是项目，别人已经做过，我们需要用的时候，直接拿来用即可，而不需要重新创造。可以很好的来解释Spring框架。
- Spring保持强大的向后兼容性。
- 解决企业应用开发的复杂性
- Spring是一个轻量级控制反转（IoC）和面向切面（AOP）的容器框架
- Spring的理念：使现有的技术更加容易使用
- SSH（Struct2 + Spring + Hibernate）
- SSM(Spring + SpringMVC + Mybatis)

##### 1.2、优点、缺点

1. 优点

- 开源免费框架（容器）

- 轻量级，<u>非侵入式的框架</u>
- <u>控制反转（IoC），面向切面编程（AOP）</u>

2. 缺点

- 发展太久之后，违背了原来的理念，配置非常繁琐。（很多同学都在Spring的配置文件上劝退了）

##### 1.3、组成

![image-20200909231721960](/Users/louwenbo/Desktop/image-20200909231721960.png)

##### 1.4、拓展

<img src="/Users/louwenbo/Desktop/image-20200909220617974.png" alt="image-20200909220617974" style="zoom: 50%;" />

- Spring Boot
  - 一个快速开发的脚手架
  - 基于SpringBoot可以快速的开发单个微服务
  - 约定大于配置（COC）
- Spring Cloud
  - SpringCloud是基于SpringBoot实现的

目前很多大公司都在使用SpringBoot进行快速开发，学习SpringBoot的前提，需要完全掌握Spring及SpringMVC

### 2、IoC理论推导

1. UserDao接口
2. UserDaoImpl实现类
3. UserService业务接口
4. UserServiceImpl业务员实现类

- 在之前所学习的编程里（例如 JavaSE），用户的需求可能会影响我们原来的代码，我们需要根据用户的需求去修改源代码，如果程序代码量十分大，修改一次的成本代价十分昂贵。

  - 例如在2020年1-4月份期间自己独立开发（Visual Basic）的排版系统，编写的变量，常量非常多，如果遇到一些特殊的需求（因为疫情会改变排版的基本需求），程序不能满足的话，需要回到源代码的层面上去更改数据，难免是麻烦的，甚至在一些设计不周的情况下出现意想不到的bug。

    <img src="/Users/louwenbo/Desktop/image-20200909223653923.png" alt="image-20200909223653923" style="zoom: 50%;" />

- 之前，程序是主动创建对象，控制权在程序员手上
- 使用了一些方法（例如Set注入），程序不再具有主动性，而是变成了被动的接受对象

这种思想，从本质上解决了问题，<u>程序员不用再去管理对象的创建了。系统的耦合性大大降低，可以使开发更加注重在业务的实现上</u>，这是IoC的原型。

### 3、IoC本质

-   **控制反转IoC（Inversion of Control）,是一种设计思想，DI依赖注入（Dependence Injection）是实现IoC的方法。**在没有IoC的程序中，我们使用面向对象编程，对象的创建与对象间的依赖关系完全硬编码在程序中，对象的创建由程序自己控制，控制反转后将对象的创建转移给第三方。
-   **IoC是Spring框架的核心内容**，使用多种方式完美的实现了IoC，可以使用XML配置，也可以使用注解，新版本的Spring也可以零配置实现IoC。
-   采用XML方式配置Bean的时候，Bean的定义信息是和现实分离的，而采用注解的方式可以把两者合为一体，Bean的定义信息直接以注解的形式定义在实现类中，从而达到了零配置的目的。











