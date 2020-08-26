# 越狱之后如何远程连接（SSH）iOS设备？

使用linux-ios-toolchain 在bash on windows中安装iOS软件，需要越狱的IPHONE或者IPAD，怎么安装呢？大家都知道，i
OS系统是基于Unix的，算是Unix衍生出来的新系统，而要玩转Unix系统，无疑最根本的使用远程连接即SSH来用命令行直接控制你的iPhone,如果有人要
问，远程连接（SSH）究竟有什么用呢？举个简单例子，前段时间号称一键清除、修复Cydia的越狱应用iLex RAT就是需要用远程连接的命令行才能使用的。

在越狱之前，苹果对root权限控制得非常之严，根本没有可能允许用户直接访问iOS的文件系统，更别提远程连接了，幸运的是，越狱之后，用户真正当家作主了，今天我
们就来看一下如何远程连接（SSH）iOS设备。

1.在Cydia中搜索、安装OpenSSH软件。

![openssh](https://img-blog.csdn.net/20160429113257187)

2.安装之后，打开设置 -> WiFi。

![这里写图片描述](https://img-blog.csdn.net/20160429113331091)

3.点击已经连接的WiFi的右边的小箭头查看详情，记下iPhone当前网络IP地址。

![这里写图片描述](https://img-blog.csdn.net/20160429113404888)

4.在PC端打开SSH软件，如Putty、SecureCRT等，都差不多，下面以免费的Putty举例说明如何连接。

5.下载Putty后，不需要安装，直接打开即可。

6.打开之后输入第4步中记下的网络IP地址，当然你的电脑需要与PC保持在同一个网络下才行：

![这里写图片描述](https://img-blog.csdn.net/20160429113429482)

7.点击Open开始进行远程连接，首先会弹出一个警告，点击Y.

![这里写图片描述](https://img-blog.csdn.net/20160429113438767)

8.连接上之后需要校验用户名和密码，用户名使用root,密码默认为alpine.

![这里写图片描述](https://img-blog.csdn.net/20160429113451751)

9.连接上之后就像操作一台普通unix系统一样，这里我们为了安全起见修改一下root密码，非常简单，但前提是需要有一点linux基础。

![这里写图片描述](https://img-blog.csdn.net/20160429113500826)

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


