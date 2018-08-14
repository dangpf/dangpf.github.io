---
title: ubuntu启用root用户-设置root密码
categories: linux
tags:
  - linux
translate_title: ubuntu-enable-root-user---set-root-password
date: 2018-08-13 14:26:08
---
### 一、启用root
设置root允许ssh登录
        
    vim /etc/ssh/sshd_config
    
修改项：**PermitRootLogin yes**

### 二、设置root密码

安装完Ubuntu后默认是没有主动设置root密码的，也就无法进入根用户。
1. 用当前登录用户打开终端，在终端输入命令 sudo passwd，输入当前用户的密码然后回车
2. 会提示输入新密码，输入完成后回车
3. 然后提示再输入一次新密码以确认，然后回车，设置成功
```
linuxidc@ubuntu:~$ sudo passwd
[sudo] password for linuxidc: 
输入新的 UNIX 密码： 
重新输入新的 UNIX 密码： 
passwd：已成功更新密码
linuxidc@ubuntu:~$
注意：这个新密码就是root的密码，可以与当前用户的密码不同。
```
在终端中输入 su root，然后输入root的密码，验证成功即可切换到root用户。在root用户下做完操作后，用exit命令即可退出root用户，退回当前登陆用户。
