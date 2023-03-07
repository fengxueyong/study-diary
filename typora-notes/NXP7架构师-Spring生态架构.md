# **Spring生态架构设计与实践**

## spring生态和演进分析

![image-20220701095621152](NXP7架构师-Spring生态架构.assets/image-20220701095621152.png)



![image-20220701095807329](NXP7架构师-Spring生态架构.assets/image-20220701095807329.png)

![image-20220701100342529](NXP7架构师-Spring生态架构.assets/image-20220701100342529.png)



![image-20220701100444978](NXP7架构师-Spring生态架构.assets/image-20220701100444978.png)

spring做了哪些。如上。







Iaas，Paas,Saas,Faas，Baas

![image-20220701101832481](NXP7架构师-Spring生态架构.assets/image-20220701101832481.png)



![image-20220701102047205](NXP7架构师-Spring生态架构.assets/image-20220701102047205.png)



三大两小

Web apps包括spring MVC等

spring batch：离线的，大数据相关的。

![image-20220701102340586](NXP7架构师-Spring生态架构.assets/image-20220701102340586.png)





![image-20220701102900029](NXP7架构师-Spring生态架构.assets/image-20220701102900029.png)

这张图是比较老的图。

![image-20220701103033935](NXP7架构师-Spring生态架构.assets/image-20220701103033935.png)



![image-20220701103251397](NXP7架构师-Spring生态架构.assets/image-20220701103251397.png)

上图是现在的：



![image-20220701103650794](NXP7架构师-Spring生态架构.assets/image-20220701103650794.png)

spring boot

![image-20220701103728125](NXP7架构师-Spring生态架构.assets/image-20220701103728125.png)



![image-20220701103818573](NXP7架构师-Spring生态架构.assets/image-20220701103818573.png)





## spring设计思想深入分析

![image-20220701111731260](NXP7架构师-Spring生态架构.assets/image-20220701111731260.png)

单纯的设计模式，其实没多大意思，主要是要将相应的思想运用到架构中去。



![image-20220701111957469](NXP7架构师-Spring生态架构.assets/image-20220701111957469.png)

![image-20220701115433618](NXP7架构师-Spring生态架构.assets/image-20220701115433618.png)

可以用如上的几个指导意义考虑单一原则。

![image-20220701115646654](NXP7架构师-Spring生态架构.assets/image-20220701115646654.png)



单一原则并不是拆的越细越好，

主要防止大而全的类，防止不想关的功能耦合在一起。

开闭原则

![image-20220701130135155](NXP7架构师-Spring生态架构.assets/image-20220701130135155.png)



![image-20220701130651119](NXP7架构师-Spring生态架构.assets/image-20220701130651119.png)



![image-20220701161430985](NXP7架构师-Spring生态架构.assets/image-20220701161430985.png)











## spring设计模式和核心功能深入剖析



![image-20220701140939412](NXP7架构师-Spring生态架构.assets/image-20220701140939412.png)



> 本质，是面向对象设计原则的实际运用，是对类的封装性、继承性和多态性以及类的关联关系和组合关系的充分理解



有GOF的23中，J2EE的，以及IOC的模式

现在大厂都在 ： DDD + 设计模式

复用 + 扩展性



### 工厂模式

![image-20220701154717663](NXP7架构师-Spring生态架构.assets/image-20220701154717663.png)

 	

![image-20220701155941778](NXP7架构师-Spring生态架构.assets/image-20220701155941778.png)



![image-20220701160003710](NXP7架构师-Spring生态架构.assets/image-20220701160003710.png)

上图是spring的工厂方法。

![image-20220701160101118](NXP7架构师-Spring生态架构.assets/image-20220701160101118.png)



![image-20220701160219995](NXP7架构师-Spring生态架构.assets/image-20220701160219995.png)





### 模板模式

![image-20220701165554755](NXP7架构师-Spring生态架构.assets/image-20220701165554755.png)



我们从spring的事务管理器看一下模板方式是怎么用的：

![image-20220701170059717](NXP7架构师-Spring生态架构.assets/image-20220701170059717.png)



![image-20220701170146711](NXP7架构师-Spring生态架构.assets/image-20220701170146711.png)



![image-20220701170212403](NXP7架构师-Spring生态架构.assets/image-20220701170212403.png)

模板方式是依赖倒置原则的最佳实践之一



![image-20220701171112985](NXP7架构师-Spring生态架构.assets/image-20220701171112985.png)

观察者模式

从架构上来说，比如zookeeper的watch机制，实际上就是观察者模式。

![image-20220701172632809](NXP7架构师-Spring生态架构.assets/image-20220701172632809.png)

![image-20220701172713343](NXP7架构师-Spring生态架构.assets/image-20220701172713343.png)



![image-20220701172757911](NXP7架构师-Spring生态架构.assets/image-20220701172757911.png)





![image-20220701173135659](NXP7架构师-Spring生态架构.assets/image-20220701173135659.png)



![image-20220701173405436](NXP7架构师-Spring生态架构.assets/image-20220701173405436.png)



其中DI，除了DI，还有依赖查找，都可以实现注入（实现）。

注意，从上到下，层次越低，比如DIP是最高的设计原则，然后才是理论，然后实现

![image-20220701173652825](NXP7架构师-Spring生态架构.assets/image-20220701173652825.png)

Ioc里面的架构涉及到了观察者模式，模板模式，反射 工长模式，如下图：



![image-20220701173732685](NXP7架构师-Spring生态架构.assets/image-20220701173732685.png)



![image-20220701174025835](NXP7架构师-Spring生态架构.assets/image-20220701174025835.png)

bean的创建流程

流程：实例化，属性注入，初始化。

![image-20220701195434569](NXP7架构师-Spring生态架构.assets/image-20220701195434569.png)



![image-20220701195510966](NXP7架构师-Spring生态架构.assets/image-20220701195510966.png)



![image-20220701195526512](NXP7架构师-Spring生态架构.assets/image-20220701195526512.png)


