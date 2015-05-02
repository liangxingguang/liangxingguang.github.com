---
layout: default
title: vfork子进程中使用return挂掉的原因
---
---------  
今天在[酷壳](http://coolshell.cn)的时候，看到一篇有关于[vfork](http://coolshell.cn/articles/12103.html#more-12103)的子进程用return整个进程会挂掉的文章，故为此做一下笔记。  
##例子  
在博客中，给出的例子是如下:

```
#include <stdio.h>  
#include <stdlib.h>  
#include <unistd.h>  

int glob = 1;  
int  
main(void){
    int var;  
    var = 88;  
    pid_t pid;  
    if((pid = vfork()) < 0){  
        printf("vfork error\n");  
        exit(-1);  
    }else if(pid == 0){  
        var++;
        return 0;
    }
    printf("pid=%d, glob = %d, var = %d\n",getpid(),glob,var);
    return 0;
}     
```  
在编译运行这段代码时，程序会不断输出最后一个printf的内容，最后输出vfork error结束退出。而将return改成exit(0)则不会出现上述情况。这究竟是什么原因呢?  
##原因
主要原因是因为vfork产生的父子进程是共享内存数据。当子进程执行return时，此时子进程的main()函数就return,当函数return了，其程序的调用栈就改变了，由于vfork是共享内存数据，所以父进程的程序栈也被破坏了。(return会释放局部变量，弹栈，返回上级函数执行),而exit是直接退出，并没有破坏函数的栈，所以能顺利执行下去.





