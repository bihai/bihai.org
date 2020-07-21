# ubuntu之apache正向代理及反向代理(ProxyPass ProxyPassReverse)

ubuntu之apache正向代理及反向代理(ProxyPass/ProxyPassReverse)

环境是UBUNTU 最新版apache2安装的目录结构有变化网上很多文章都不适用了。

#  配置

(1)安装proxy组件

    
    
    a2enmod proxy proxy_ajp proxy_balancer proxy_connect proxy_ftp proxy_http  

(2)修改配置

    
    
    sudo vim /etc/apache2/mods-enabled/proxy.conf

如果有内容设置则设置如下：

    
    
    <IfModule mod_proxy.c>  
        #turning ProxyRequests on and allowing proxying from all may allow  
        #spammers to use your proxy to send email.  
    ProxyRequests Off  
    <Proxy *>  
        Order deny,allow  
        Deny from all  
        #Allow from .your_domain.com  
    </Proxy>  

(3)修改配置

    
    
    vim /etc/apache2/sites-enabled/default
    
    
    <VirtualHost *:80>  
      ...
         ProxyPass /test/ http://127.0.0.1:3000/  
         ProxyPassReverse /test/ http://127.0.0.1:3000/
      ...
    </VirtualHost>  

重启服务：

    
    
    sudo service apache2 restart

测试一下试试：

    
    
    cd ~/wwwroot/test
    echo hello>index.html
    python -m SimpleHTTPServer 3000

打开浏览器测试一下吧:)  
[ http://localhost/test ](http://localhost/test)

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


