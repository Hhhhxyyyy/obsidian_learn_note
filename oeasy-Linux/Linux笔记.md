# Linux

## lesson 1 内核 uname

学习使用命令行操作  Linux

连接服务器的 ssh 时都要使用命令行

进入终端，查看 Linux 内核

有命令 `uname -r`

利用 `unmae --help` 查看该命令全部功能

```
uname
用法

	-a, --all 以如下次序输出所有信息，其中若 -p 和 -i 的探测结果不可知则省略

	-s, --kernel-name 输出内核名称
	-n, --nodename 输出网络节点上的主机名
	-r, --kernel-release 输出内核发行号
	-v, --kernel-version 输出内核版本号
	-m, --machine 输出机器硬件（CPU）名
	-p, --processor 输出系统处理器的体系结构 or 省略
	-i, --hardware-platform 输出硬件平台名 or 省略
	-o, --operating-system 输出当前的操作系统
	    --help 显示此帮助信息并退出
	    --version 显示版本信息并退出
```

使用 `uname -a` 后 将会依次执行剩余的命令，显示内核的全部信息

## lesson 2~3 自由软件和开源

-   计算机本身的特性决定
    -   计算机保存传递的是电子
    -   而不是原子
    -   这就使得存储和分发的成本几乎为零
-   在这样的物理基础上
    -   出现了自由软件运动
    -   从rms提出的free software 开始
    -   到gnu研发的各种软件
-   自由软件运动之后出现了开源运动
    -   提倡把源代码开放
    -   也被大量的商业公司所跟随
-   github可以在全世界范围内进行协作
-   linux是5000个极客一起协作出来的内核

## lesson 4~5 Linux 发行版

发行版 distro 是内核和应用程序的集合

- 一个典型的 Linux 发行版包括
 - Linux内核
 - 一些 GNU 程序库和工具
 - 命令行 shell
 - 可选的图形界面

查看发行版可以访问 [distrowatch](https://distrowatch.com)

选择所需要的发行版可以访问 [Distrochooser](https://distrochooser.de/zh-cn/)，该网站可根据你的需求为你推荐合适的发行版

Linux 发行版主要有三大家族：

- Debian 家族 ubuntu、kali  
- Rhel 家族 Red hat enterprise linux : Centos、Fedora、Mandriva  
- Suse 家族 openSUSE

如何查找当前系统的发行版：

借助命令 `ls` , `list`

`ls /etc/*release`

```
命令解释
`/ `是整个文件的根目录（root）下
`/etc` 是根下的 etc 文件夹下
`/etc/*release` 是根下的 etc 文件夹下的所有以 release 结尾的文件
```

之后会显示该目录下的所有发行版文件
教程所使用的系统有如下两个发行版 
-   /etc/lsb-release
    -   Linux Standard Base
-   /etc/os-release
    -   Operating System

如何查看当前这两个发行版

利用命令 `cat`， `concatenate`

`cat /etc/*release`

可以查看这两个发行版的具体信息

## lesson 6 我在哪  pwd
### 正文

`cd`, `change directory` 跳转命令

可以跳转到参数指定的目录下，如 `cd /etc/` 就跳转到了根目录下的 etc 文件夹内

`pwd`, `print working directory` 输出当前文件夹/当前工作目录

```
cd /boot 
ls
pwd
```

我们进入根目录下的 /boot 文件夹

> Linux系统在本地启动时，目录 /boot 非常重要，其中的文件和目录有
> （1）系统Kernel的配置文件；
> （2）启动管理程序GRUB的目录，里面存放的都是GRUB在启动时所需要的画面、配置及各阶段（stage1, stage1.5, stage 2）的文件。
> （3）Initrd文件，是系统启动时的模块供应的主要来源
> （4）System.map文件时系统Kernel中的变量对应表
> （5）vmlinuz是在启动过程中最重要的一个文件，因为这个文件就是实际系统所使用的kernel。

引导过程

>1.  关机状态中，内核和整个系统最开始在硬盘里
>2.  引导程序通过 cpu 把内核从硬盘的 /boot 目录加载到内存中
>3.  cpu 开始执行内存中的内核(kernel)对应的指令
>4.  内核(kernal)完成初始化
>5.  内核接管了系统资源（cpu、内存、外设）
>6.  操作系统完成启动过程
>7.  进入某个壳(shell)
>8.  等待下一步输入给壳的指令

shell：用户间接操作内核的界面，从而能控制硬件进行io读写

>zsh 
>bash

当 shell 上有命令要求运行某个程序时

>1.  分配内存
>2.  把该程序从硬盘加载到内存中
>3.  分配 cpu 资源去执行程序

如何查看内存：进入根目录下的 proc 文件夹

```
cd /proc
ls
cat meminfo
pwd
```

![](photo%20for%20Linux/L6-3.png)

proc 指的是 process 进程，该文件夹内同步了内存中的进程，蓝色数字表示对应ID的进程 

查看当前所有进程

`ps` Process Status 进程状态，显示执行命令时的进程快照

`ps -ef`

![](photo%20for%20Linux/L6-1.jpg)

`ps -ef` 后列出了所有的进程，分析该表的列名：

```
- UID 用户ID，输出用户名
- PID 进程ID
- PPID 父亲进程ID
- C 进程占用CPU的百分比
- STIME 进程启动刀现在的时间
- TTY 该进程在哪个终端运行（若无关则显示？，若为pts/0等，则表示由网络连接主机进程）
- CMD 命令的名称和参数
```

`ps aux`

![](photo%20for%20Linux/L6-2.png)

`ps aux` 同样列出了所有的进程，但显示内容和侧重与 `ps -ef` 的不同，分析该表的列名：

```
- USER 用户名
- PID 进程ID
- %CPU CPU百分比
- %MEM 内存占用百分比
- VSZ 该进程使用的虚拟内存量（KB）
- RSS 该进程占用的固定内存量（KB）（驻留中页的数量）
- TTY 该进程在哪个终端运行
- STAT 进程的状态
- START 该进程被触发启动的时间
- TIME 该进程的CPU使用时间
- COMMAND 命令的名称
```

STAT 为进程状态

常见的几个状态缩写

- S  休眠状态
- R  正在运行的或在队列中待运行
- s  进程的领导者（有子进程）
- l  多线程、克隆线程
- N  优先级较低的进程
- <  优先级较高的进程
- L  部分页被锁进内存
- Z  僵尸进程
- +  位于后台的进程组


![](photo%20for%20Linux/L6-3.png)

### 总结

路径操作

- `cd`, `change directory` 跳转命令
- `pwd`, `print working directory` 输出当前文件夹/当前工作目录

进程文件夹 /proc

查看进程

- `ps -ef`
- `ps aux`

**预告**：/proc 中的

- version
- dmazoneinfo
- cpuinfo

## lesson 7 灵魂之问 whatis

### 正文

/proc 中的

- version
- dmazoneinfo
- cpuinfo

可以利用 `cat` 命令查看，命令 `cat` 可以将里边的内容输出到标准输出流

```
cd /proc
ls
cat cpuinfo
```

![](photo%20for%20Linux/L7-1.png)


如何查看所有命令呢

`bash` 切换到 bash 状态，连续按两下 `tab`，选择 yes，就可以看到所有的命令总量，大概条数在1900+，后可按 `ctrl + c` 退出，`zsh` 切换回 zsh 状态

![](photo%20for%20Linux/L7-2.png)

新命令：`whatis` 可以查看其他命令的作用

`whatis` + 命令名

```
whatis pwd
whatis cat
whatis whatis
```

![](photo%20for%20Linux/L7-3.png)

### 总结

`cat` 连结文件，将内容输出为标准输出流
`whatis` 查看命令作用

## lesson 8 详查手册 man

### 正文

`whatis` 只能简单查看命令介绍，命令的细节通过 `man` 来查看

`man` manual 查询手册

`man` + 命令名称，查看时 `h` help 能查看本说明的帮助，`q` quit 可以退出，`⬆️` 向上, `⬇️` 向下

![](photo%20for%20Linux/L8-1.png)

可以使用 `/` 进行搜索

![](photo%20for%20Linux/L8-2.png)

查看 `cat` 的手册

`man cat`

![](photo%20for%20Linux/L8-3.png)

`man` 命令共有三种翻页方式

- `⬆️` 向上, `⬇️` 向下；
- `k` 向上, `j` 向下； 与 vim 一致
- `ctrl`+`f` 向下 forward 一页；`ctrl`+`b` 向上 backward 一页

对于大部分命令来说在执行时

**命令 = 命令 + 选项 + 参数**

### 总结

`man` 查询手册

三种翻页方式

- `⬆️` 向上, `⬇️` 向下；
- `k` 向上, `j` 向下； 与 vim 一致
- `ctrl`+`f` 向下 forward 一页；`ctrl`+`b` 向上 backward 一页

手册内搜索使用  `/`

**命令 = 命令 + 选项 + 参数**

## lesson 9 此处有啥 ls

### 正文



### 总结