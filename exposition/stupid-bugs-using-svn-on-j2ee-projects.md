Title: J2EE的巨2的svn错误
Date: 2011-05-18 11:55
Author: Ley
Category: 说明文
Slug: stupid-bugs-using-svn-on-j2ee-projects
Tags: j2ee, java, svn, 编程

起因：
-----

</p>
最近把一个J2EE的工程，具体是Spring框架开发的。放在了Google
Code上头。为了图省事，直接把整个MyEclipse project放在了Google
Code上头，但是有一个烦人的问题，WebRoot\\WEB-INF下头的classes文件夹其实没有必要放上去，而且每次都会遇到一些莫名其妙的错误。

有几次，我尝试用svn删除classes目录，结果，svn莫名的把我的src也给删除了。还好svn的版本控制基本靠谱，我又checkout一次，再export，再放回去，这样的日子也基本能过。不过这样下去终究不是办法，终于，在版本号达到14时，我做了一个艰难的决定——Google之。

问题原因：
---------

</p>
原来，造成问题的原因是MyEclipse会把Src下头的所有文件拷贝到classes编译之，当然也就包括了.svn目录。所以，紊乱了...

解决方案：
---------

</p>
解决方案很简单，告诉MyEclipse不要拷贝呗。具体设置方法如下：

工程上头点击右键-\>点击Properties-\>点击Java Build
Path-\>点击Source选项卡-\>双击Exclude，编辑属性-\>在Exclusion
Pattern里头添加~~\*\*/.svn/\*\*~~(更正错误：应当是\*\*/.svn/，否则classes不被编译？)，然后再把classes
ignore了就行了。

总结：
-----

</p>
相当坑爹。
