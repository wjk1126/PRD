# inode
![](https://gss3.bdstatic.com/-Po3dSag_xI4khGkpoWK1HF6hhy/baike/w%3D268%3Bg%3D0/sign=b07c9b7a43a98226b8c12c21b2b9de3c/9a504fc2d5628535be65cb2e90ef76c6a7ef6333.jpg)
表中包含文件系统所有文件列表
包含除了文件名之外的所有文件信息，文件名在目录中
inode包含文件的元信息
括：  
文件的字节数  
文件的拥有者uid  
文件的所属组gid  
文件的r、w、x权限  
文件的时间戳 

```
[root@centos7 ~]#ls -i
100663421 ！               100664845 filea
100663363 anaconda-ks.cfg  100663367 initial-setup-ks.cfg
100663390 Desktop            1552155 Music
100663391 Documents         34877112 Pictures
  1552154 Downloads         68506236 Public
100664855 f1                34877111 Templates
100663417 file              68506237 Videos
```
inode也会消耗硬盘空间，所以硬盘格式化的时候，操作系统自动将硬盘分成两个区域。一个是数据区，存放文件数据；另一个是inode区（inode table），存放inode所包含的信息。   
每个inode都有一个号码，操作系统用inode号码来识别文件。对于系统来说，文件名只是inode号码便于识别的别称或绰号
# 硬链接
指针对一个文件给他起多个名称  
创建硬链接会增加额外的记录项以引用文件  
对应于同一文件系统上一个物理文件  
每个目录引用相同的inode号   创建时链接数递增  
语法：

```
ln filename [linkname ]
```

```
[root@centos7 date]#ll
total 0
-rw-r--r--. 1 root root 0 Sep 24 19:46 f1
[root@centos7 date]#ln f1 f11 
[root@centos7 date]#ll
total 0
-rw-r--r--. 2 root root 0 Sep 24 19:46 f1
-rw-r--r--. 2 root root 0 Sep 24 19:46 f11
```

不能跨越驱动器或分区  
即使删除 f1 但f11仍然能访问 本质上只是删个名字而已 硬链接不能跨分区创建
不能针对目录来实现 
# 软连接
文件A和文件B的inode号码虽然不一样，但是文件A的内容是文件B的路径。读取文件A时，系统会自动将访问者导向文件B。因此，无论打开哪一个文件，最终读取的都是文件B。这时，文件A就称为文件B的“软链接”（soft link）或者“符号链接”（symbolic link）
[root@centos7 date]#ll
total 0
-rw-r--r--. 2 root root 0 Sep 24 19:46 f1
-rw-r--r--. 2 root root 0 Sep 24 19:46 f11

```
[root@centos7 date]#ln -s f1 f1-link
[root@centos7 date]#ll
total 0
-rw-r--r--. 2 root root 0 Sep 24 19:46 f1
-rw-r--r--. 2 root root 0 Sep 24 19:46 f11
lrwxrwxrwx. 1 root root 2 Sep 24 20:19 f1-link -> f1
[root@centos7 date]#
[root@centos7 date]#rm f1
rm: remove regular empty file ‘f1’? y
[root@centos7 date]#ll
total 0
-rw-r--r--. 1 root root 0 Sep 24 19:46 f11
lrwxrwxrwx. 1 root root 2 Sep 24 20:19 *f1-link -> f1*（不存在了）
 [root@centos7 date]#ln -s dir1 dir1-link
[root@centos7 date]#ll
total 4
drwxr-xr-x. 2 root root   6 Sep 24 20:22 dir1
lrwxrwxrwx. 1 root root   4 Sep 24 20:22 dir1-link -> dir
```
这意味着，文件A依赖于文件B而存在，如果删除了文件B，打开文件A就会报错：“No such file or directory”。这是软链接与硬链接最大的不同。文件A指向文件B的文件名，而不是文件B的inode号码，文件B的inode链接数不会因此而发生改变。
#### 硬链接和软链接的区别

```
1，	同一个文件？
2，	跨分区？
3，	链接数增长？
4，	Inode Number 是否相同？
5，	原文件删除，链接文件可否访问？
6，	大小？
7，	支持目录？
8，	相对路径？
```

![](http://s5.51cto.com/wyfs02/M01/86/D6/wKioL1fM4ingnT0zAAA8aKAQ89M007.png)
![](http://www.th7.cn/d/file/p/2014/04/30/89a90988cbf77b824bbb26c076dae3bc.jpg)
