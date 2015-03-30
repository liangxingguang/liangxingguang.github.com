---
layout: default
title:  Markdown语法学习
---
--------
##什么是markdown

>Markdown是一个将文本转化为HTML的工具，Markdown 的语法全由一些符号所组成，这些符号经过精挑细选，其作用一目了然。
--------
##标题
>Markdown提供两种方式(Setext和Atx)来显示标题
>**语法**
    Setext方式
    标题1
    ===========

    标题2
    -----------

    Atx方式
    #标题1
    ##标题2
    ######标题6

*效果*

标题1
===========

标题2
-----------

Atx方式
----
#标题1
##标题2
######标题6
-----

##列表

无序列表用*,+或-后面加上空格来表示
>**语法**
>   
>* Item1
>* Item2
>* ttem3
>
>+ Item1
>+ Item2
>+ Item3
>   
>- Item1
>- Item2
>- Item3
*效果*

* Item1
* Item1
* Item1

+ Item1
+ Item1
+ Item1

- Item1
- Item1
- Item1

---------
##代码区域
行内代码使用反斜杠\`表示.
代码段落则是在每行文字前加4个空格或者一个缩进符表示
**语法**
>\```
>int main(){
>   printf("hello markdown\n");
>   return 0;
>}
>\```
>   int main(){
>       printf("hello markdown\n");
>       return 0;
>   }

*效果*
```
int main(){
    printf("hello markdown\n");
    return 0;
}
```

    int main(){
        printf("hello markdown\n");
        return 0;
    }

-------

##强调

**语法:**
>单星号=\*斜体\*
>单下划线=\_斜体\_
>双星号=\**加粗\**
>双下划线=\__加粗\__

*效果:*

单星号=*斜体*
单下划线=_斜体_
双星号=**加粗**
双下划线=__加粗__

----

##链接

Markdown支持两种风格的链接:*Inline和Reference*

**语法:**
>*Inline:以中括号标记显示链接文本，后面紧跟小括号包围的链接。如果链接有title属性，则在链接中使用*空格*加*title属性*.
>Reference：一般应用于多个不同位置使用相同链接。通常分为两个部分，调用部分为[链接文本][ref]；定义部分可以出现在文本中的其他位置，格式为[ref]: http://some/link/address (可选的标题)。
>*注：ref中不区分大小写*.
>
>这个是Inline\[实例\](www.baidu.com "百度")
>这个是Reference\[实例\]\[ref\].
>\[ref\]:www.baidu.com("百度")

*效果:*

这是一个Inline[实例](www.baidu.com "百度")
这是一个Reference[实例][ref]
[ref]:www.baidu.com("百度")

---

##图片

图片的使用方法基本上和链接类似，只是在中括号前加叹号。
*注：Markdown不能设置图片大小，如果必须设置则应使用HTML标记<img>.*





