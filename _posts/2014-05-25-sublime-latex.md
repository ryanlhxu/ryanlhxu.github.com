---
layout: post
title: 用Sublime Text编写LaTeX
description: 补全代码与表格制作
category: Academy
tags: [LaTeX, Sublime]
comments: true
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

使用Sublime Text搭建LaTeX环境的权衡在于你不能像Texmaker或者WinEdt运用菜单栏或者公式栏插入你想要的环境或者符号了，但是可以更加自由的制作代码片段并更加快速的自动补全。因此对LaTeX的基本命令已经比较熟悉的可以尝试使用Sublime Text。

<br/>

先用Sublime Text 2搭建LaTeX环境，MikTeX或者TeXlive都是可以的。先要通过Sublime Text的宏包管理下载LaTeXTools，然后搭建LaTeX都编写环境。具体步骤可参考[这篇文章](http://elegantlatex.org/2014/04/21/sublime-text-latex/)的后半部分。

<br/>

LaTeXTools已经帮你写好了不少代码片段。例如输入bfigure，再按Tab键就补全了插入图片的代码片段; 输入bit，再按Tab键就补全了罗列环境的代码片段……

<br/>

要看具体有哪些代码片段，点击Preference -> Browse Packages, 找到LaTeXTools这个文件夹，按类型排序，找到所有后缀是sublime-snippet的文件看看就知道了。如果想添加一个常用的代码片段，例如最优化的片段，


<p>$$\begin{equation}  
 \begin{array}{cll}
 & \underset{x}{\text{max}}  & f(x) \\
 & \text{subject to}  & x>0
 \end{array}
\end{equation}
$$</p>
 
 <br/>

首先新建一个sublime-snippet文件，输入

{% highlight html %}
<snippet>
	<content><![CDATA[
\begin{equation*}
 \begin{aligned}
 & \underset{${1:x}}{\text{${2:max}}}
 & & ${3:f_0(x)} \\\\
 & \text{subject to}
 & & ${4:f_i(x) \leq b_i, \; i = 1, \ldots, m.}
 \end{aligned}
\end{equation*}
]]></content>
	<tabTrigger>bopt</tabTrigger>
	<scope>text.tex.latex</scope>
</snippet>
{% endhighlight %}

这里需要解释一下的是，如${1:x}, 数字1代表光标第一次停留的地方，即是第一处会被替换的地方；x是将会被替代的内容。按Tab键会依次推进。

<br/>

而

{% highlight html %}
<tabTrigger>bopt</tabTrigger>
{% endhighlight %}
  

则代表输入bopt点击Tab键就可以自动补全最优化的代码。

<br/>

此代码片段文件编写完毕后，命名并且保存在LaTeXTools文件夹内。今后在编写LaTeX时需要用到最优化格式，只需要输入bopt后按Tab键即可补全完整代码。

