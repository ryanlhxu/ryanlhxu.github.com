---
layout: post
title: 自动化报告生成框架
description: 提高金融从业者的日常工作效率
modified: 2017-02-09
category: Coding
tags: [Python,Finance]
comments: true
---

### 环境
* Window 7及以上系统、Mac OS以及Ubuntu等Linux系统

* Python 2.7

* Wind客户端，并且修复其python插件

* Pandoc

* XeLaTeX编译环境

### 简单步骤
* 通过脚本文件组织报告内容并生成Markdown文件（具体见流程图）。

* 通过Pandoc将Markdown文件转换成PDF文件，以下命令将test.md转化成test.pdf，其中template.tex是XeLaTeX模板，可根据偏好修改模板。

    $ pandoc --template=template.tex --latex-engine=xelatex test.md -o test.pdf
	

### 流程图

<figure>
	<a href="{{ site.url }}/images/report_framework.jpg"><img src="{{ site.url }}/images/report_framework.jpg"></a>
	<figcaption>自动化报告流程图</figcaption>
</figure>


### 模板template.tex
* 在[用markdown写毕业论文](http://www.tuicool.com/articles/RBfaea)一文中使用的template.tex上稍作修改，在此表示感谢。

