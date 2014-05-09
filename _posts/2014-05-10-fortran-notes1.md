---
layout: post
title: Fortran学习笔记1
description: "Write Makefile"
category: Study
tags: [Fortran,coursera]
comments: true
---
### Working with Multiple Files

Suppose we have such a long fortran code

{% highlight fortran %}
program demo
    print *, "In main program"
    call sub1()
    call sub2()
end program  

subroutine sub1()
    print *, "In sub1"
end subroutine sub1  

subroutine sub1()
    print *, "In sub1"
end subroutine sub1
{% endhighlight %}

We can split the code into three pieces, i.e.

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

and compile all the three together

    $ gfortran main.f90 sub1.f90 sub2.f90 -o main.exe

then, run the main.exe to get the result.

<br/>

We could also split into separate complile

    $ gfortran -c main.f90 sub1.f90 sub2.f90 

then link steps to write output to a text file.
    
    $ gfortran main.f90 sub1.f90 sub2.f90 -o main.exe
    $ main.exe > output.txt

In the second case, if we modify sub2.f90, we only have to re-compile sub2.f90,

    $ gfortran sub2.f90 -o main.exe

then link steps again.

### Write Makefiles

~~~
# Makefile

output.txt: main.exe
    main.exe > output.txt

main.exe:



~~~





