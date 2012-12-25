Title: Firefox支付宝插件安装问题的解决
Date: 2009-05-09 20:59
Author: Ley
Category: 网络, 说明文
Slug: add-alipay-plugin-for-firefox
Tags: firefox, 插件, 支付宝

![][]![][1]

首先，在本文开始之前，先向伟大的[mg12][]致敬，是他的[这篇文章][]，解开了困扰我长达一两天的一个问题。

**问题起因**：

由于本人前两天买了块硬盘，于是重做了系统，于是也重装了firefox，但是装上firefox之后，不是特别稳定，于是卸载了又重装了一下（看似废话，其实这里是**<span style="color: #ff00ff;">伏笔</span>**）。

</p>

问题就是，前天还是昨天的时候，想上淘宝充话费，于是习惯性地打开FF，输入[taobao.com][]，然后再搞定买卖手续后发现：没有装支付宝插件。不过很好解决啊，下载了淘宝提示的[非IE插件][]，然后关掉FF，安装完打开FF，准备付钱之时，发现支付宝还不能登陆。于是我以为是FF关得不够长，于是又关了它一分多钟，再装。事实证明这种唯心的，不科学的方法是解决不了问题的...

</p>

**问题的初步解决**：

我的方法很没有意思，下载了一个[Chrome][]，然后给它装了插件（方法同firefox，那个安装包是很多浏览器通吃的）。真的不能怪我，我也急着交话费，迟了连动态口令都收不到了。

</p>

**问题的彻底解决**：<!--more-->

这里就真的要感谢neoease了，今天上他的博客，本来是无聊逛逛，不料发现他不久以前写的一篇“[手动为
Firefox
添加支付宝安全插件][这篇文章]”（还好它还在首页，不然我真的看不见了），他提到支付宝插件的安装实际是在
Windows 注册表中找到系统上的浏览器路径, 然后把插件安装到浏览器相应目录。

</p>

然后它提到，可以手动提取安装包里面的"npaliedit.dll"到firefox的plugin目录。这对我来说太好办了，我都不用提取，直接从chrome的plugin目录(我的是"Users\\XXX\\AppData\\Local\\Google\\Chrome\\Application\\Plugins")拷了一个过来。放到firefox目录下，久违的密码输入窗口又出现啦\~嗯，问题完美解决，赶紧给人家[道谢][]\~

</p>

**问题的分析**：

既然问题解决了，何不估一回“事后诸葛亮”呢，既然mg12说是调用了注册表以后找到安装位置的，会不会是插件插件安装包把位置找错了\~\~这里就涉及到前面的一个<span style="color: #ff00ff;">**伏笔**</span>啦，因为我重装系统后，装了firefox又卸载了再装的，第一次是在d盘，第二次是在c盘，我赶紧到d盘曾经装过firefox的目录去查看，果然，插件被安装到了这里。

</p>

就此，我分析一下问题的产生的原因，可能是我在第一次卸载firefox的时候，并没有选择完全卸载而是保留一些用户数据。不过我查找了数据表里面和firefox有关的键值，也没有找到原来d盘的相关信息，至于支付宝是怎么找到的，我就懒得探究啦。

</p>

嗯，这个故事到这里算是结束了，和我一样出现这个问题的可能性可能是非常非常小的，但是，从这个故事中，我们学会，万一遇到了问题，瞎掰是弄不清的，最好是Google一下，或者，逛别人的[博客][]\~;-)

*本文来自[Ley’s Blog][]，转载请注明出处。*

</p>
[ad\#post-end]

  []: https://img.alipay.com/images/cms2/200902/20090212536919.gif
  [1]: http://www.mozilla.com/img/tignish/about/logo/download/logo-wordmark-version-preview.png
  [mg12]: http://www.neoease.com
  [这篇文章]: http://www.neoease.com/install-aliply-plugin-into-firefox/
  [taobao.com]: http://taobao.com
  [非IE插件]: https://img.alipay.com/download/aliedit/npaliedit.exe
  [Chrome]: http://pack.google.com/intl/zh-cn/pack_installer.html?hl=zh-cn
  [道谢]: http://www.neoease.com/install-aliply-plugin-into-firefox/#comment-13064
  [博客]: http://feed.feedsky.com/imley "rss我吧"
  [Ley’s Blog]: ../ "Ley's Blog"
