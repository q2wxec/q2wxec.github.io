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

​	由于众所周知的google服务访问的原因，在工程前端执行包安装过程中，在执行**webdriver-manager update**，命令时，由于无法访问google服务下载chorme的相关驱动，将导致后续进行**e2e**测试的失败。具体

失败信息如下图所示。

![webdriver-er](/img/webdriver-er.png)

如图所示，在执行**webdriver-manager update**时，由于无法访问到相应地址，而导致失败。国内存在相应的镜像，但是webdriver-manager update的逻辑是先查询对应地址获得版本信息，基于本机的版本，自动选择安装包，而国内的镜像网站无法同原地址一样以xml格式提供对应的版本信息。因而我将需要安装的包以及版本信息文件上传至github上提供静态资源的访问。而相关地址的配置位置在工程路径下**node_modules\protractor\node_modules\webdriver-manager\built\config.json**(可能存在不同情况，在node_modules目录下搜索webdriver-manager即可)。

修改下图标注位置即可（**win10用户可直接使用我提供的路径**）

![config-webdriver](/img/config-webdriver.png)



## （三）npm test 无法通过的问题

​	由于初始化时，并未设置任何前端js的测试，因而执行 **mvn test -P prod**，进行测试时，执行到**npm test**命令时，将由于找不到任何测试而报错退出，如下图所示：

![npmtest-er](/img/npmtest-er.png)

规避这个问题，需要修改**package.json**文件，在**npm  test** 命令中加入 **--passWithNoTests** 配置参数，详见下图：

![pack-test-change](/img/pack-test-change.png)





## （四）mvn 启动出现elasticsearch path.home 未配置的问题

​		使用**mvn**命令直接启动整个项目，项目总是出现下图异常

​	![pack-test-change](/img/mvn-er.png)

​		可是，在**springboot**配置文件中**application-dev.yml**已经进行了相关变量的配置，经过分析，mvn启动了**springboot：run**命令，而对应的plugin必须配置相关的profile才会主动读取相关的配置，而不会通过**applicaition.yml**中**spring.profiles.active**实现自动配置。因而如下图在启动plugin中添加对应profile解决问题。

![mvn-solve](/img/mvn-solve.png)

