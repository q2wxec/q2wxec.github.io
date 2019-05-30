---
layout:     post
title:      "Jhipster系列-01,CookBook案例环境初始化踩坑指南"
subtitle:   "Jhipster系列,CookBook案例,环境初始化, 踩坑指南"
date:       2019-05-20
author:     "fxx"
header-img: "img/jhipster-head.png"
tags:
    - Java
    - Jhipster
    - CookBook
---



# Jhipster系列-01,CookBook案例环境初始化踩坑指南

## （一） 本文参考书籍

​	本文初始化Jhipster工程基于[JHipster-mini-book-v5.pdf](<https://q2wxec.github.io/JHipster-mini-book-v5.pdf>)  Part-One  Building an app with JHipster，相关工程代码生成请参照书中内容实现，本处不再赘述，仅对本人初始化环境过程中遇到的相关问题及解决方案进行记录与说明。

​	本文相关代码实现详见[Jhipster-cookbook-v5](<https://github.com/q2wxec/Jhipster-cookbook-v5-study>) 。

## （二）webdriver-manager 无法upadte的问题

​	由于众所周知的google服务访问的原因，在工程前端执行包安装过程中，在执行webdriver-manager update，命令时，由于无法访问google服务下载chorme的相关驱动，将导致后续进行e2e测试的失败。具体

失败信息如下图所示。

![webdriver-er](img/webdriver-er.png)





## （三）npm test 无法通过的问题







## （四）mvn 启动出现elasticsearch path.home 未配置的问题

