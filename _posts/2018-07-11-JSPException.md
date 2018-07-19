---
layout: post
title: JSP中的HttpServlet异常
date: 2018-07-11
categories: exception
tags: [jsp, httpservlet]
description: The superclass "javax.servlet.http.HttpServlet" was not found on the Java Build Path
---

***JavaWeb: 报错信息The superclass "javax.servlet.http.HttpServlet" was not found on the Java Build Path***

解决方法：
1.项目右键Build Path --> Configure BuildPath... --> Java Build Path --> Libraries --> Add Library... 
    --> Server Runtime --> Server Library
  如果Server Library下没有Tomcat服务器，则先执行步骤2添加Tomcat，再重新执行步骤1
  
2.添加Tomcat：  
    window --> Preferences --> Server --> Runtime Environments --> Add... --> New Runtime Server Environment  
     --> Apache --> Apache Tomcat v9.0 
       