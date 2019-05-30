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

![webdriver-er](/img/webdriver-er.png)

如图所示，在执行webdriver-manager update时，由于无法访问到相应地址，而导致失败。国内存在相应的镜像，但是webdriver-manager update的逻辑是先查询对应地址获得版本信息，基于本机的版本，自动选择安装包，而国内的镜像网站无法同原地址一样以xml格式提供对应的版本信息。因而我将需要安装的包以及版本信息文件上传至github上提供静态资源的访问。而相关地址的配置位置在工程路径下node_modules\protractor\node_modules\webdriver-manager\built\config.json(可能存在不同情况，在node_modules目录下搜索webdriver-manager即可)。

修改下图标注位置即可（win10用户可直接使用我提供的路径）

![config-webdriver](/img/config-webdriver.png)



## （三）npm test 无法通过的问题







## （四）mvn 启动出现elasticsearch path.home 未配置的问题

