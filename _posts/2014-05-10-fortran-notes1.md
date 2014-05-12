---
layout: post
title: Fortran学习笔记1
description: "Write Makefile"
modified: 2014-05-12
category: Study
tags: [Fortran,Coursera,Makefile]
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
写Makefile可以大大简化同时编译多个文件的过程，可以更加快捷的更新编译结果，并更新最终的执行程序。

### 处理多个文件

假设我们写了如下的一段较长的代码，

{% highlight fortran %}
! fullcode
program demo
    print *, "In main program"
    call sub1()
    call sub2()
end program  

subroutine sub1()
    print *, "In sub1"
end subroutine sub1  

subroutine sub2()
    print *, "In sub2"
end subroutine sub2
{% endhighlight %}

要产生执行文件，可以直接

    $ gfortran fullcode.f90 -o fullcode.exe
    $ fullcode

就能得到运行结果。

<br/>

我们经常将较长的代码拆分开来。例如将上段代码的可以拆分成主程序和两个子程序。

{% highlight fortran %}
! main.f90
program demo
    print *, "In main program"
    call sub1()
    call sub2()
end program  
{% endhighlight %}

{% highlight fortran %}
! sub1.f90
subroutine sub1()
    print *, "In sub1"
end subroutine sub1 
{% endhighlight %}

{% highlight fortran %}
! sub2.f90
subroutine sub2()
    print *, "In sub2"
end subroutine sub2
{% endhighlight %}

通过共同编译这三段代码，我们可以得到执行文件并最后运行。


    $ gfortran main.f90 sub1.f90 sub2.f90 -o main.exe
    $ main.exe

<br/>

我们也可以分开编译这三段程序，先产生目标文件，

    $ gfortran -c main.f90 sub1.f90 sub2.f90 

然后连接得到执行文件，并将结果写入out.txt里面。
    
    $ gfortran main.o sub1.o sub2.o -o main.exe
    $ main.exe > output.txt

我们时常需要修改某个子程序, 但是我们不希望花时间重新编译没有被修改的程序。因此，如果我们修改了sub2.f90, 我们只需要重新翻译sub2.f90就可以了。

    $ gfortran -c sub2.f90

同样的， 连接三个目标文件产生执行程序。

### 写Makefile

写Makefile可以大大简化以上的过程，可以更加快捷的更新编译结果，以及更新最终的执行程序。在尝试写Makefile之前，我们首先要确认已经安装了make执行程序。可以安装mingw，并将bin路劲添加到系统路径里面。为了后面的尝试，我们先把以.o以及.exe文件删除。

    $ rm -f *.o *.exe

Makefile的写法如下，按最后被执行的顺利从上往下写。即，后被执行的命令写在上面，而先被执行的写在下面，

{% highlight makefile %}
# Makefile
output.txt: main.exe
    ./main.exe>output.txt

main.exe: main.o sub1.o sub2.o 
    gfortran main.f90 sub1.o sub2.o -o main.exe

main.o: main.f90
    gfortran -c main.f90

sub1.o: sub1.f90
    gfortran -c sub1.f90

sub2.o: sub2.f90
    gfortran -c sub2.f90
{% endhighlight %}

可以看到，每次执行都有两行组成。上面一行的冒号左边代表目标，冒号代表产生目标所依赖的文件。下面一行描述了产生目标的过程。例如，第一行说的是要产生out.txt需要先产生main.exe；第二行说的是由main.exe产生output.txt所执行的命令。

<br/>

例如，在输入
    
    $ make output.txt

之后，就产生了最终的结果。因为之前我们没有编译过任何一个子程序，所以这个make命令是完整的执行了Makefile里面所有命令并得到目标文件的。

<br/>

我们可以简化Makefile的形式，例如可以编译过程合写为一个统一形式，即


{% highlight makefile %}
# Makefile
output.txt: main.exe
    ./main.exe>output.txt

main.exe: main.o sub1.o sub2.o 
    gfortran main.f90 sub1.o sub2.o -o main.exe

%.o: %.f90
    gfortran -c $<
{% endhighlight %}

我们也可以通过运用宏观变量并且引用他们的方式来进一步简化Makefile以及避免不必要的错误。


