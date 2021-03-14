# TOMCAT架构总览

## 一、文件结构

- bin：存放可执行的文件，如startup，shutdown
- conf：存放配置文件，如核心配置文件server.xml和应用默认的部署描述文件web.xml
- lib：存放Tomcat运行需要的jar
- logs：存放运行的日志文件
- webapps：存放默认的web应用部署目录
- work：存放web应用代码生成和编译文件的临时目录

## 二、首层结构Service

在tomcat容器下的首层结构就是Service，Service可以有多个，这个设计可以理解为多个Service为对应多个webapps文件，当你使用两个相同名称的war包，可以考虑这么用。

![p1](/home/caikun/Desktop/my md/tomcat/pic/p1.jpg)

Service内部的核心组件只有两个，一个是Connector，负责接收和返回请求;另一个是Container，负责处理请求。

## 三、Connector的内部结构

### 1.功能

- 监听网络端口，接收/响应网络请求。
- 网络字节流处理。Connector先接到网络字节流-转化->Tomcat request-转化->ServletRequest 后交给Container，Container返回的ServletResponse也会最后被转化为网络字节流。

### 2.结构

- Endpoint:处理Socket接收和发送，其内部由Acceptor监听请求，Handler处理数据。AsyncTimeout检查i请求超时。一般使用NioEndPoint
- Processor：构建Tomcat request和Response对象。Http11Processor
- Adapter：Tomcat request，Response与ServletRequest，ServletResponse之间相互转换。

![](/home/caikun/Desktop/my md/tomcat/pic/p2.jpg)

在源码中需要关注Acceptor和poller之间的关系。（生产消费）

## 四、Container

### 1.功能

- Engine：管理多个虚拟主机
- Host：
- Context：
- Wrapper：封装servlet

![](/home/caikun/Desktop/my md/tomcat/pic/p3.jpg)

### 2.请求过程

容器的请求处理过程就是在 Engine、Host、Context 和 Wrapper 这四个容器之间层层调用，最后在 Servlet 中执行对应的业务逻辑。各容器都会有一个通道 Pipeline，每个通道上都会有一个 Basic Valve（如StandardEngineValve）， 类似一个闸门用来处理 Request 和 Response 。

打开 tomcat/conf 目录下的 server.xml 文件来分析一个http://localhost:8080/docs/api 请求。

第一步：连接器监听的端口是8080。由于请求的端口和监听的端口一致，连接器接受了该请求。

第二步：因为引擎的默认虚拟主机是 localhost，并且虚拟主机的目录是webapps。所以请求找到了 tomcat/webapps 目录。

第三步：解析的 docs 是 web 程序的应用名，也就是 context。此时请求继续从 webapps 目录下找 docs 目录。有的时候我们也会把应用名省略。

第四步：解析的 api 是具体的业务逻辑地址。此时需要从 docs/WEB-INF/web.xml 中找映射关系，最后调用具体的函数。



整理自： https://zhuanlan.zhihu.com/p/248426114