Title: 在Wordpress MU首页调用登陆接口的方法
Date: 2009-04-15 12:00
Author: Ley
Category: wordpress, 编程
Tags: php, wordpress

前面在帮别人做（应该是“改”）一个带博客系统小网站时，用的[wordpress
mu][]，然后看到一款模板挺好用的，于是想把它改成wordpress的模板，结果那个模板有个从首页登陆的登陆框，于是想物尽其用，在网上找了一些代码，
把登陆接口放在了首页，下面就把代码贴出来吧（别人的代码，加上我调用时做的部分修改）：

（把这断代码添加到functions.php末尾，再调用）<!--more-->

<p>
~~~~ {lang="php" line="1"}
function home_page_login_form() {global $current_user, $blog_id;if ( ! is_user_logged_in() ) {?>用户登陆用户名: 密码: 记住我现在注册} else {$blogs = get_blogs_of_user($current_user->ID);$username = $current_user->user_login;$siteurl= get_settings('siteurl');?>Hi, !   你的博客:if ( ! empty($blogs) ) foreach ( $blogs as $blog ) {$blog_id = $blog->userblog_id;$details = get_blog_details($blog_id);$blogname = htmlspecialchars( $details->blogname );echo "" . $blogname . " | 管理";}?>}}
~~~~

</p>

效果见下图：

![][] ![][1]

登陆前 登陆后

原讨论帖见：[http://mu.wordpress.org/forums/topic.php?id=2730][]

代码文本附件：[登陆代码][]

&nbsp

*本文来自[Ley's Blog][]，转载请注明出处。*

  [wordpress mu]: http://mu.wordpress.org/
  []: http://imley.net/upload/pics/Capture1.JPG
  [1]: http://imley.net/upload/pics/Capture2.JPG
  [http://mu.wordpress.org/forums/topic.php?id=2730]: http://mu.wordpress.org/forums/topic.php?id=2730
  [登陆代码]: http://imley.net/wp-content/uploads/2009/05/wpmulog.rar
  [Ley's Blog]: http://imley.net "Ley's Blog"
