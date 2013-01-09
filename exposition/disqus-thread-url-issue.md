Title: 吐槽一下DISQUS的thread链接错误问题
Date: 2013-01-03 10:23
Author: Ley
Category: 说明文
Slug: disqus-thread-url-issue
Tags: disqus, disqus_url, pelican

## 背景

### 没有信息量的背景

事情得从前段时间我把博客从[WordPress](http://imley.net/2012/12/25/bye-wordpress/ "Bye WordPress")换到[Pelican](http://blog.imley.net/2012/12/25/hello-pelican/ "Hello, Pelican")开始说起。

当时，一时头脑发热的我，告别了使用多年，人见人爱，花见花开的WordPress，转投比较小众的[Pelican](https://github.com/getpelican/pelican "ddd")（我承认是受[@yegle](http://twitter.com/yegle "Yegle的博客")的启发）。

### 信息量来了

Pelican是静态博客，如果需要评论的话，默认是用的[DISQUS](http://disqus.com/ "DISQUS")的评论服务。如果使用Pelican的notmyidea这个主题，在`pelicanconf.py`里头添上`DISQUS_SITENAME`字段，就可以使用DISQUS的评论服务了——很爽是吧。

一开始我都没有意识到这个问题，直到有一天我的博客被评论了——我一看DISQUS给我的邮件。里头评论那个链接怎么指向的是`http://localhost:8000/slug/`这样的测试地址啊，简直是不能忍啊。于是，为了解决这个问题，我开始了艰难的求索之路。

## 失败的尝试

### 试图修改URL

不是URL错了嘛，我改就是，于是从DISQUS的用户的角度出发，我进入了DISQUS的后台。找到了`Tools->Migrate Threads`这个选项卡。总之，我在尝试了上头所列的三种方式（"Domain Migration Wizard", "Upload a URL map", "Recirect Crawler"）之后，都无果…

另外，这期间我认为DISQUS可能修改数据会有延时，等了好几天。总之，最后的结论就是，通过管理界面的工具，不靠谱。

### 试图调用DISQUS的API

在第一次尝试失败以后，我本着计算机系学生“应该写代码解决问题”的精神，展开了阅读DISQUS API并尝试写脚本解决该问题的工作。

还好的是，[DISQUS的API文档][disqus-api-doc]还算完善，也有[Python的API bindings][disqus-python-api-binding]，事情的痛苦指数降低了一半。

在艰难地获取了token以后，我开始写脚本并进行测试了。我用的是`Threads`对象的`update`方法，虽然[文档页面][thread-update-api]上头写明了:

> **this method is currently under development and subject to change.**

我还是义无反顾，抱着既然走到这一步。就继续走下去的信息，走了下去。

事情从这个时候似乎开始柳暗花明了，很快，我写了一个脚本，找到哪些Threads的URL是错误的，然后`update`它们（提示：**下面这段脚本只是为了说明我如何“尝试”解决问题，千万不要指望它能解决问题**）：

    :::python
    from disqusapi import DisqusAPI

    secret_key = 'your_secret_key'
    public_key = 'your_public_key'
    token = 'your_token'
    
    wrong_url = 'localhost:8000'
    
    disqus = DisqusAPI(secret_key, public_key)
    
    # perhaps you should use a Paginator
    threads = disqus.threads.list(forum='your_site')
    
    for thread in threads:
        link = thread['link']
        print link
        if link is None:
            continue
        if link.find(wrong_url) >= 0:
            link = link.replace(wrong_url, 'blog.imley.net')
            try:
                result = disqus.threads.update(thread=thread['id'],
                                               url=link,
                                               access_token=token)
                print "id:%s now with url:%s" % (result['id'],
                                                 result['link'])
            except(Exception) as e:
                print e

因为我十分怀疑自己对DISQUS API的理解，所以我打印了处理结果。结果我**欣喜**地发现，API返回回来的URL地址正确了！

但是我还是十分怀疑我是不是调用错了API，于是我再用API查了一次。结果刚刚更新的`link`字段，还是令人憋屈的`localhost:8000`打头的地址——我还是以为有延时，于是等了一天——一天以后，我再次用API去查，还尼玛是`localhost:8000`。于是，我的第二轮，宣告尝试。

这一轮，最让我感觉到憋屈的是。尼玛要不就别给我返回，咋返回了期望的response还不给人家处理。不过DISQUS也可以说，这个页面上头一个大大的告示，就是告诉你这个API方法不可靠嘛~

## 解决问题

### 能解决吗

我几乎快要放弃了，但每每欲放弃，不爽之情油然而生。于是我只能硬着头皮弄下去了，在这么多次尝试无果以后，我终于开始怀疑——*“这个URL字段是不是能改”*了，于是我又去DISQUS的官方帮助里头找，终于，让我找到了[这个页面][disqus-url-update-policy]，上头说到：

> Thread URLs cannot be updated by passing `disqus_url` after a thread has been created. `disqus_url` can only be set once, upon thread creation.

尼玛啊~~根本就不能改啊！尼玛...尼玛怎么就不在`Threds->update`的[API页面][thread-update-api]稍微提一下呢，尼玛真是浪费感情啊！

于是，这个问题终于被我最终判定为不可解决了，我几乎感觉不会再爱了。

*P.S. 这个问题也不是完全无解，你可以把文章链接改了，重新导入，或者迁移一次threads，但是我情感上真的接受不了*

### 问题的源头

如果这个问题真的不能解决，那么，我还能做的，就只有预防它了。所以，我终于开始仔细思考造成这个问题的原因了。

找啊找啊找朋友，找到一个好朋友，终于让我找到了这个问题的[官方解释][disqus-js-vars]，原来，在threads被初始化的时候`disqus_url`这个参数被设置了，而且不会了。而这个参数如果没有被在页面中显式地声明，那么就会通过`window.location.href`获取。

就算再不熟悉js，我也知道了，这就是**万恶之源**啊。

*回头想想，为啥讨论这个问题的人少，大概是大家不会在本地预览一下博客，而是直接上传到服务器吧。*

### 避免问题

既然问题的原因一清二楚了，那么剩下的事情就好办了，看了一下Pelican的代码，找到主题对应DISQUS threads调用的这段API，然后一顿修改，测试，问题解决了，人民群众表示情绪很稳定。

最后，抱着回馈大众的指导思想，我将自己写的三行代码commit，并且提交了生平第一个[pull request][pr-on-disqus-url-issue]。不过事情过去这么多天了，大家一点反应也没有，大概是我的英文太烂，抑或是这个实现实在是太暴力了…

### 回头想想

现在想想，如果我一开始就对造成问题的原因寻根问底，也许就不用走这么多弯路，浪费这么多感情了。归根结底，还是解决问题的态度不端正啊。

## 后记

我之所以会花这么长的时间，为这个根本不复杂的问题，写这么一篇日志，只是因为，**我用过情**。

[disqus-api-doc]: http://disqus.com/api/docs/ "DISQUS api docs"
[disqus-python-api-binding]: https://github.com/disqus/disqus-python "DISQUS API bindings for Python"
[thread-update-api]: http://disqus.com/api/docs/threads/update/ "DISQUS thread update api"
[disqus-url-update-policy]: http://help.disqus.com/customer/portal/articles/735170-how-can-i-update-discussion-urls "how to update disqus url"
[disqus-js-vars]: http://help.disqus.com/customer/portal/articles/472098-javascript-configuration-variables#disqus-url "DISQUS对初始化一个Threads的各个变量的解释"
[pr-on-disqus-url-issue]: https://github.com/getpelican/pelican/pull/669 "我提交的Pull Request"
