Title: 推荐一个让wordpress能发邮件的插件^
Date: 2009-04-21 11:07
Author: Ley
Category: wordpress
Slug: a-plugin-for-wordpress-send-email
Tags: wordpress, 插件, 邮件

昨天突然觉得我在自己机器上搭的wordpress系统有一点毛病，就是无法给注册用户发送通知邮件，也无法给管理员发送邮件。

于是，在google上搜了一下，找到一个[国内的兄弟][]写的程序，感觉挺好用的。

另外，ps一下，我觉得对比其它插件，这个插件最大的特点就是能返回服务器的信息，帮助你调试一些可能出现的问题。如果你要用gmail的话，请修改php.ini，找到“;extension=php\_openssl.dll”这一行，去掉前面的分号，然后重启Apache服务。

具体的可以看[他的文章][]。

  [国内的兄弟]: http://www.himagic.cn/
  [他的文章]: http://www.himagic.cn/index.php/archives/127.html
