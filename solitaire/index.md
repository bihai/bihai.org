# 微软纸牌合集资源文件研究


# 成功反编译“微软纸牌集合”资源文件
1989年，微软推出了Windows 2.0图像操作系统，微软纸牌合集(Microsoft Solitaire Collection)开始随windows捆绑，成了大众休闲放松的利器。后来微软将它单独拿出来发扬光大，做出了跨平台的游戏，还是值得一玩，可惜限制比较多，于是乎最近花了一天时间，终于成功反编译了“微软纸牌集合（Microsoft Solitaire Collection）”的资源文件，以及图片集索引逆向转为跨平台json/atlas/texturePacker文件格式，可以直接用于跨平台软件制作，包括网页版，只是作为研究而已，没什么实际意义。至此，微软全平台游戏终于全部解包完毕，包括solitaire, minesweeper等等，还是很有借鉴意义。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200819181552183.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RocmlsbGVy,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020081918155297.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RocmlsbGVy,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020081918155284.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RocmlsbGVy,size_16,color_FFFFFF,t_70#pic_center)
# 文件格式说明
微软纸牌采用BR****I算法的zip压缩文件格式作为资源文件包，图集atlasIndex索引是加密（或者说是编译）的二进制文件，不知道是不是笔者孤陋寡闻，没有找到相关资料，只好用ultralEdit/vb6/vscode分析了一天，终于凑合转为JSON文件格式，好看好用多了:)。
zip文件格式应该不用多说，但是用普通的解压缩软件解不开这些.archive文件，只好又写了一个专用的解包工具，牵扯版权就不发了。
atlasIndex文件格式比较复杂，主要如下：
 1. 文件头8字节

```vbnet
'atlas.atlasindex文件格式说明
'atlas.atlasindex file format specification
'Offset      0  1  2  3  4  5  6  7   8  9  A  B  C  D  E  F
'00000000   68 2E 00 00 B4 30 00 00  00 00 00 00 00 00 00 00   h.  ?
Type TAtlasHeader
    lOffsetTable As Long '&h2e68
    lOffsetNamelist As Long '&h30b4
End Type 'TAtlasHeader

```
第一个长整数&h2e68是索引表的偏移量位置，第二个整数&h30b4是名称列表。

 2. &h70偏移开始表结构的索引，各种跳转，实在是一言难尽啊，抽空整理一下VB6源代码，估计感兴趣的也不多。
 以上抛砖引玉，主要还是知识浅薄，孤陋寡闻，不知道是不是已经有人做了，纯粹业余兴趣，如果侵犯版权或者有其他错误请批评指正。
 

Welcome to https://bihai.org!


