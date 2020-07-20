# Ubuntu 安装黑客背单词Reciteword

Reciteword是一款中文界面的背单词软件（也称黑客背单词），功能比较强大。在Ubuntu中安装可能会遇到一些小困难，故在此说明一下。  
本文介绍的是从源码编译安装的过程。  
Table of Contents  
1 下载及安装（转载部分）  
1.1 下载程序  
1.2 准备工具  
1.3 黑客背单词的安装  
2 遇到的编译错误  
3 问题解决  
1 下载及安装（转载部分）  
1.1 下载程序  
reciteword的网站是：  
作者提供了如下几个包，请按需下载源码包：  
主程序源码（必须） reciteword

课本（重要） reciteword-books  
词典（可选） reciteword-dicts  
皮肤（可选） reciteword-skins-rw  
真人发音 WyabdcRealPeopleTTS （可选，是stardict的真人语音）  
1.2 准备工具  
先安装编译需要的包  
apt-get install libesd0-dev pkg-config libgtk2.0-dev esound  
如果是Ubuntu 8.04版本，安装时可能会出现删除pulseaudio-esound-compat，ubuntu-
desktop这两个文件，请之后再安装回去，如果不安装，进入桌面后桌面不成正常使用，我的方法是重启后按ctrl+alt+f1，进入控制台，打入以下命令：  
sudo apt-get install ubuntu-desktop就会安装这两个文件，重启后正常
安装libesd0-alsa0，保证开启esd後，仍能用alsa。  
apt-get install libesd-alsa0启用esd，这是reciteword播放声音所必须的：（假设是gnome环境）  
在菜单中：系统->首选项->音效，在打开的窗口中：音效->允许软件混音(ESD)。  
为了使设置生效，建议你最好重新启动系统。  
1.3 黑客背单词的安装  
安装过程就没有什么特别的了，进入存有reciteword的文件后：

    
    
    　tar -xvfj reciteword-*.tar.bz2
    　　cd reciteword-0.*
    　　./configure –prefix=/usr
    　　make
    　　sudo make install 
    　　2

遇到的编译错误  
ubuntu会出现这样编译出错  

    
    
    bookfile.cpp: In function ‘gchar* rw_book_get_value(const gchar*, gchar*, gint)’:
    bookfile.cpp:95: error: invalid conversion from ‘const char*’ to ‘gchar*’
    bookfile.cpp: In function ‘gint rw_book_get_file_info(gchar*, gchar**, gchar**, gchar**, gchar**, gchar**, gchar**)’:
    bookfile.cpp:140: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:153: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:154: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:155: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:156: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:157: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp: In function ‘BookFile* rw_book_open_file(gchar*)’:
    bookfile.cpp:228: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:229: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:230: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:231: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:232: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:233: warning: deprecated conversion from string constant to ‘gchar*’
    bookfile.cpp:209: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
    make[3]: *** [bookfile.o] 错误 1
    make[3]:正在离开目录 `/tmp/word/reciteword-0.8.4/src'
    make[2]: *** [all-recursive] 错误 1
    make[2]:正在离开目录 `/tmp/word/reciteword-0.8.4/src'
    make[1]: *** [all-recursive] 错误 1
    make[1]:正在离开目录 `/tmp/word/reciteword-0.8.4'
    make: *** [all] 错误 2
    

3 问题解决  

    
    
    　bookfile.c
    pp:95: error: invalid conversion from ‘const char*’ to ‘gchar*

根据以上错误找到 bookfile.cpp 在头文件处加上两句代码  

    
    
    #include "bookfile.h"
    #include <cstring>
    #include <cstdio>
    #include <sys/stat.h>
    #include <fstream>
    #include <string>
    
    const gchar* str1;
    const gchar* str2 = strchr(str1, 'a');

再找到函数 （大概在90行里）

    
    
    static gchar *
    rw_book_get_value (const gchar * str1, gchar * str2,gint utf8)
    -----------------------------------------------------

把原来的 tmp1 = strstr (str1, str2);  
改为 tmp1 = (gchar*)strstr (str1, str2);  
经过上面的改动 再编译即可

编译成功，要安装到/usr/local/share/reciteword/：

    
    
    tar -xjvf reciteword-books-0.8.5.tar.bz2 -C /usr/local/share/reciteword/
    tar -xjvf reciteword-dicts-0.8.2.tar.bz2 -C /usr/local/share/reciteword/
    tar -xjvf reciteword-skins-rw-0.8.2.tar.bz2 -C /usr/local/share/reciteword/skins
    tar -xjvf reciteword-skins-rw_en-0.8.2.tar.bz2 -C /usr/local/share/reciteword/skins
    tar -xjvf WyabdcRealPeopleTTS.tar.bz2 -C /usr/share

搞定

  * [ 点赞  1  ](javascript:;)
  * [ 收藏  ](javascript:;)
  * [ 分享 ](javascript:;)
  *     * 文章举报 

[ ![](https://profile.csdnimg.cn/2/1/1/3_thriller)
![](https://g.csdnimg.cn/static/user-reg-year/1x/20.png)
](https://blog.csdn.net/thriller)

[ thriller ](https://blog.csdn.net/thriller)

发布了19 篇原创文章  ·  获赞 18  ·  访问量 5万+

[ 私信 ](https://im.csdn.net/im/main.html?userName=thriller) 关注


