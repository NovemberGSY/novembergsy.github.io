---
title: Servlet
category: Java
---
### **Servlet**

- Servlet主要用于处理客户端传来的HTTP请求，并返回一个响应，它能够处理的请求有doGet()和doPost()等方法。
- Servlet由Servlet容器提供，所谓的Servlet容器是指提供了Servlet 功能的服务器（例如Tomcat），Servlet容器将Servlet动态的加载到服务器上。与HTTP 协议相关的Servlet使用HTTP请求和HTTP响应与客户端进行交互。因此，Servlet容器支持所有HTTP协议的请求和响应。Servlet应用程序的体系结构如图所示。

![image-20200825092752267](/Users/louwenbo/Library/Application Support/typora-user-images/image-20200825092752267.png)

- Servlet的请求首先会被HTTP服务器接收，HTTP服务器只负责静态HTML页面的解析，对于Servlet的请求转交给Servlet容器，Servlet容器会根据web.xml文件中的映射关系，调用相应的Servlet，Servlet将处理的结果返回给Servlet容器，并通过HTTP服务器将响应传输给客户端。

- Servlet技术具有如下特点：

- - 方便：Servlet提供了大量的实用工具例程，如处理很难完成的HTML表单数据、读取和设置HTTP头，以及处理Cookie和跟踪会话等。
  - 跨平台：Servlet用Java类编写，可以在不同操作系统平台和不同应用服务器平台下运行。
  - 灵活性和可扩展性：采用Servlet开发的Web应用程序，由于Java类的继承性及构造函数等特点，使得应用灵活，可随意扩展。