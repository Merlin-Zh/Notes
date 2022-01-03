Spring Ioc

[toc]

# 一、Spring IoC基础

我们之前在自定义IOC容器中，通过BeanFactory的方式来实现了这个容器，在Spring中同样有这么一个`BeanFactory`，它也就是Spring中的IOC容器实现了。

在我们自定义的项目中，我们是通过`beans.xml`文件去配置类与类之间的依赖关系的，从而实现的依赖注入。在Spring中，不光有纯xml的方式来进行配置，还提供了纯注解、xml+注解的方式来让我们选择。

- 纯xml：bean信息全部定义在xml配置文件中
- 纯注解：所有的bean都由注解定义
- xml + 注解：部分bean由xml定义，部分bean使用注解定义

不同的bean定义方式，导致了`BeanFactory`也有不同的启动方式。

- 对于纯xml和xml + 注解的定义方式，容器的启动方式为：

  - javaSE应用

    ```java 
    ApplicationContext applicationContext = new ClassPathXmlApplicationContext("beans.xml");
    ```

    或

    ```java
  ApplicationContext applicationContext = new FileSystemXmlApplicationContext("file_path/beans.xml");
    ```

  - javaWeb应用：ContextLoaderListener监听器去加载xml

* 对于纯注解定义方式：

  * javaSe应用：

    ```java
    ApplicationContext applicationContext = new AnnotationConfigApplicationContext(SpringConfig.class);
    ```

  * javaWeb应用：ContextLoaderListener监听器去加载注解配置类

``` ```

## 1、BeanFactory和ApplicationContext的区别

BeanFactory是Spring框架中IoC容器的顶层接口，它只是⽤来定义⼀些基础功能，定义⼀些基础规范，⽽ApplicationContext是它的⼀个⼦接⼝，所以ApplicationContext是具备BeanFactory提供的全部功能的。

通常，我们称BeanFactory为SpringIOC的基础容器，ApplicationContext是容器的⾼级接⼝，⽐BeanFactory要拥有更多的功能，⽐如说国际化⽀持和资源访问（xml，java配置类）等等。
