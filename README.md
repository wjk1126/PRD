![link](https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1187890068,4006029206&fm=27&gp=0.jpg)
# linux 基础  

Linux的诞生
 Linux由芬兰赫尔辛基大学的Linus Torvalds创建1991年10月，Linux第
一个公开版0.02版发布
1994年3月，Linux 1.0
版发布Linus的标志是可爱的企鹅,取自芬兰的吉祥物

Linux 的五个重要支柱
>• UNIX操作系统  
• MINIX 操作系统  
• GNU 计划  
• POSIX 标准  
• Internet 网络  

**1**，学习Linux
首先需要安装一台虚拟机（Vmware）  
点开下面链接有Vmware的下载和安装过程  
[www.wjk.com](https://blog.csdn.net/liujiding/article/details/76252525)

**2**，虚拟机安装完毕之后创建一台新的虚拟机  
下面有Linux虚拟机的详细步骤  
[www.wjk.com](https://jingyan.baidu.com/article/3a2f7c2e3a853626afd6112f.html)

**3**，安装centos6或者centos7的过程中需要有相对应的iso 最好的选择就是在官方下载自己需要的版本，我们用的话就用DVD，下面有官方链接
[www.centos.org](https://www.centos.org/download/)


**4**，操作系统安装  
 centos6安装步骤 ，       [www.wjk.com](https://jingyan.baidu.com/article/acf728fd6bdba1f8e510a3f7.html)

  centos7安装步骤，  [www.wjk.com](https://jingyan.baidu.com/article/11c17a2cd091cdf446e39d9b.html)

操作系统安装完毕 

Linux系统分两种模式：图形化和命令行  
init 5 为图形化 init 3 为命令行  init 0 关机  init 6 重启

Linux用户分别为管理员用户和普通用户  
```
[root@centos6 ~]#id -u
0
当查出来结果为0 则此用户为管理员 不为0则为普通用户
```


## 一，命令
Windows：一切皆图形  
Linux：一切皆命令  
在Windows中全是图形化很少操作需要用命令解决所以这就是两种操作系统之间的差别  
在Linux操作系统中我们最熟悉的东西应该就是命令

命令的格式：
==COMMAND [OPTIONS...] [ARGUMENTS...]==  
命令+选项+参数  

```
[root@centos6 ~]#ls -l /date
total 16
drwx------. 2 root root 16384 Sep 19 19:58 lost+found

ls（命令） -l（选项）date（参数）

```
命令分为内部命令和外部命令  
当一个命令执行时在系统中查找顺序  
alias（别名） --- 内部 --- hash（缓存） ---$PATH（变量）

选项 分为短格式和长格式    
短格式 ：
```
-a  -b  -c  -d
```

长格式 ：
```
--all   --escape  --block-size=SIZE
```
参数大部分为文件

ctrl+c  ctrl+d 中止当前执行的命令

## 二，文件和目录
如同Windows中一样 Linux同样有文件和目录   
在Linux中文件和目录被组织成大树倒根状   
文件系统根目录用“/”表示 
路径分隔用 /
文件名称区分大小写  
文件名最长为255个字节

#### 1，文件系统结构

> /bin          基本命令库  
> /boot        静态文件和启动相关文件  内核  
> /dev          设备  
> /etc          系统配置  
> /lib            共享库  
> /media，/mnt    挂载点   
> /opt        第三方应用程序  
> /sbin       管理员 用的  
> /srv     数据  
> /tmp    临时数据  
> /usr   第二个分层  
> /var  可变数据 

**不同颜色的文件区分** 

> 蓝色   目录  
> 绿色  可执行程序  
> 红色  打包文件  
> 浅蓝色  链接文件  
> 灰色 其他文件  
> 粉色 sock文件  
> 浅黄色 管道文件  

du -sh /*  
du 查看每个目录大小  
lsblk 查看硬盘分区
#### 2，文件类型
-：普通文件  
d: 目录文件  
b: 块设备  
c: 字符设备  
l: 符号链接文件  
p: 管道文件pipe  
s: 套接字文件socket  

**绝对和相对路径**  
 *绝对路径*：  
以正斜杠开始  
完整的文件的位置路径  
可用于任何想指定一个文件名的时候

*相对路径名* ：   
不以斜线开始
指定相对于当前工作目录或某目录的位置  
可以作为一个简短的形式指定一个文件名
![link](https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=2363709519,411122135&fm=200&gp=0.jpg)
