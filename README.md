Sublime-Text-CnIM
=================

在ubuntu 14.04 64位中实测可用。
fcitx输入法可以选择搜狗或者小企鹅。

###下载
```Shell
    git clone https://github.com/courseraRunsheng/Sublime-Text-CnIM.git
```
###使用Sublime Text 3官方.deb安装包安装的：
- 默认安装目录: /opt/sublime_text
- 将编译好的sub-fcitx-cn.so文件复制到安装目录之下，然后使用 subl命令挂载该文件启动sublime即可
- 简单命令如下
```Shell
    cd Sublime-Text-CnIM
    sudo cp -r usr /
    sudo cp -r opt /
```
----------
###其他方式安装的，需要自行编译文件：

安装编译环境
```Shell
    sudo apt-get install build-essential
    sudo apt-get install libgtk2.0-dev
```
进入`sub-fcitx.c`所在目录，执行下面命令编译成共享库
```Shell
    gcc -shared -o sub-fcitx-cn.so sub-fcitx.c  `pkg-config --libs --cflags gtk+-2.0` -fPIC
```
使用下面命令启动Sublime Text 3，测试能否切换并输入中文
```Shell
    LD_PRELOAD=./sub-fcitx-cn.so subl
```
`subl`为Sublime Text 3默认启动命令

如果你不是使用该命令，请将`subl`改为你自己的Sublime Text启动命令

**如果上面的命令启动后能输入中文**

复制`sub-fcitx-cn.so`到Sublime Text所在目录
```Shell
    sudo cp sub-fcitx-cn.so /opt/sublime_text/sub-fcitx-cn.so
```
编辑Sublime Text启动命令
```Shell
    sudo gedit /usr/bin/subl
```
在`#!/bin/sh`下面添加一行
```Shell
    export LD_PRELOAD=/opt/sublime_text/sub-fcitx-cn.so
```
在终端执行`subl`启动Sublime Text 3

###Enjoy～
