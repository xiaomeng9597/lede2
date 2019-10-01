中文：如何编译自己需要的 OpenWrt 固件
___
*** 不要fork我这个repo，此repo不会实时更新Lean大的，很有可能会缺少新功能或者留有未修复的BUG。***
*** 以下命令可以作为你搭建环境和编译的参考***
___
注意：
1. 不要用 root 用户 git 和编译！！！
2. 国内用户编译前最好准备好梯子
3. 默认登陆IP 192.168.5.1, 没有密码，早期固件请尝试 password

** 欢迎关注油管频道 “eSir playground” 观看相关的教学视频 **
** 频道地址：https://www.youtube.com/c/esirplayground **

编译命令如下:

1. 首先装好 Ubuntu 64bit，推荐  Ubuntu  14 LTS x64

2. 命令行输入 sudo apt-get update ，然后输入
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev patch unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex node-uglify gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx-ucl libelf-dev autoconf automake libtool autopoint

从此时开始，你必须使用非root权限用户进行后续操作
3. git clone https://github.com/coolsnowwolf/lede 下载好源代码，然后 
   
   cd lede 进入目录

4. ./scripts/feeds update -a 
   ./scripts/feeds install -a
   
5.   make menuconfig 选择cpu架构，型号，固件类型，所需插件及工具等等等等

6.   make download 下载源码文件到buildroot目录下的dl目录

7.   make V=s

7-1. 如果你非常谨慎，也可以使用以下命令替换第7步的命令，来编译你的固件。

     make -j1 V=s （-j1 后面是线程数。第一次编译推荐用单线程，国内请尽量全局科学上网）

本套代码保证肯定可以编译成功。里面包括了 R9 所有源代码，包括 IPK 的。

你可以自由使用，但源码编译二次发布请注明我的 GitHub 仓库链接。谢谢合作！

特别提示：
1. 源代码中绝不含任何后门和可以监控或者劫持你的 HTTPS 的闭源软件，SSL 安全是互联网最后的壁垒。安全干净才是固件应该做到的。
2.如果你自认为 Koolshare 论坛或者其固件的脑残粉，本人不欢迎你使用本源代码。所以如果你是，那么使用过程中遇到任何问题本人概不回应。
3.如有问题需要讨论，欢迎加入 QQ 讨论群：Gargoyle OpenWrt 编译大群 ,号码 718010658 ，加群链接 点击链接加入群聊【Op共享技术交流群】：https://jq.qq.com/?_wv=1027&k=5PUGjOG

Before going to the next step，welcome subscribe youtube channel “佚sir playground” to obtain related video tutorials and more.

You need to have installed gcc, binutils, bzip2, flex, python, perl, make,
find, grep, diff, unzip, gawk, getopt, subversion, libz-dev and libc headers.

Run "./scripts/feeds update -a" to get all the latest package definitions
defined in feeds.conf / feeds.conf.default respectively
and "./scripts/feeds install -a" to install symlinks of all of them into
package/feeds/.

Please use "make menuconfig" to choose your preferred configuration for the toolchain and firmware.

And then run "make download" to download source code to buildroot dl dir.

At last Simply run the command "make V=s" to build your firmware.

It will build the cross-compile toolchain, the kernel and all choosen applications.

To build your own firmware you need to have access to a Linux, BSD or MacOSX system
(case-sensitive filesystem required). Cygwin will not be supported because of
the lack of case sensitiveness in the file system.



Note: Addition Lean's private package source code in ./package/lean directory. Use it under GPL v3.

GPLv3 is compatible with more licenses than GPLv2: 
it allows you to make combinations with code that has specific kinds of additional requirements that are not in GPLv3 itself. 
Section 7 has more information about this, including the list of additional requirements that are permitted.
