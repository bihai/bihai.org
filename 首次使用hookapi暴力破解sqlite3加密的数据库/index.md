# 首次使用HOOKAPI暴力破解SQLITE3加密的数据库

怕原作者生气，在这就不放源代码了。  
最近研究“给力大CI典”的时候，反汇编了一下，是用DELPHI写的，使用SQLITE3定制版本加密了一部分数据库，于是通过HOOKAPI到sqlite3_k
ey，找到了密码，然后用VB6写了个解密SQLITE3的工具，把数据库都解密了。  
这里就给出两个密钥：  
1、shao8977545*S  
用于zclb.db。  
2、shao897754*Z  
用于其余的加密数据库。  
具体用法很简单，就是调用sqlite3_key，然后sqlite3_rekey，然后就没有然后了。  
因为是用来学习反编译和SQLITE加解密，这里就只说说思路而已，具体请下载支持“给力大CI典”，资料都在里面。

  * [ 点赞  2  ](javascript:;)
  * [ 收藏  ](javascript:;)
  * [ 分享 ](javascript:;)
  *     * 文章举报 

[ ![](https://profile.csdnimg.cn/2/1/1/3_thriller)
![](https://g.csdnimg.cn/static/user-reg-year/1x/20.png)
](https://blog.csdn.net/thriller)

[ thriller ](https://blog.csdn.net/thriller)

发布了19 篇原创文章  ·  获赞 18  ·  访问量 5万+

[ 私信 ](https://im.csdn.net/im/main.html?userName=thriller) 关注


