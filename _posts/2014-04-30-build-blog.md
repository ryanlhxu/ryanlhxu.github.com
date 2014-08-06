---
layout: post
title: 使用Jekyll在GitHub上搭建个人博客
description: "像黑客一样写博客"
modified: 2014-05-3
category: Coding
tags: [Jekyll, GitHub, Blog]
comments: true
---

<section id="table-of-contents" class="toc">
  <header>
    <h3>Contents</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->

> Blogging Like a Hacker.   

搭建博客的主要目是自娱自乐一下，同时希望保存一些自己学习和生活中的心得体会。如果还能与其他人分享、交流相互的经历，那就更好了。一方面自己对网络技术的了解确实很少，但另一方面又不想直接使用其他商业网站的博客（有太多的广告）。于是打算自己搭建一个相对比较简单与干净的静态网页。

选择Jekyll是因为他让博客安置在GitHub上面，而自己之前已经使用过GitHub，并且积累了初步的Git基础。虽然之前也用过WordPress，但是觉得那个东西还是略显笨重。当然完全免费也是我使用Jekyll的一个重要原因。

在搭建博客之前，我还是建议先了解一下jekyll的基本构架和GitHub使用的基本知识，同时熟练使用一个比较出色的本文编辑器，比如Sublime Text之类的。如果对html语言有较好的掌握，那就更好了，不过这个可以边看边学。

简单来说这次搭建过程主要分成以下几个步骤：
 1. 搭建Ruby环境
 2. 安装Jekyll
 3. 在GitHub上建立库，克隆jekyll-bootstrap模板至本地
 4. 本地测试
 6. 创建post
 5. 修改模板及其他配置
 7. 发布

主要参考的文章是[Jekyll QuickStart](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)。

---

#### 搭建Ruby环境

jekyll是用Ruby语言写的一个静态网页生成工具，所以必须先在本地搭建好Ruby环境。在[RubyInstaller](http://rubyinstaller.org/downloads/)下载Ruby的最新版本并且安装，在安装过程中注意**勾选添加环境变量**。同时**必须**下载devkit, 解压到希望的路径下面(我将其解压到了D盘)。打开终端，先到devkit的路径下面，然后
    
    $ ruby dk.rb init
    $ ruby dk.rb install

会显示安装成功的信息。

#### 安装jekyll

仍然在命令行输入
  
    $ gem install jekyll

可能比较慢，要等待一些时间。如果一次不成功，多试几次。最后会显示安装成功。

#### 在GitHub上建立库，克隆jekyll-bootstrap模板至本地

在[GitHub](https://github.com)创建新的库，取名为USERNAME.github.com（这里的usename替换为你自己账号名字的，下同）。打开Git Shell，进入希望放置博客的路径，键入

    $ git clone https://github.com/plusjade/jekyll-bootstrap.git USERNAME.github.com
    $ cd USERNAME.github.com
    $ git remote set-url origin git@github.com:USERNAME/USERNAME.github.com.git
    $ git push origin master

稍等片刻，访问USERNAME.github.io, 就可以看到自己的博客了。

#### 本地测试

进入博客所在的路径，在终端命令行输入

    $ cd USERNAME.github.com
    $ jekyll serve

然后，打开[http://localhost:4000/](http://localhost:4000/), 即可以在本地浏览博客。

#### 创建post

仍然在命令行输入

    $ rake post title = "Hello World"

这个命令会自动在_posts目录下创建一个名为2014-04-29-hello-world.md的文件，日期缺省使用当前日期。这就是你的博客内容。
命名必须严格按照如上的格式，即yyyy-mm-dd-title.md。.md内文本格式要按照刚才生成的示例， 同时使用MarkDown语法撰写文章，具体可参考[MarkDown教程](http://daringfireball.net/projects/markdown/syntax)，我也是第一次写。

也可以不使用这个命令，直接在_posts的目录下增添一个按如上格式命名.md文件。以后写文章直接在里面添加就可以了。

####  修改模板及其他配置

如果不喜欢现在的模板，可以改变，在终端键入

    $ rake theme:install git="https://github.com/jekyllbootstrap/theme-the-program.git"
  
这样就下载了the-program这个模板。要将主题改变为the-program，键入 
  
    $ rake theme:switch name="the-program"

这样就改变了模板，更多模板请查看[http://themes.jekyllbootstrap.com/](http://themes.jekyllbootstrap.com/)。

浏览博客的时候会发现他采用了一个默认的社交评论工具"disqus", 由于这基本上市国外的东西，还是很难忍受的。所以打开_config.yml，找到comments这部分，将provider中的"disqus"改成"false"，这样就可以取消评论。但我参考了[Jekyll设置友言为社会化评论组件](http://joeyio.com/jekyll/2013/04/13/how-to-use-uyan-in-Jekyll/), 这样可以登录新浪微博等社交平台进行评论，效果不错。其实如果设置多说的话也差不多。

#### 发布

最后是更新发布你的博客，还是打开Git Shell，在博客的路径下，输入

    $ git add .
    $ git commit -m "modified theme"
    $ git push
    
再浏览博客。

其实我也是刚开始玩，准备先clone几个别人博客，仔细研究一下。等差不多配置满意了就可以专心写文章了。不过这要等到期中之后了。最近太忙了，好多问题要过段时间再来补充。先写个大概。

