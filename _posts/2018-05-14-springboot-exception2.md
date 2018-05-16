---
layout: post
title:[ springboot启动报错 java.lang.IllegalStateException: Failed to introspect annotated methods on class org ]
date: 2018-05-14
categories: blog
tags: [IllegalStateException, startup]
description: springboot启动异常处理
---

idea启动springboot +maven项目报错： 
  
[ INFO ] [2017-11-03 14:50:17:017] com.taikang.Application [48] [main]- Starting Application on WMM with PID 4384 (started by Administrator in G:\workspace-s\IdeaProjects\hello)  
[ INFO ] [2017-11-03 14:50:17:017] com.taikang.Application [665] [main]- The following profiles are active: DEV  
[ INFO ] [2017-11-03 14:50:17:017] org.hibernate.validator.internal.util.Version [30] [background-preinit]- HV000001: Hibernate Validator 5.2.4.Final  
[ INFO ] [2017-11-03 14:50:18:018] org.springframework.context.annotation.AnnotationConfigApplicationContext [581] [main]- Refreshing org.springframework.context.annotation.AnnotationConfigApplicationContext@bdd8f7: startup date [Fri Nov 03 14:50:18 CST 2017]; root of context hierarchy  
[ WARN ] [2017-11-03 14:50:18:018] org.springframework.context.annotation.AnnotationConfigApplicationContext [549] [main]- Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.BeanDefinitionStoreException: Failed to parse configuration class [com.taikang.Application]; nested exception is java.lang.IllegalStateException: Failed to introspect annotated methods on class org.springframework.boot.web.support.SpringBootServletInitializer  
Disconnected from the target VM, address: '127.0.0.1:60450', transport: 'socket'  
[ ERROR] [2017-11-03 14:50:18:018] org.springframework.boot.SpringApplication [839] [main]- Application startup failed  
org.springframework.beans.factory.BeanDefinitionStoreException: Failed to parse configuration class [com.taikang.Application]; nested exception is java.lang.IllegalStateException: Failed to introspect annotated methods on class org.springframework.boot.web.support.SpringBootServletInitializer  
    at org.springframework.context.annotation.ConfigurationClassParser.parse(ConfigurationClassParser.java:187)  
    at org.springframework.context.annotation.ConfigurationClassPostProcessor.processConfigBeanDefinitions(ConfigurationClassPostProcessor.java:324)  
    at org.springframework.context.annotation.ConfigurationClassPostProcessor.postProcessBeanDefinitionRegistry(ConfigurationClassPostProcessor.java:246)  
    at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanDefinitionRegistryPostProcessors(PostProcessorRegistrationDelegate.java:273)  
    at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanFactoryPostProcessors(PostProcessorRegistrationDelegate.java:98)  
    at org.springframework.context.support.AbstractApplicationContext.invokeBeanFactoryPostProcessors(AbstractApplicationContext.java:681)  
    at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:523)  
    at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:761)  
    at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:371)  
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:315)  
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:1186)  
    at org.springframework.boot.SpringApplication.run(SpringApplication.java:1175)  
    at com.taikang.Application.main(Application.java:36)  
Caused by: java.lang.IllegalStateException: Failed to introspect annotated methods on class org.springframework.boot.web.support.SpringBootServletInitializer  
    at org.springframework.core.type.StandardAnnotationMetadata.getAnnotatedMethods(StandardAnnotationMetadata.java:163)  
    at org.springframework.context.annotation.ConfigurationClassParser.doProcessConfigurationClass(ConfigurationClassParser.java:301)  
    at org.springframework.context.annotation.ConfigurationClassParser.processConfigurationClass(ConfigurationClassParser.java:237)  
    at org.springframework.context.annotation.ConfigurationClassParser.parse(ConfigurationClassParser.java:204)  
    at org.springframework.context.annotation.ConfigurationClassParser.parse(ConfigurationClassParser.java:173)  
    ... 12 common frames omitted  
Caused by: java.lang.NoClassDefFoundError: javax/servlet/ServletContext  
    at java.lang.Class.getDeclaredMethods0(Native Method)  
    at java.lang.Class.privateGetDeclaredMethods(Class.java:2615)  
    at java.lang.Class.getDeclaredMethods(Class.java:1860)  
    at org.springframework.core.type.StandardAnnotationMetadata.getAnnotatedMethods(StandardAnnotationMetadata.java:152)  
    ... 16 common frames omitted  
Caused by: java.lang.ClassNotFoundException: javax.servlet.ServletContext  
    at java.net.URLClassLoader$1.run(URLClassLoader.java:366)  
    at java.net.URLClassLoader$1.run(URLClassLoader.java:355)  
    at java.security.AccessController.doPrivileged(Native Method)  
    at java.net.URLClassLoader.findClass(URLClassLoader.java:354)  
    at java.lang.ClassLoader.loadClass(ClassLoader.java:425)  
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:308)  
    at java.lang.ClassLoader.loadClass(ClassLoader.java:358)  
    ... 20 common frames omitted  
  
Process finished with exit code 1  

解决办法：
点此参考地址打开连接：https://stackoverflow.com/questions/37938289/spring-boot-java-lang-classnotfoundexception-javax-servlet-servletcontext-and


pom.xml中的

In maven, I changed the scope like this: <scope>provided</scope> to <scope>compile</scope> and it worked!!.