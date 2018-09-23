# alias and date
###  alias：命令别名
语法：alias[别名]=[命令名称]  
参数：若不加参数，则会列出当前所有的别名设置  

```
[root@centos7 ~]#alias
alias cdnet='cd /etc/sysconfig/network-scripts/'
alias cp='cp -i'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'
```

```
[root@centos7 ~]#cat /etc/bashrc 
# /etc/bashrc
# System wide functions and aliases
# Environment stuff goes in /etc/profile

[root@centos7 ~]#alias ct='cat /etc/bashrc'
[root@centos7 ~]#ct
# /etc/bashrc
# System wide functions and aliases
# Environment stuff goes in /etc/profile
```
**unalias**：撤销别名  
unalias [-a] name [name ...]  
-a 取消所有别名
```
[root@centos7 ~]#unalias ct
[root@centos7 ~]#ct
bash: ct: command not found...
Similar command is: 'tc'
```
 
在命令行中定义的别名，仅对当前shell进程有效
如果想永久有效，要定义在配置文件中  
仅对当前用户：~/.bashrc  
对所有用户有效：/etc/bashrc

```
[root@centos7 ~]#vim .bashrc

# .bashrc

# User specific aliases and functions

alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'
alias cdnet='cd /etc/sysconfig/network-scripts/'
# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi
```
**source**:生效文件

```
[root@centos7 ~]#source .bashrc
```
如果别名同原命令同名，如果要执行原命令，可使用  
\ALIASNAME  
“ALIASNAME”  
‘ALIASNAME’  
command ALIASNAME  
/path/commmand  

### 命令格式
COMMAND [OPTIONS...] [ARGUMENTS...]  
选项：用于启用或关闭命令的某个或某些功能  
短选项：-c 例如：-l, -h  
长选项：--word 例如：--all, --human-readable  
参数：命令的作用对象，比如文件名，用户名等  
注意：  
多个选项以及多参数和命令之间使用空白字符分隔  
取消和结束命令执行：Ctrl+c，Ctrl+d  
多个命令可以用;符号分开  
一个命令可以用\分成多行  

## date
：用来显示或设定系统的日期与时间  

**命令参数**  
-d<字符串>：显示字符串所指的日期与时间。字符串前后必须加上双引号  
-s<字符串>：根据字符串来设置日期与时间。字符串前后必须加上双引号  
-u：显示GMT

```
[root@centos7 ~]#date
Sun Sep 23 16:56:31 CST 2018
```

```
[root@centos7 ~]#date -s "16:59:22 2018-09-23"
Sun Sep 23 16:59:22 CST 2018
```




```
[root@centos7 ~]#man date
DATE(1)                    User Commands                    DATE(1)

NAME
       date - print or set the system date and time

SYNOPSIS
       date [OPTION]... [+FORMAT]
       date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

DESCRIPTION
       Display  the  current  time  in the given FORMAT, or set the
       system date.

       Mandatory arguments to long options are mandatory for  short
       options too.

       -d, --date=STRING
              display time described by STRING, not 'now'

       -f, --file=DATEFILE
              like --date once for each line of DATEFILE
```
##### clock：显示硬件时钟
-s, --hctosys 以硬件时钟为准，校正系统时钟  
-w, --systohc 以系统时钟为准，校正硬件时钟  
时区：/etc/localtime

```
[root@centos7 ~]#clock
Sun 23 Sep 2018 05:02:50 PM CST  -0.476039 seconds
```
**cal**：显示日历  

```
[root@centos7 ~]#cal
   September 2018   
Su Mo Tu We Th Fr Sa
                   1
 2  3  4  5  6  7  8
 9 10 11 12 13 14 15
16 17 18 19 20 21 22
23 24 25 26 27 28 29
30
```
