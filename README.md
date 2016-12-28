
# **Ubuntu16.10环境下Apache配置**  
  Ubuntu用apt-get install apache2安装apache2后，配置文件都在/etc/apache2目录下。

## 基本原理
  apache2在启动的时候自动读取/etc/apache2/apache.conf文件的配置信息，不同的配置项按功能  
  分布在不同的文件中，然后被Include包含到apache2.conf这个主配置文件中，方便管理。就是说事  
  实apache2主配置文件只有一个，即apache2.conf，其他的都是被Include进来的。可以把所以的配  
  置都放在apache2.conf或者任何一个配置文件中，但是划分到不同文件会让我们管理起来方便很多。
  
# **Linux常用命令**
* 新建文件touch 文件名  

# **图片**  
![my_img](http://img06.tooopen.com/images/20160920/tooopen_sy_179407883616.jpg)
