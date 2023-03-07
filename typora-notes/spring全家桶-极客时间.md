# JDBC必知必会

## 那些好用的连接池

### HikariCP

号称性能很好，比其他的都好很多，里面有很多关于性能的代码优化，之所以HikariCP这么快是因为HikariCP在各个地方做了各种各样的优化。

HikariCP是spring boot 2.x默认自带的数据库连接池，只要配置spring.datasource.hikari.*即可（spring boot1.x 默认是tomcat的连接池



### Druid

最大的特点就是监控，帮助发现很多问题，而且强调不会影响太多的性能。能防SQL注入，内置logging能诊断hack行为。

有一个界面，可以实时的看到数据的一些状态。



内置ExceptionSorter，数据库密码加密等。

还有一个特点，扩展点很多，在很多地方都有扩展点可以让我们扩展。

配置：

![image-20220704104919088](spring全家桶-极客时间.assets/image-20220704104919088.png)

![image-20220704105010831](spring全家桶-极客时间.assets/image-20220704105010831.png)



上面包括了一些SQL防注入的能力。

![image-20220704105117930](spring全家桶-极客时间.assets/image-20220704105117930.png)

这个是怎么使用filter做扩展。



另外，如果你要引入其他的连接池，那么要在starter-jdbc里面把hikariCP排除掉



### 如何选择连接池

![image-20220704105326446](spring全家桶-极客时间.assets/image-20220704105326446.png)





# O/R mapping

## 认识JPA

![image-20220704105834651](spring全家桶-极客时间.assets/image-20220704105834651.png)



![image-20220704105920740](spring全家桶-极客时间.assets/image-20220704105920740.png)



## Mybatis



![image-20220704111412766](spring全家桶-极客时间.assets/image-20220704111412766.png)

![image-20220704112422336](spring全家桶-极客时间.assets/image-20220704112422336.png)



![image-20220704112519067](spring全家桶-极客时间.assets/image-20220704112519067.png)



![image-20220704112600742](spring全家桶-极客时间.assets/image-20220704112600742.png)





# 链路追踪

![image-20220704132512500](spring全家桶-极客时间.assets/image-20220704132512500.png)

Span可以理解为一次RPC调用，Trace



![image-20220704132633017](spring全家桶-极客时间.assets/image-20220704132633017.png)





## spring cloud sleuth

![image-20220704132844833](spring全家桶-极客时间.assets/image-20220704132844833.png)

![image-20220704132940430](spring全家桶-极客时间.assets/image-20220704132940430.png)





# 数据访问进阶

## 通过AOP打印数据访问层的摘要



![image-20220706094821519](spring全家桶-极客时间.assets/image-20220706094821519.png)



![image-20220706095846913](spring全家桶-极客时间.assets/image-20220706095846913.png)



Druid内置有输出功能，

但是HikariCp是没有的，要借助其他工具，比如P6Spy
