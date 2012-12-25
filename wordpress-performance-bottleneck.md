Title: WordPress的性能瓶颈
Date: 2011-11-24 20:38
Author: Ley
Category: OS, wordpress, 网络, 说明文
Slug: wordpress-performance-bottleneck

如果不是有这个free usage trial（感谢[亚马逊][]），我不会这么快用上VPS；

如果不是这台主机内存有613MB（再次感谢[亚马逊][]），我是不敢在VPS上直接上LAMP的；

如果不是做QA的经历（这次感谢[百度][]），我可能没有意识进行性能测试；

总之，最近我搞了台VPS，自己配置了LAMP环境（感谢[ubuntu][]），迁移了博客，然后测试了一下性能，%\*\^&...（此处省略1000字）

总之，我的结论是：

-   WordPress对主机**CPU消耗很严重**，不管是LAMP，还是LNMP；
-   在我的博客上头，当请求网站首页时，并发数10，开了5秒以后，CPU\_IDLE直接降到0，网站基本处于无响应状态。为了证明这不是由Apache引起的，我后来又搭了一个套LNMP环境，发现内存和CPU占用确实减小了，但是，达到CPU\_IDLE=0只是时间问题——其实也撑不了10秒；
-   一定开WP super
    cache，开了以后，请求大部分变成了静态文件请求，上150的并发无压力；
-   开了WP super
    cache以后，至少是这个主机，运行WordPress的博客，我觉得LAMP，LNMP差别不大，毕竟有613MB的总内存在那里，如果并发数在200以内的话，二者差别不大；
-   以上测试结论得出极不严谨，最好不要参考；
-   我预感自己还是会迁移到LNMP上的；

</p>

  [亚马逊]: http://aws.amazon.com/free/ "免费试用AWS"
  [百度]: http://www.baidu.com/
  [ubuntu]: http://cloud.ubuntu.com/
