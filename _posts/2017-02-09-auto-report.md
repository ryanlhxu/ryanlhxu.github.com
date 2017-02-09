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
ww



### 附template.tex，参考[用markdown写毕业论文](http://www.tuicool.com/articles/RBfaea)一文，在此表示感谢。

{% highlight r %}
\documentclass[$if(fontsize)$$fontsize$,$endif$$if(lang)$$lang$,$endif$$if(papersize)$$papersize$,$endif$]{$documentclass$}

\usepackage{placeins}       
	\providecommand{\tightlist}{%
\setlength{\itemsep}{0pt}\setlength{\parskip}{0pt}}	
\usepackage{geometry} 		% 設定邊界
\geometry{
  top=1in,
  inner=1in,
  outer=1in,
  bottom=1in,
  headheight=3ex,
  headsep=2ex
}
\usepackage[T1]{fontenc}
\usepackage{lmodern}
\usepackage{amssymb,amsmath}
\usepackage{ifxetex,ifluatex,booktabs}
\usepackage{fixltx2e} % provides \textsubscript
% use upquote if available, for straight quotes in verbatim environments
\IfFileExists{upquote.sty}{\usepackage{upquote}}{}
\ifnum 0\ifxetex 1\fi\ifluatex 1\fi=0 % if pdftex
  \usepackage[utf8]{inputenc}
$if(euro)$
  \usepackage{eurosym}
$endif$
\else % if luatex or xelatex
  \usepackage{fontspec} 	% 允許設定字體
  \usepackage{xeCJK} 		% 分開設置中英文字型
  \setCJKmainfont{STSong} 	% 設定中文字型
  \setmainfont{Times New Roman} 	% 設定英文字型
  \setromanfont{Times New Roman} 	% 字型
  \setmonofont{Courier New}
  \linespread{1.2}\selectfont 	% 行距
  \XeTeXlinebreaklocale "zh" 	% 針對中文自動換行
  \XeTeXlinebreakskip = 0pt plus 1pt % 字與字之間加入0pt至1pt的間距，確保左右對整齊
  \parindent 0em 		% 段落縮進
  \setlength{\parskip}{0pt} 	% 段落之間的距離
  \ifxetex
    \usepackage{xltxtra,xunicode}
  \fi
  \defaultfontfeatures{Mapping=tex-text,Scale=MatchLowercase}
  \newcommand{\euro}{€}
\setCJKfamilyfont{hwzs}{STZhongsong}                        %华文中宋  hwzs  
\newcommand{\hwzs}{\CJKfamily{hwzs}}  
\setCJKfamilyfont{hwk}{STKaiti}                                    %华文楷体  hwk  
\newcommand{\hwkt}{\CJKfamily{hwk}}  		  
\setCJKfamilyfont{hwxh}{STXihei}                                %华文细黑  hwxh  
\newcommand{\hwxh}{\CJKfamily{hwxh}}  	  
  \setCJKfamilyfont{hei}{SimHei}                                    %黑体  hei  
\newcommand{\hei}{\CJKfamily{hei}}                          % 黑体   (Windows自带simhei.ttf)  

\setCJKfamilyfont{hwsong}{STSong}                            %华文宋体  hwsong  
\newcommand{\hwst}{\CJKfamily{hwsong}}  	  
  
$if(mainfont)$
    \setmainfont{$mainfont$}
$endif$
$if(sansfont)$
    \setsansfont{$sansfont$}
$endif$
$if(monofont)$
    \setmonofont{$monofont$}
$endif$
$if(mathfont)$
    \setmathfont{$mathfont$}
$endif$
\fi
% use microtype if available
\IfFileExists{microtype.sty}{\usepackage{microtype}}{}
$if(geometry)$
\usepackage[$for(geometry)$$geometry$$sep$,$endfor$]{geometry}
$endif$
$if(natbib)$
\usepackage{natbib}
\bibliographystyle{plainnat}
$endif$
$if(biblatex)$
\usepackage{biblatex}
$if(biblio-files)$
\bibliography{$biblio-files$}
$endif$
$endif$
$if(listings)$
\usepackage{listings}
$endif$
$if(lhs)$
\lstnewenvironment{code}{\lstset{language=Haskell,basicstyle=\small\ttfamily}}{}
$endif$
$if(highlighting-macros)$
$highlighting-macros$
$endif$
$if(verbatim-in-note)$
\usepackage{fancyvrb}
$endif$
$if(tables)$
 \FloatBarrier
\usepackage{longtable}
$endif$
$if(graphics)$
\usepackage{graphicx}
% We will generate all images so they have a width \maxwidth. This means
% that they will get their normal width if they fit onto the page, but
% are scaled down if they would overflow the margins.
\makeatletter
\def\maxwidth{\ifdim\Gin@nat@width>\linewidth\linewidth
\else\Gin@nat@width\fi}
\makeatother
\let\Oldincludegraphics\includegraphics
\renewcommand{\includegraphics}[1]{\Oldincludegraphics[width=\maxwidth]{#1}}

$endif$
\ifxetex
  \usepackage[setpagesize=false, % page size defined by xetex
              unicode=false, % unicode breaks when used with xetex
              xetex]{hyperref}
\else
  \usepackage[unicode=true]{hyperref}
\fi
\hypersetup{breaklinks=true,
            bookmarks=true,
            pdfauthor={$author-meta$},
            pdftitle={$title-meta$},
            colorlinks=true,
            urlcolor=$if(urlcolor)$$urlcolor$$else$blue$endif$,
            linkcolor=$if(linkcolor)$$linkcolor$$else$magenta$endif$,
            pdfborder={0 0 0}}
\urlstyle{same}  % don't use monospace font for urls
$if(links-as-notes)$
% Make links footnotes instead of hotlinks:
\renewcommand{\href}[2]{#2\footnote{\url{#1}}}
$endif$
$if(strikeout)$
\usepackage[normalem]{ulem}
% avoid problems with \sout in headers with hyperref:
\pdfstringdefDisableCommands{\renewcommand{\sout}{}}
$endif$
\setlength{\parindent}{0pt}
%\setlength{\parskip}{6pt plus 2pt minus 1pt}
\setlength{\emergencystretch}{3em}  % prevent overfull lines


\title{\huge 在OSX平台上的XeLaTeX中文測試} % 設置標題，使用巨大字體
\author{FoolEgg.com} 		% 設置作者
\date{February 2013} 		% 設置日期
\usepackage{titling}
\setlength{\droptitle}{-8em} 	% 將標題移動至頁面的上面


\usepackage{fancyhdr}
\usepackage{lastpage}
\pagestyle{fancyplain}


$if(numbersections)$
\setcounter{secnumdepth}{5}
$else$
\setcounter{secnumdepth}{0}
$endif$
$if(verbatim-in-note)$
\VerbatimFootnotes % allows verbatim text in footnotes
$endif$
$if(lang)$
\ifxetex
  \usepackage{polyglossia}
  \setmainlanguage{$mainlang$}
\else
  \usepackage[$lang$]{babel}
\fi
$endif$
$for(header-includes)$
$header-includes$
$endfor$


$if(title)$
\title{$title$}
$endif$
\author{$for(author)$$author$$sep$ \and $endfor$}
\date{$date$}


\begin{document}
$if(title)$
\maketitle
$endif$


$for(include-before)$
$include-before$


$endfor$
$if(toc)$
{
\hypersetup{linkcolor=black}
\setcounter{tocdepth}{$toc-depth$}
\tableofcontents
}
$endif$
$body$


$if(natbib)$
$if(biblio-files)$
$if(biblio-title)$
$if(book-class)$
\renewcommand\bibname{$biblio-title$}
$else$
\renewcommand\refname{$biblio-title$}
$endif$
$endif$
\bibliography{$biblio-files$}


$endif$
$endif$
$if(biblatex)$
\printbibliography$if(biblio-title)$[title=$biblio-title$]$endif$


$endif$
$for(include-after)$
$include-after$


$endfor$
\end{document}
{% endhighlight %}