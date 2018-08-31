title: C/C++ language 指针教程
date: 2015-04-24 17:24:53
tags:
categories: 算法
---
<div>
<div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;">
// xx.cpp : 定义控制台应用程序的入口点。<br/>
//<br/><br/>
#include &quot;stdafx.h&quot;<br/>
#include &quot;iostream&quot;<br/>
using namespace std;<br/><br/>
int main( )<br/>
{<br/>
     cout&lt;&lt;&quot;C/C++ language 指针教程&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     cout&lt;&lt;&quot;指针、引用和取值&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     cout&lt;&lt;&quot;什么是指针？什么是内存地址？什么叫做指针的取值？指针是一个存储计算机内存地址的变量。在这份教程里“引用”表示计算机内存地址。从指针指向的内存读取数据称作指针的取值。指针可以指向某些具体类型的变量地址，例如int、long和double。指针也可以是void类型、NULL指针和未初始化指针。本文会对上述所有指针类型进行探讨。&quot;&lt;&lt;endl&lt;&lt;endl;<br/><br/>
     cout&lt;&lt;&quot;根据出现的位置不同，操作符 * 既可以用来声明一个指针变量，也可以用作指针的取值。当用在声明一个变量时，*表示这里声明了一个指针。其它情况用到*表示指针的取值。&quot;&lt;&lt;endl&lt;&lt;endl;<br/><br/>
     cout&lt;&lt;&quot;&amp;是地址操作符，用来引用一个内存地址。通过在变量名字前使用&amp;操作符，我们可以得到该变量的内存地址。&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     // 声明一个int指针<br/>
     int *ptr;<br/>
     // 声明一个int值<br/>
     int val0 = 1;<br/>
     // 为指针分配一个int值的引用<br/>
     ptr = &amp;val0;<br/>
     // 对指针进行取值，打印存储在指针地址中的内容<br/>
     int deref = *ptr;<br/>
     cout&lt;&lt;&quot;deref =&quot;&lt;&lt;deref&lt;&lt;endl&lt;&lt;endl&lt;&lt;endl;<br/><br/>
     //*******************************<br/>
     cout&lt;&lt;&quot;void指针、NULL指针和未初始化指针&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     cout&lt;&lt;&quot;一个指针可以被声明为void类型，比如void *x。一个指针可以被赋值为NULL。一个指针变量声明之后但没有被赋值，叫做未初始化指针。&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     int *uninit; // int指针未初始化<br/>
     int *nullptr1 = NULL; // 初始化为NULL<br/>
     void *vptr; // void指针未初始化<br/>
     int val = 1;<br/>
     int *iptr;<br/>
     int *castptr;<br/>
     // void类型可以存储任意类型的指针或引用<br/>
     iptr = &amp;val;<br/>
     vptr = iptr;<br/>
     cout&lt;&lt;&quot;iptr=&quot;&lt;&lt;iptr&lt;&lt;&quot; vptr=&quot;&lt;&lt;vptr&lt;&lt;endl;<br/>
     // 通过显示转换，我们可以把一个void指针转成<br/>
     // int指针并进行取值<br/>
     castptr = (int *)vptr;<br/>
     cout&lt;&lt;&quot;*castptr=&quot;&lt;&lt;*castptr&lt;&lt;endl;<br/>
     // 打印null和未初始化指针<br/><br/>
     cout&lt;&lt;&quot;nullptr=&quot;&lt;&lt;nullptr1&lt;&lt;endl&lt;&lt;endl&lt;&lt;endl;<br/>
     //cout&lt;&lt;&quot;uninit=&quot;&lt;&lt; uninit&lt;&lt;endl;<br/><br/>
     //*******************************<br/>
     cout&lt;&lt;&quot;指针和数组&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     cout&lt;&lt;&quot;C语言的数组表示一段连续的内存空间，用来存储多个特定类型的对象。与之相反，指针用来存储单个内存地址。数组和指针不是同一种结构因此不可以互相转换。而数组变量指向了数组的第一个元素的内存地址。&quot;&lt;&lt;endl&lt;&lt;endl;<br/><br/>
     cout&lt;&lt;&quot;一个数组变量是一个常量。即使指针变量指向同样的地址或者一个不同的数组，也不能把指针赋值给数组变量。也不可以将一个数组变量赋值给另一个数组。然而，可以把一个数组变量赋值给指针，这一点似乎让人感到费解。把数组变量赋值给指针时，实际上是把指向数组第一个元素的地址赋给指针。&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     int myarray[4] = {1,2,3,0};<br/>
     int *ptrArr = myarray;<br/>
     cout&lt;&lt;&quot;*ptrArr=&quot;&lt;&lt;*ptrArr&lt;&lt;endl&lt;&lt;endl&lt;&lt;endl;<br/>
     // 数组变量是常量，不能做下面的赋值<br/>
     // myarray = ptr<br/>
     // myarray = myarray2<br/>
     // myarray = &amp;myarray2[0]<br/><br/>
     //*******************************<br/>
     cout&lt;&lt;&quot;指针与结构体&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     cout&lt;&lt;&quot;就像数组一样，指向结构体的指针存储了结构体第一个元素的内存地址。与数组指针一样，结构体的指针必须声明和结构体类型保持一致，或者声明为void类型。&quot;&lt;&lt;endl&lt;&lt;endl;<br/>
     struct person {<br/>
          int age;<br/>
          char *name;<br/>
     };<br/>
     struct person first;<br/>
     struct person *ptrStruc;<br/>
     first.age = 21;<br/>
     char *fullname = &quot;full name&quot;;<br/>
     first.name = fullname;<br/>
     ptrStruc = &amp;first;<br/>
     cout&lt;&lt;&quot;age=&quot;&lt;&lt;first.age&lt;&lt;&quot; name=&quot;&lt;&lt;ptrStruc-&gt;name&lt;&lt;endl&lt;&lt;endl&lt;&lt;endl;<br/><br/>
     return 0;<br/>
}<br/><br/></div>
</div>