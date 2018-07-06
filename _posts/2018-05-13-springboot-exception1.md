---
layout: post
title: springboot访问异常
date: 2018-05-13
categories: blog
tags: [springboot访问异常, springboot]
description: springboot访问异常处理Spring Boot报错：This application has no explicit mapping ... a fallback
---
启动spring boot然后访问页面的时候，出现如下错误。  

Whitelabel Error Page


This application has no explicit mapping for /error, so you are seeing this as a fallback.
Mon Jul 06 21:57:13 CST 2015
There was an unexpected error (type=Not Found, status=404).
No message available



找了一晚上，居然发现是某个配置出错了！

spring.mvc.view.prefix: /WEB-INF/jsp/
spring.mvc.view.suffix: .jsp应该改为

spring.view.prefix=/WEB-INF/jsp/
spring.view.suffix=.jsp。

这充分体现了spring的默认大于配置理念