# ubuntu on windows 编译安装 stardict 3.06

###  胡正写的stardict：

星际译王——拉轰吧——目前还号称是linux下最好的词典。  
胡正是四大魔幻程序员之一，虽然身体略有不适，不妨碍他的努力和优秀。  
[ http://huzheng.org ](http://huzheng.org)  
他号称所有（大部分）的软件、著作都是免费的，这一点很了不起，这也是我的梦想。  
那么程序员怎么生存呢？这是个问题。  
程序员可以兼职送外卖，呵呵。  
支持一把！

###  获取方式：

1、下载地址： [ http://code.google.com/p/stardict-3/downloads/list
](http://code.google.com/p/stardict-3/downloads/list) (需要爬墙)  
2、也可以这个： [ https://sourceforge.net/projects/stardict-4/
](https://sourceforge.net/projects/stardict-4/)  
3、或者祭出GITHUB大神：

    
    
    git clone https://github.com/huzheng001/stardict-3

还是这个比较靠谱:)

###  开始编译：

    
    
    cd stardict-3
    apt update && apt upgrade
    apt install  libenchant-dev libgtkspell-dev libgconf2-dev libgnome2-dev libgnome-common libespeak-dev  libcanberra-gtk3-dev libbonobo-2.0-dev libmysqlclient-dev flite1-dev
    ./autogen.sh
    ./configure --prefix=/usr --sysconfdir=/etc --mandir=/usr/share/man --disable-gucharmap --disable-dictdotcn --disable-festival --disable-flite

That’s all folks!

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


