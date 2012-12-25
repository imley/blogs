Title: ubuntu下VLC中文字幕显示问题的解决
Date: 2009-12-19 00:11
Author: Ley
Category: 抄袭作文
Slug: chs-subtitle-in-ubuntu-vlc
Tags: linux, ubuntu, vlc, OS 

为了为可能进入的实验室实习做准备，今天重新装上了ubuntu，今天的安装总的来说还是顺利多了。在播放软件上，这次我选择了VLC，因为感觉mplayer虽然强大，但是始终界面不是十分友好。而VLC也是灰常强大的。

但是，在Linux下播放电影时，经常会遇到乱码的问题，下面就谈谈我的经验。

造成字幕乱码的原因可能有**两个**:

### 1. GB字符的解码：

</p>
因为Linux下中文默认采取utf-8编码，所以在解码GB字符时，会产生乱码现象，除了用gedit将字幕文件转换为utf-8编码外，还可以通过设置VLC实现，具体方法在[ubuntu论坛][]早有讨论，现摘录如下：

<p>
> ​1. 首先启动VLC，按Ctrl+P,左下角的显示设置 选 全部
>
> </p>
>
> ​2. 依次点开：视频－字幕／OSD－文本渲染器
> 右侧的字体栏中，选择一个中文字体。（我选的是/usr/share/fonts/truetype/wqy/wqy-zenhei.ttc）
>
> ​3. 接着点开：输入／编码－其它编码器－字幕 右侧的 字幕文本编码 选 GB18030
>
> <p>
> ​4. *然后 把 自动检测 UTF－8 字幕 格式化字幕
> 前面的勾去掉。（这条在新版中似乎已经不存在）<!--more-->*

</p>
<em>

</em>

### 2. 系统字体配置文件的原因

</p>
这个也是我具体遇到的问题，幸好，由于flash插件出现了同样的现象，在[另外一个博客][]中，我找到了这个问题的解决方法，同样是摘抄如下：

<p>
> 输入： cd /etc/fonts/conf.d/
>
> </p>
>
> 为了安全，备份一下： sudo cp 49-sansserif.conf 49-sansserif.conf\_backup
>
> 输入如下指令： sudo gedit ./49-sansserif.conf
>
> 此时文件显示内容。
>
> 将其中的第1、2、4个后面的sans-serif或者serif用你自己系统中支持中文的字体的名字代替，注意字体名字的大小写
>
> 比如：我的系统中安装了wqy-zenhei.ttf，我则用wqy-zenhei代替上述所说的字段，结果如下：
>
> \<match target=”pattern”\>
>
> \<test qual=”all” name=”family” compare=”not\_eq”\>
>
> \<string\>wqy-zenhei\</string\>
>
> \</test\>
>
> \<test qual=”all” name=”family” compare=”not\_eq”\>
>
> \<string\>wqy-zenhei\</string\>
>
> \</test\>
>
> \<test qual=”all” name=”family” compare=”not\_eq”\>
>
> \<string\>monospace\</string\>
>
> \</test\>
>
> \<edit name=”family” mode=”append\_last”\>
>
> \<string\>wqy-zenhei\</string\>
>
> \</edit\>
>
> <p>
> \</match\>

</p>
OK，以上两种问题，也就是我在使用Linux下的播放软件中遇到的问题，将两个合起来介绍一下，方便一下可能遇到同样问题的朋友。其实，都是别人的智慧。

*本文来自[Ley's Blog][]，转载请注明出处，另外，请给我个链接。*

<em>

</em>

[ad\#post-end]

  [ubuntu论坛]: http://forum.ubuntu.org.cn/viewtopic.php?f=74&t=201887&start=0
  [另外一个博客]: http://spiritfrog.javaeye.com/blog/194121
  [Ley's Blog]: http://imley.net/2009/12/19/chs-subtitle-in-ubuntu-vlc/
    "Ley's Blog"
