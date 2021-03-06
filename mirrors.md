---
title: Linux镜像与软件源
date: '2017-05-18 23:12:29'
categories: []
layout: post
author: Yongxin Shi
description: linux的软件源机制就如同软件商店一样的存在，可以从软件源里安装软件。不同发行版的软件源都是不同的
slug: mirrors
tags: []
draft: false
---

Linux镜像与软件源
==========

### 软件源
linux的软件源机制就如同软件商店一样的存在，可以从软件源里安装软件。不同发行版的软件源都是不同的

### 镜像
大多数发行版的的服务器都在国外，在加上GWF的关系，所以在中国的访问速度感人。国内一些流量比较大的机构就会自己建立镜像站（一般都是学校和互联网巨头），来加速访问。linux发行版镜像站的所属都不同。所以无法自己切换镜像。所以一般都手动切换镜像（换源）


### 以Ubuntu为例
一般情况下，将 /etc/apt/sources.list 文件中 Ubuntu 默认的源地址 http://archive.ubuntu.com/ 替换为 http://mirrors.ustc.edu.cn 即可。

也可以使用如下命令：

    sudo sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' \
    /etc/apt/sources.list

当然也可以直接编辑 /etc/apt/sources.list 文件（需要使用 sudo）。以下是 Ubuntu 16.04 参考配置内容：

    deb https://mirrors.ustc.edu.cn/ubuntu/ xenial main restricted universe multiverse
    deb https://mirrors.ustc.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
    deb https://mirrors.ustc.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
    deb https://mirrors.ustc.edu.cn/ubuntu/ xenial-security main restricted universe multiverse

或者

    cat > /etc/apt/sources.list << "EOF"
    deb https://mirrors.ustc.edu.cn/ubuntu/ xenial main restricted universe multiverse
    deb https://mirrors.ustc.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
    deb https://mirrors.ustc.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
    deb https://mirrors.ustc.edu.cn/ubuntu/ xenial-security main restricted universe multiverse
    EOF

### 关于debian 版本
debian 默认是稳定版。源里写着的是版本代号。现在 stable = stretch 系统

默认是stable， 作为桌面用户完全可以用unstable

stable 稳定，但包陈旧。适合服务器用

升级顺序：

oldstable → stable → testing → unstable → experimental

请不要使用`experimental`，除非你对dpkg 足够了解


## 国内的一些知名开源镜像站

中国科学技术大学
http://mirrors.ustc.edu.cn/

清华大学 TUNA 协会
https://mirrors.tuna.tsinghua.edu.cn/

欢迎访问网易开源镜像站
http://mirrors.163.com/

Alibaba Open Source Mirror Site（阿里云）
http://mirrors.aliyun.com/
