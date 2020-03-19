# ubuntu14.04 安装配置JDK

1,下载jdk-7u45-linux-x64.tar.gz  
网址：  
[ http://www.oracle.com/technetwork/java/javase/downloads/index.html
](http://www.oracle.com/technetwork/java/javase/downloads/index.html)  
2, 解压JDK  
进入JDK的下载目录

    
    
    sudo tar zxvf jdk-8u91-linux-x64.tar.gz  -C ~/jdk/
    （8u91代表版本号，请自行修改，下同）

3,设置环境变量（全局）

    
    
    sudo gedit  /etc/profile  

打开profile文件输入

    
    
    export JAVA_HOME=~/jdk/jdk1.8.0_91
    export CLASSPATH=".:$JAVA_HOME/lib:$CLASSPATH"  
    export PATH="$JAVA_HOME/bin:$PATH"  

4,设置系统默认JDK

    
    
    sudo update-alternatives --install /usr/bin/java java ~/jdk/jdk1.8.0_91/bin/java 300  
    sudo update-alternatives --install /usr/bin/javac javac ~/jdk/jdk1.8.0_91/bin/javac 300  
    sudo update-alternatives --config java  

5, 验证JDK  
输入命令

    
    
    java -version  

见到JDK的信息则表示成功。

  * [ 点赞  ](javascript:;)
  * [ 收藏  ](javascript:;)
  * [ 分享 ](javascript:;)
  *     * 文章举报 

[ ![](https://profile.csdnimg.cn/2/1/1/3_thriller)
![](https://g.csdnimg.cn/static/user-reg-year/1x/20.png)
](https://blog.csdn.net/thriller)

[ thriller ](https://blog.csdn.net/thriller)

发布了19 篇原创文章  ·  获赞 18  ·  访问量 5万+

[ 私信 ](https://im.csdn.net/im/main.html?userName=thriller) 关注


