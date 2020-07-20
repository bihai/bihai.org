# WEIPHP 4 欢迎语BUG：如果是多图文，则所有文章都显示第一篇

#  WEIPHP 4 欢迎语BUG：如果是多图文，则所有文章都显示第一篇

找了半天，原来是个低级错误：  
打开\Application\Home\Model\WeixinModel.class.php  
goto 298行，  
加入：

    
    
    $art=[];

问题原因，卧槽，循环语句没有初始化变量，后面的校验是根据前一个的来的，真不敢商用啊:)。

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


