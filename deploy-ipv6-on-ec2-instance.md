Title: EC2上配置IPV6
Date: 2011-11-21 16:17
Author: Ley
Category: 说明文
Slug: deploy-ipv6-on-ec2-instance
Tags: ec2, ipv6, amazon

前两天弄了这台主机以后，就发现连接速度那是相当慢啊——于是，终于忍不住的我，今天把服务器换到了东京机房——不过这是后话了...

为了让学校访问能够快一些，我决定给EC2主机打一个隧道，上IPV6，经过反复试验，最后得到较为成功的解决方案如下：

第一步：隧道申请：
----------------

</p>
​1. 到he.net的[免费隧道][]申请页面注册用户，申请成功以后密码发到邮箱；

​2. 登陆后选择“[Create BGP Tunnel][]”，申请隧道：

Endpoit就填你申请的EC2的静态地址；

</p>

服务器的话，视情况选择吧，我选的日本，其实我觉得Hongkong应该也不错；

</p>
​3. 创建成功以后，会显示隧道信息，点击“Example
Configuration”出现配置指南，我使用的是“Linux-net-tools”；

二、配置隧道：
-------------

</p>
​1.
这一步实在是很简单，把上一步得到的脚本存到某个脚本文件，例如set\_v6.sh；

​2. 然后这样子：

<p>
~~~~ {.brush:shell}
sudo sh set_v6.sh #太坑爹了
~~~~

</p>
​3.
当然，你也可以把这个加入系统启动脚本，或者把脚本里头的内容加入到网络配置文件里头去，这个就不表了；

三、One More Thing：
-------------------

</p>
事情完了吗，没有...接下来的内容才是本文的重点：

首先，he.net是通过ICMP协议确认客户端状态的，所以，你需要保证他们的服务器能够ping通你。但是亚马逊似乎给系统加了某种特别的防火墙规则，尽管我在防火墙里头允许了he.net服务器的IP，但是有时还是会出现ping不通的问题。

经过搜索和观察，发现当从EC2主机发出V6的ping请求（不管是ping谁）时，外面在大致10分钟以内可以ping进来，于是，我的终极解决方案便是：

把 **ping6 -c 2
ipv6.google.com**加入到了crontab里头，虽然坑爹，但是经过测试，有效。

本文到此结束。

本文在一定程度上参考了这篇文章：[http://benctechnicalblog.blogspot.com/2011/01/ipv6-in-amazon-ec2.html][]

  [免费隧道]: http://tunnelbroker.net/
  [Create BGP Tunnel]: http://tunnelbroker.net/new_tunnel.php?type=bgp
  [http://benctechnicalblog.blogspot.com/2011/01/ipv6-in-amazon-ec2.html]:
    http://benctechnicalblog.blogspot.com/2011/01/ipv6-in-amazon-ec2.html
