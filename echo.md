# echo
**作用**：显示字符  
**语法**：echo [-neE][字符串]  
echo 可以单纯读发量的内容，利用 echo读出变量，另需要在发量名称前面加上$，或者是以$（变量）的方式用都可以  
启用命令选项-e，若字符串中出现以下字符，则特别加以处理，而不会将它当成一般文字输出  

```
\a 发出警告声  
\b 退格键  
\c 最后不加上换行符号  
\n 换行且光标移至行首  
\r 回车，即光标移至行首，但不换行  
\t 插入tab  
\\ 插入\字符  
\0nnn 插入nnn（八进制）所代表的ASCII字符  
echo -e '\033[43;31;5mmagedu\033[0m'  
\xHH插入HH（十六进制）所代表的ASCII数字（man 7 ascii）
```
**echo的用法**
```
[root@centos7 ~]#echo $SHELL
/bin/bash
```
echo既是内部命令又是外部命令
```
[root@centos7 ~]#type -a echo
echo is a shell builtin
echo is /usr/bin/echo
```
可以用 man 帮助查看 echo 的用法和选项
```
[root@centos7 ~]#man echo


ECHO(1)                    User Commands                    ECHO(1)

NAME
       echo - display a line of text

SYNOPSIS
       echo [SHORT-OPTION]... [STRING]...
       echo LONG-OPTION

DESCRIPTION
       Echo the STRING(s) to standard output.

       -n     do not output the trailing newline

       -e     enable interpretation of backslash escapes

       -E     disable interpretation of backslash escapes (default)

       --help display this help and exit

       --version
              output version information and exit
```
echo中{}的用法

```
[root@centos7 ~]#echo file{1,2,3}
file1 file2 file3
[root@centos7 ~]#echo file{1..9}
file1 file2 file3 file4 file5 file6 file7 file8 file9
```
命令行扩展：$( ) 或 ``
```
[root@centos7 ~]#echo  "This system's name is $(hostname) "
This system's name is centos7.localdomain 
[root@centos7 ~]#echo "i am `whoami` "
i am root 
```
