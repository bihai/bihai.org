# shell 脚本中经常要用到ssh。怎么能不交互的输密码呢？

1、登录A机器  
2、 ` ssh-keygen -t [rsa|dsa] ` ，将会在~/.ssh下生成密钥文件和私钥文件 ` id_rsa,id_rsa.pub ` 或
` id_dsa,id_dsa.pub `  
3、将 ` .pub ` 文件复制到B机器的 ` .ssh ` 目录， 并

    
    
    cat id_dsa.pub >> ~/.ssh/authorized_keys

4、大功告成，从A机器登录B机器的目标账户，不再需要密码了（直接运行 ` #ssh 192.168.1.100 ` ）

面交互输入，就得使用 ` expect ` 脚本，例:

    
    
    #!/bin/bash
     passwd='123456'
     /usr/bin/expect <<-EOF
     set time 30
     spawn ssh  root@192.168.1.100
     expect {
     "*yes/no" { send "yes\r"; exp_continue }
     "*password:" { send "$passwd\r" }
     }
     expect "*#"
     send "cd /home/trunk\r"
     expect "*#"
     send "ls\r"
     expect "*#"
     send "exit\r"
     interact
     expect eof
     EOF

  * [ 点赞  3  ](javascript:;)
  * [ 收藏  ](javascript:;)
  * [ 分享 ](javascript:;)
  *     * 文章举报 

[ ![](https://profile.csdnimg.cn/2/1/1/3_thriller)
![](https://g.csdnimg.cn/static/user-reg-year/1x/20.png)
](https://blog.csdn.net/thriller)

[ thriller ](https://blog.csdn.net/thriller)

发布了19 篇原创文章  ·  获赞 18  ·  访问量 5万+

[ 私信 ](https://im.csdn.net/im/main.html?userName=thriller) 关注


