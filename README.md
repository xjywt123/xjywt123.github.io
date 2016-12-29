
# **Ubuntu16.10环境下Apache配置**  
  Ubuntu用apt-get install apache2安装apache2后，配置文件都在/etc/apache2目录下。

## 基本原理
  apache2在启动的时候自动读取/etc/apache2/apache.conf文件的配置信息，不同的配置项按功能  
  分布在不同的文件中，然后被Include包含到apache2.conf这个主配置文件中，方便管理。就是说事  
  实apache2主配置文件只有一个，即apache2.conf，其他的都是被Include进来的。可以把所以的配  
  置都放在apache2.conf或者任何一个配置文件中，但是划分到不同文件会让我们管理起来方便很多。
  
## apache2.conf配置文件
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
  `Timeout  
  `  
# **重启Ubuntu后apache出现问题的解决方案**  
* 现象  
AH00526: Syntax error on line 74 of /etc/apache2/apache2.conf:
Invalid Mutex directory in argument file:${APACHE_LOCK_DIR} 

* 解决方案  
sudo /etc/init.d/apache2 restart 后解决
  
# **Linux常用命令**
* 新建文件touch 文件名  

# **图片**  
![my_img](http://img06.tooopen.com/images/20160920/tooopen_sy_179407883616.jpg)
