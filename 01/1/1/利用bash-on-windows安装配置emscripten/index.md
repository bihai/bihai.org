# 利用“bash on windows”安装配置emscripten

#  利用“bash on windows”安装配置emscripten

  1. 配置使用bash on windows：   
1） 所有设置、更新和安全、针对开发人员、开发人员模式；  
2） Windows 更新、高级选项、获取Insider Preview版本；  
3） 选择你的会员级别、快；  
4） 最低更新至14316版本；  
5） 搜索、启用或关闭windows功能；  
6） 选中Windows Subsystem for Linux (Beta)；  
7） 重新启动、运行、bash  
8） 按Y键下载ubuntu及配置bash。

  2. 安装emscripten：   
1） 在/etc/apt/sources.list中加入国内快速镜像，如：163.com等；  
2） 更新升级ubuntu环境  
` apt-get update && apt-get upgrade `  
3） 安装构建工具  
` apt-get install build-essential `  
4） 安装CMake  
` apt-get install cmake `  
5）安装 Python  
` sudo apt-get install python2.7 `  
6）安装 node.js  
` sudo apt-get install nodejs `  
7）安装 Java  
` sudo apt-get install default-jre `  
8）安装 git  
` sudo apt-get install git-core `  
9） 变更到工作路径  
` cd ~/ `  
10）获取emsdk安装文件  
` wget https://s3.amazonaws.com/mozilla-games/emscripten/releases/emsdk-
portable.tar.gz `  
11）解压缩  
` tar vxf emsdk-portable.tar.gz `  
12） 变更到安装路径  
` cd emsdk_portable/ `  
13） 更新安装  
` ./emsdk update && ./emsdk install latest `  
14）激活最新版本  
` ./emsdk activate latest `  
15）设置默认路径  
` source ./emsdk_env.sh `  
16）测试安装结果  
` ./emcc tests/hello_world.cpp `

好了，这样就可以在windows中解决emscripten无法执行python命令等问题了，完美哟。

想的真美，可惜现在的bash on windows因为SYMLINK和TTY有BUG，无法运行TAR，需要等待下一个版本来解决，貌似已经有眉目了，期待啊。

windows 10 preview build 14332 推送已经貌似解决了symlink问题，可以使用node
6.0.0，安装emscripten也不成问题了。

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


