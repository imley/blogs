Title: 将搜狗浏览器的教育网加速功能应用到firefox
Date: 2009-04-21 12:47
Author: Ley
Category: 网络
Tags: 代理服务器, 加速, 搜狗, 教育网

**<span style="color: #ff0000;">声明</span>一下：**写这个是因为苦于在教育找一个好用稳定的代理实在不易，但是本人是FF爱好者，已经不习惯IE内核的浏览器了，写到这里只是给各位使用其它浏览器而加速不了的用户一个找代理的方便途径。本人是<span style="color: #ff0000;">**极力反对**</span>将代理用于迅雷的下载的，毕竟教育网内的[下载资源][]本来就很多，而且迅雷太占带宽了。所以，请各位给搜狗的整理节省一下资源。另外，建议每天打开一次搜狐首页。或者像我\~用[搜狗输入法][]\~;-)

</p>

Sogou教育网加速是在后台新建一个子进程，专门做代理使用的，打开这个子进程后，Sogou浏览器会在本地8081端口创建一个代理。然后我们在用Sogou浏览器的时候，系统就会使用这个代理来上网。

</p>

弄清这个原理以后，我们就可以利用Sogou浏览器的这个特点来实现对其它浏览器的加速了（因为虽然其加速功能不错，但是稳定性实在太差了，而且，本人已经严重依赖firefox了）。

</p>

其实也很简单，这里有两个实现方法：

</p>

​1. 最傻瓜式：
这个方法很简单，就是打开Sogou浏览器，然后将其教育网加速功能打开。这时候，再把你想用的浏览器的代理服务器地址设为“127.0.0.1”，把端口设为“8081”，支持https,http；（如果你不知道怎么设置代理服务器，先[google][]吧）然后，你的浏览器速度[就飞快][]了。

</p>

但是，这种方法有一个很明显的缺点，就是必需得开着Sogou，虽然现在大家内存都很大，但是怎么看怎么碍眼。所以就有第二种方法了。

</p>

​2. 稍微进阶式：<!--more-->[ad\#in-post]
其实也不难，按"Win"+"R"键打开运行对话框输入“C:Program
Files\\SogouExplorer\\SogouExplorer.exe
-proxy”（以我的系统安装的为例，具体使用时把前面的那个地址替换成你的地址即可，不过别忘了后面的-proxy）；这样一来，你就不用打开Sogou浏览器，使用它的加速进程了。

</p>

如果还觉得麻烦的话。可以在注册表的启动项里面添加一条记录，具体在：[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run]，然后，添加一个string变量，名字自己取，值就是那个“C:Program
Files\\SogouExplorer\\SogouExplorer.exe -proxy”。然后就可以了。

</p>

​3. 补充方法：

</p>

前面偶然看到别人的一个方法，应该说比我的两个方法都要<span style="color: #0000ff;">**简单好用**</span>：

</p>

这个方法就是，新建一个快捷方式，然后将快捷方式的路径填写为："
<span style="color: #993366;">"C:Program
Files\\SogouExplorer\\SogouExplorer.exe"-proxy</span>
"（以我的系统为例，紫色字体为你要填写的快捷路径地址，**<span style="color: #800080;">注意</span>**，前面的路径要有**<span style="color: #3366ff;">英文半角</span>**引号，后面的参数不带引号，快捷方式的建立为在桌面点右键-\>新建-\>快捷方式）。然后你可以把这个快捷方式添加到“开始菜单”的启动项里头，这样就可以实现开机启动了。

</p>

这里，为我前面提供的复杂方法，道歉\~;-)

</p>

特别感谢：[byr论坛][] Geeti提供的方法。

</p>

***PS: 在sogou浏览器1.1版，windows 7下测试有效。***

</p>

<em><strong>  

</strong></em>

</p>

*本文来自[Ley's Blog][]，转载请注明出处。*  

[ad\#post-end]

</p>

  [下载资源]: http://bt.byr.edu.cn "北邮人BT"
  [搜狗输入法]: http://wubi.sogou.com/ "http://wubi.sogou.com/"
  [google]: http://g.cn
  [就飞快]: http://imley.net
  [byr论坛]: http://bbs.byr.edu.cn/wForum/
  [Ley's Blog]: http://imley.net "Ley's Blog"
