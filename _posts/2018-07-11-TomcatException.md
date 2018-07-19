---
layout: post
title: Tomcat启动报错Multiple Contexts have a path of "/servelet"
date: 2018-07-11
categories: exception
tags: [tomcat, 启动报错]
description: The superclass "javax.servlet.http.HttpServlet" was not found on the Java Build Path
---

***tomcat启动报错：Could not publish server configuration for Tomcat v9.0 Server at localhost.   
Multiple Contexts have a path of "/servelet"***

解决方法：
1. 删除server下Tomcat中的server.xml文件中末尾重复多余的\<Context>设置  

2. 删除server，重新创建一个：new --> Server
       