Title: 云中漫步
Date: 2011-11-18 22:09
Author: Ley
Category: 小学作文
Slug: dance-in-the-cloud
Tags: aws, ec2, vps

昨天刚说要申请AWS的账户，今天就弄了台主机，把博客迁到EC2上头了，真是看了一堆教程以后手痒，没有办法。也不管他原来的主机还有五个月才到期了。

直接上的ubuntu server
10.04的AMI，原来用ubuntu还是比较习惯了，结果今天那个网速太坑爹，phpmyadmin装了一半断网了，弄了半天才把所有的进程强杀了。

628的内存，上一个LAMP环境还是够用的，而且我还上了apache2-mpm-itk，确实是有些奢侈，不过我这个PV完全没有问题。

我也没有测试性能，貌似也差不到哪儿去。等哪天有时间了，比较一下LAMP和LNMP到底有啥性能上的区别，再看是用LAMP还是LNMP，或许可以考虑牵头架nginx，搭一个RoR玩玩。

这些都是后话了，总结一下吧。今天已经弄好的东西：

1.  把ubuntu 10.04装上去，并且装上LAMP（8G的root
    volume，系统用了不到1G，还有将近7G可以用）；
2.  安装和配置sendmail，现在可以发邮件了（其实就是为了WordPress发邮件），还设了一个MX记录，为了尽量不判垃圾吧；
3.  LAMP配置的是apache-mpm-itk，这个博客放在小权限用户下，应该安全性有一定保障，不过性能扛不扛得住是一个问题；
4.  把博客迁移过来了，直接改了A记录，对于国内用户来说，流亡一下WordPress不算啥；

</p>
下一步要做的事情：

<div>
</p>

1.  考虑测试一下这个服务器的性能；
2.  要是能加一个反向代理提一下速度最好了；
3.  可以考虑搞一个he.net的V6隧道试试看，教育网能够加速一下；
4.  搞懂AWS这一套东西到底是咋算的，还有2G的EBS的free usage怎么利用上；
5.  可以试一下写一些脚本，用svn啥的实现一些自动部署之类的东东；
6.  考虑一下安全性，比如说防止恶意攻击啥的；

</p>
以上事项排名不分先后，期望在free usage tier过期之前完成。

<p>
</div>
</p>

