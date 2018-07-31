---
title: 断网环境下利用pip安装Python离线安装包
date: 2018-07-19 23:06:00
categories: python
tags:
  - pip
  - python
---
### 一、安装pip

#### 1、下载最新pip

新建packages文件夹放在目录中：/packages

从该[网站](http://www.lfd.uci.edu/~gohlke/pythonlibs/#pytz)提供的编译好的包下载最新版本：
- pip-8.1.2-py2.py3-none-any.whl
- wheel-0.29.0-py2.py3-none-any.whl

放在packages文件夹中,离线安装pip时，这两个包需要准备好。

还需要一个包：setuptools-36.4.0-py2.py3-none-any.whl


#### 2、安装下载好的pip

下载 [get-pip.py](https://bootstrap.pypa.io/get-pip.py) 文件

执行命令：

    python  get-pip.py--no-index--find-links=/root/packages

PS：如果你可以联网，那么安装pip就方便多了，直接执行python get-pip.py。

### 二、利用pip离线安装python包-方案

#### 1、在可以联网的开发机器上安装好需要的包

例如：

    pip  install  elasticsearch

#### 2、打包已安装的包

#查看安装的包

    pip  list

#生成requirements.txt(记录所有依赖包及其精确的版本号)

    pip freeze >requirements.txt

#下载对应的包

    pip install --download /root/packages -r requirements.txt

#### 3、离线情况安装打包好的包

将packages文件夹和requirement.txt拷贝至离线机器上目录下

执行命令：

    pip install --no-index--find-links=./packages -r requirements.txt
