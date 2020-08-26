# 使用 Git Hook 实现网站的自动部署

自动化能解放人类的双手，而且更重要的是，因为按照规定的流程来走，也减少了很多误操作的产生。不知道大家平时都是怎么样更新自己生产环境的代码的，FTP
覆盖旧文件、服务器定时任务去 build 最新的源码，还是有更高级的做法？

目前我在使用 Git Hook 来部署自己的项目。Git Hook 是 Git 提供的一个钩子，能被特定的事件触发后调用。其实，更通俗的讲，当你设置了
Git Hook 后，只要你的远程仓库收到一次 push 之后，Git Hook 就能帮你执行一次 bash 脚本。

下面是我使用 Git Hook 进行简单的自动化部署，可能还有更高级的做法，大家自己去挖掘。

在服务器初始化一个远程 Git 仓库

git init 和 git –bare init 初始化出来的仓库是完全不一样的，具体我 Google
了下，英文倒是理解了，但是要翻译出中文却不知道用什么形容词去称呼这2种仓库。

这里我们要通过 git –bare init 初始化一个远程仓库

    
    
    $ cd ~
    $ mkdir testRepo
    $ cd testRepo
    $ git --bare init

在服务器初始化一个本地 Git 仓库

这个仓库就是通过 git init 初始化出来最常见的本地仓库，它的作用是拉去远程仓库（其实就在它旁边）最新的源码，然后在这个仓库里进行编译，把代码编译到
www 目录（网站的根目录）。

    
    
    $ cd ~
    $ mkdir testRepo
    $ cd testRepo
    $ git --bare init

为远程仓库设置 Hook

    
    
    $ cd ~/testRepo/hooks
    $ vim post-receive

post-receive 里面的执行脚本

    
    
    #!/bin/sh
    unset GIT_DIR
    DeployPath=/home/user/testDeploy
    WwwPath=/home/wwwroot/testDeploy
    cd $DeployPath
    git add . -A && git stash
    git pull origin master
    # 下面这2步都是按照实际你自己添加的bash脚本
    fis release -Dompd $WwwPath # 我使用的FIS，对前端代码进行编译
    qrsync /home/user/qiniutools/config.json # 使用七牛同步工具进行同步

最后，为 post-receive 添加可执行权限

    
    
    chmod +x post-receive

为本地仓库添加 remote 源

这次的本地仓库就真的是你开发机上面的本地了。在你原有 Git 项目里面添加一条新的 remote 源，以后往这个 remote 源里面 push
代码就会自动触发上面那 bash 脚本了。

    
    
    $ git remote add deploy user@server.ip:/home/user/testRepo
    $ git push deploy master

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


