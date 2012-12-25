Title: 推荐几个本地快速搭建php运行环境的工具
Date: 2009-05-06 10:16
Author: Ley
Category: 编程
Slug: some-tools-set-up-local-php-environment
Tags: apache, php

![][]

虽然本人接触[php][]已经很久，但是确实没有学到太多东西，因为每次都是断断续续的，也是因为这种断断续续，让我每次都要重新在电脑里头搭建一个php环境。但是，真正要让一个php环境搭建起来，如果逐个安装，手动配置的话，那绝对是相当的麻烦（不过我也保证你绝对会学到很多的东西，尽管有些东西是后知后觉的），所以一般来说，推荐使用一些快速搭建php环境的套件。

下面，就结合我的“心路历程”，来推荐几款这样的软件吧：<!--more-->

**1. Xammp**

<strong>![][1]

</strong>

很老牌的php搭建套件，立足于普及apache，让各们知道apache是很强大，也是很友好的。按其官方网站的说法，“XAMPP
是一个易于安装且包含 MySQL、PHP 和 Perl 的 Apache 发行版。XAMPP
的确非常容易安装和使用：只需下载，解压缩，启动即可。”，看起来是很吸引人了，我第一次搭建php环境的时候也是用的这个，但是现在已经不记得具体怎样了。

在查了一下资料以后，发现这个软件是相当的强大的。可以快速安装配置，既有GUI图形界面，又可以使用命令行批处理快速实现。而且，最为重要的是，这个软件既有Windows的版本，也有Linux的版本，甚至是Mac,
Solaris的版本，而且都是一样的好用，至于缺点，可能不是中文原生的，英文不好的可能要找一下[汉化版][]。

这里给出这个软件的官网吧，上面有详细的配置说明：[http://www.apachefriends.org/zh\_cn/xampp.html][]

**2. PhpStudy**

<strong>![][2]

</strong>

这是国内一位童鞋做的php环境套件，集成Apache+PHP+MySQL+phpMyAdmin+ZendOptimizer，一次性安装，无须配置即可使用，该程序不仅包括PHP调试环境，还包括了开发工具、开发手册等。在这里提到是因为我曾经用过很长的一段时间，你可以打开他的一个控制台，会在任务栏停放一个小图标，可以通过其图形界面实现很多功能。真的是很简单易用，但是，作者好像在开发到1.75版以后，就没有再次开发了。而且至少在我的机器上会有这样的缺点，那就是运行wordpress的执行效率特别低。所以如果只是简单学学php的话，还是可以用这款软件的。

给出一个作者博客的链接：[http://blog.chinaunix.net/u/19869/index.html][]

​3. PHPnow

![][3]

这个也是我现在电脑上用的php套件包，是国人自己的作品，包括[Apache][]-2.0.63
/ 2.2.11, [PHP][]-5.2.9-2, [MySQL][]-5.0.77 / 5.1.33, [Zend
Optimizer][]-3.3.3, [phpMyAdmin][]-3.1.3.1, \* eAccelerator
0.9.5.3(默认不启动).

这个软件的安装做得很简洁，解压（必须是英文目录）了以后就基本是按照命令行提示一步一步走，后期的配置也是通过命令行界面执行几个批处理文件实现的，还是很简洁，个人感觉虽然简洁，但确实非常好用，也很稳定，没有发现什么兼容性的问题。值得一赞的是，他提供了[快速配置多个虚拟主机][]的选项，也是因为这个，我才真正知道了原来虚拟主机是这样弄的（汗...）

同样，给出官网的链接：[http://phpnow.org/index.html][]

上面有软件的[下载][]，以及[比较详细的文档][]。不过，文档中的软件版本可能和现在不一样，最好还是下下来，跟着走走，就基本会用了(Vista下建议把UAC关了，不然可能会出错)。

嗯，也就这么多了，希望对各位有帮助，别忘了，配置好了以后，赶紧装个[wordpress][]试试，或者玩玩[刚出来正式版][]的[BuddyPress][]。

本文完。

*本文来自[Ley's Blog][]，转载请注明出处。*

  []: http://lh6.ggpht.com/_R9Ztc0cXeZc/SgDmQgX_GUI/AAAAAAAAAEk/Ilw8NKdS4zY/s400/php-logo.jpg
  [php]: http://zh.wikipedia.org/w/index.php?title=PHP&variant=zh-cn
    "如果你还不知道php是什么的话"
  [1]: http://www.apachefriends.org/img/xampp-logo-new.gif "Xammp"
  [汉化版]: http://www.google.cn/search?q=xammp%E4%B8%AD%E6%96%87%E7%89%88&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:zh-CN:official&client=firefox-a
  [http://www.apachefriends.org/zh\_cn/xampp.html]: http://www.apachefriends.org/zh_cn/xampp.html
  [2]: http://www.greendown.cn/uploadfiles/2007-11-28/20071128_174704_329.gif
    "Phpstudy"
  [http://blog.chinaunix.net/u/19869/index.html]: http://blog.chinaunix.net/u/19869/index.html
  [3]: http://phpnow.org/guide/1.png "phpnow"
  [Apache]: http://httpd.apache.org/
  [PHP]: http://cn.php.net/
  [MySQL]: http://www.mysql.com/
  [Zend Optimizer]: http://zend.com/products/zend_optimizer
  [phpMyAdmin]: http://www.phpmyadmin.net/
  [快速配置多个虚拟主机]: http://phpnow.org/pp.html
  [http://phpnow.org/index.html]: http://phpnow.org/index.html
  [下载]: http://phpnow.org/download.html
  [比较详细的文档]: http://phpnow.org/docs.html
  [wordpress]: http://www.wpcng.com/2009/02/wordpress-271-chinese-version-released/
  [刚出来正式版]: http://lucifr.com/2009/05/02/buddypress-10-released/
  [BuddyPress]: http://buddypress.org/
  [Ley's Blog]: http://imley.net "Ley's Blog"
