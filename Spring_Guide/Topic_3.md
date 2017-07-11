### Topic_3: Beans BeanFactor 和 ApplicationContext

    org.springframework.beans
    org.springframework.context
    
    
> BeanFactory 提供一种先进的配置机制来管理任何种类bean(对象), ApplicationContext 建立在BeanFactory之上,并增加了其他的功能，
    比如更容易同Spring AOP特性整合，消息资源处理(用于国际化)，时间传递， 以声明的方式创建ApplicationContext,可选的父上下文和与
    应用层相关的上下文(比如WebApplicationContext)
    
  ---------------------------------------------
  #### 3.1 BeanFactory 和BeanDefinitions基础
  
  BeanFactory 实际上是实例化，配置和管理众多bean的容器。bean彼此合作，之间互相产生依赖。
  (ApplicationContext是BeanFactory的子类-->ApplicationContext的Xml)
  * 表示方式：org.springframework.beans.factory.BeanFactory(接口)
  
  * 实现之一：org.springframework.beans.factory.xml.XmlBeanFactory
  
  
  > javeBean(仅包含一个默认的(无参数的)构造函数,在属性后面定义想对应的setter和getter方法)
  
#### 3.2 创建Bean方式
* 通过构造函数创建bean
```
<bean id="exampleBean" class="examples.ExampleBean"/>
<bean name="anotherExample" class="examples.ExampleBeanTwo"/>
```
* 通过静态工厂方法构建Bean
 ```
 <bean id="exampleBean" class="examples.ExampleBean2" factory-method="createInstance">
 ```
 * 通过实例工厂方法创建bean()
 ```
 <bean id="myFactoryBean" class="">
 <bean id="exampleBean" factory-bean="myFactoryBean" factory-method="createInstance">
 ```
 #### 3.3 Singleton的使用与否
  Bean被定义为两种部署模式中的一种: singleton或prototype
  ```
  <bean id="examples.ExampleBean" singleton="false">
  <bean name="yetAnotherExample" class="example.ExampleBeanTwo" singleton="true">
  ```
 
  #### 设置bean的属性与和合作者
 
 > 反向控制通常与依赖注同时提及，bean通过`构造函数的参数`和`工厂方法的参数`两种方式来定义它们的依赖，
 当对象实例被构造出来或从一个工厂方法返回后设置在某个实例上的属性。
 
 反向控制/依赖注入崔仔两种主要的形式:
 
 * 基于setter的依赖注入：通过调用bean的setter方法实现
 *基于构造函数的依赖注入：通过调用带有很多参数的构造方法实现
 

 > 目前对于控制反转(反向控制)和依赖注入的理解：
   * 控制反转(反向控制)：通过构建容器，然后通过容器创建bean，与一般的bean实例化方式相反，所以称为反向控制。
   * 依赖注入：通过对象类的构造函数参数或者setter函数参数的方式将另一个类实例以参数的形式将另一个类与当前类关联起来。
 
 
 
 
 
 
 
 [静态工厂方法](http://www.cnblogs.com/sluggard/p/4343426.html)
  
 -[标题](#topic)
 
 -[context](#context)
 
 <h3 id="topic" align="center" lang="fr">标题</h3>
 <h1 id="context" align="center" title="true">context</h3>
  <h1 id="context" align="center" title="true" lang="fr">context</h3>
