
# **1.Ubuntu16.10环境下Apache配置** 
  Ubuntu用apt-get install apache2安装apache2后，配置文件都在/etc/apache2目录下。

## 1.1.基本原理
  apache2在启动的时候自动读取/etc/apache2/apache.conf文件的配置信息，不同的配置项按功能  
  分布在不同的文件中，然后被Include包含到apache2.conf这个主配置文件中，方便管理。就是说事  
  实apache2主配置文件只有一个，即apache2.conf，其他的都是被Include进来的。可以把所以的配  
  置都放在apache2.conf或者任何一个配置文件中，但是划分到不同文件会让我们管理起来方便很多。
  
## 1.2.pache2.conf配置文件
  该文件是apache的住配置文件，包括三个级别的配置。
* 控制apache服务器执行过程的全局配置。
* 定义主服务或者默认服务器的参数配置，这些配置会响应Virtual Host不处理的请求。这类配置也为  
  所有的Virtual Host配置提供默认值。
* Virtual Host相关的配置使得同一个apache服务进程处理向不同IP地址或者主机名发送的请求。

  `#Section1:Global Environment`  
  `#ServerRoot:apache服务器根目录。主配置文件，日志都在该目录。`  
  `#注意路径结束时不要加斜杠，默认时/etc/apache2`  
  `ServerRoot "/etc/apache2“`  
  `LockFile ${APACHE_LOCK_DIR}/accept.lock`  
  `#apache服务启动时在该文件记录进程ID号`  
  `#This needs to be set in /etc/apache/envvars`  
  `PidFile ${APACHE_PID_FILE}`  
  `#连接超时，单位秒`  
  `Timeout`  
  
# **2.重启Ubuntu后apache出现问题的解决方案**  

* 现象  
AH00526: Syntax error on line 74 of /etc/apache2/apache2.conf:
Invalid Mutex directory in argument file:${APACHE_LOCK_DIR} 

* 解决方案  
sudo /etc/init.d/apache2 restart 后解决  

# **3.Linux常用命令**   
* 新建文件touch 文件名  
* 查询网络端口占用 netstat -ap
* 杀死进程 kill + pid  
* Tab键，命令行自动补全，  两下Tab键，列出所有可选命令行补全  

## 3.1.查询文件列表，ls命令  
* ls / 将列出根目录下的文件清单,如果给定一个参数，将会使该参数作为命令行的运行目录  
* ls -l 将会列出更详尽的文件清单
* ls -a 将会给出所有文件的清单，包括隐藏文件  
* ls -p 显示文件类型  

## 3.2.查询当前所在目录  
* pwd  

## 3.3.进入其他目录  
* cd cd/root/  

## 3.4.在屏幕上输出字符  
* echo "hello world"

## 3.5.显示文件内容  
*  cat your file name  

## 3.6.移动文件  
* mv file1.txt file2.txt 此时，file1.txt被删除，其内容被移到file2.txt,在后面加 -v 会显示移动文件的反馈信息  

## 3.7.建立空文本文件  
* touch  your file name  

## 3.8.删除文件目录  
* rm -i  your file name 删除文件时显示提示信息，i就是interface的意思
* rm -r your dir name 删除文件夹时必须指定-R,R就是recursive即循环参数  
* alias rm = "rm -i" -i 会成为rm命令的默认参数  

## 3.9.查看进程  
* ps查看你所启动的所有进程  
* ps -a 查看所有进程，包括其他用户启动的进程  
* ps -auxww，是一个非常人性化的命令，除一些极其特殊的进程外，会以一个高可读的形式显示进程信息  

## 4.0.控制流程  

### 4.0.1.输入输出  
* 输入用来从键盘读入信息，输出用于在屏幕上显示信息，我们能重定向命令中输入输出流的位置  

### 4.0.2.输出重定向  
* 如果你想把命令的输出留重定向到一个文件而不是终端,你可以在ls命令后加上 >your file name  
* 如果指定文件名的文件不存在，则创建该文件，如果该文件已存在，则覆盖旧文件
* 要想每次不覆盖文件，在文件末尾添加新内容，则应使用>>your file name  

### 4.0.3.输入重定向  
* 还可以把文件的内容作为命令的输入  
* 如sort < your file name  

### 4.0.4.管道  
* Linux的强大之处在于能把简单的命令组合成复杂的功能，通过键盘上的\|符号完成，即把前一个命令的输出当做后一个命令的输入  
* 

## 4.1.grep命令  
* Linux系统中grep命令是一种强大的文本搜索工具，它能使用正则表达式搜索文本，并把匹配的行打印出来。grep全称是Global Regular Expression Print，表示全局正则表达式版本，它的使用权限是所有用户  

## 4.2.后台进程  
* CLI不是串行系统接口，你可以在执行其他命令时给出系统命令，要启动一个后台进程，追加"\&"在命令后面,除了不能同时开始执行命令外，这时，\&相当于";"
* sleep 60&  
ls 
睡眠命令在后台运行，你依然可以和计算机交互

* 如果一个命令占用很多时间，可以按下ctrl+Z来停止进程，输入bg使其转入后台，输入fg可以使其重新转入前台
