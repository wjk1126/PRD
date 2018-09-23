# history
history主要用于显示历史指令记录内容，下达历史记录中的指令提高工作效率

**用help来查看一下history的选项和使用帮助**
```
[root@centos7 ~]#help history
history: history [-c] [-d offset] [n] or history -anrw [filename] or history -ps arg [arg...]
    Display or manipulate the history list.
    
    Display the history list with line numbers, prefixing each modified
    entry with a `*'.  An argument of N lists only the last N entries.
    
    Options:
      -c	clear the history list by deleting all of the entries
      -d offset	delete the history entry at offset OFFSET.
    
      -a	append history lines from this session to the history file
      -n	read all history lines not already read from the history file
      -r	read the history file and append the contents to the history
    	list
      -w	write the current history to the history file
    	and append them to the history list
```
**查看历史**

```
[root@centos7 ~]#history 
    1  who am i
    2  echo PS1
    3  echo $PS1
    4  PS1="\[\e[1;5;41;33m\][\u@\h \W]\\$\[\e[0m\]"
    5  PS1="\[\e[1;33m\][\u@\h \W]\\$\[\e[0m\]"
    6  PS1="\[\e[1;35m\][\u@\h \W]\\$\[\e[0m\]"
    7  nano /etc/profile.d/env.sh
    8  clear
    9  rz
   10  vim /etc/motd
```

**history的选项**

```
-d  删除指令的命令
-c  清空命令
-a  手工追加当前回话的命令历史到历史文件中
n   显示最近n条命令
-r: 读历史文件附加到历史列表
-w: 保存历史列表到指定的历史文件
-n: 读历史文件中未读过的行到历史列表
-p: 展开历史参数成多行，但不存在历史列表中
-s: 展开历史参数成一行，附加在历史列表后
```


**调用历史命令**

```
!#  重复执行第#条命令
!!  重复执行上一条命令
!str 执行以str开头的命令（默认最近的）
!？ 获得最后执行的状态码
```
**演示**
```
[root@centos7 ~]#history 5
  487  history 
  488  history -d 487
  489  history 3
  490  whoami  注意
  491  history 5
[root@centos7 ~]#history -d 490
[root@centos7 ~]#history 5
  489  history 3
  490  history 5
  491  history -d 490
  492  history n 5
  493  history 5
[root@centos7 ~]#history -c
[root@centos7 ~]#history 
    1  history 
[root@centos7 ~]#history 
    1  history 
    2  whami
    3  whoami
    4  history 
[root@centos7 ~]#!!
history 
    1  history 
    2  whami

```
**快捷键**  
==ctrl+r== 在命令历史中搜索命令   
（reverse-i-search）`’：  
==ctrl+g== 从历史搜索中退出

**命令历史环境变量**  
==HISTSIZE==：命令历史记录的条数

```
[root@centos7 ~]#echo $HISTSIZE
1000
[root@centos7 ~]#HISTSIZE=500
[root@centos7 ~]#echo $HISTSIZE
500
```
==HISTFILESIZE==：命令历史文件记录历史的条数  

```
[root@centos7 ~]#echo $HISTFILESIZE
1000
[root@centos7 ~]#HISTFILESIZE=800
[root@centos7 ~]#echo $HISTFILESIZE
800
```
==HISTTIMEFORMAT=“%F %T “== 显示时间  
==HISTIGNORE=“str1:str2*:… “== 忽略str1命令，str2开头的历史

**环境变量**：HISTCONTROL  

```
ignoredups  默认，忽略重复的命令，连续且相同为“重复”
ignorespace 忽略所有以空白开头的命令
ignoreboth  相当于ignoredups, ignorespace的组合
erasedups   删除重复命令
```

export 变量名="值“  
存放在 /etc/profile 或 ~/.bash_profile
