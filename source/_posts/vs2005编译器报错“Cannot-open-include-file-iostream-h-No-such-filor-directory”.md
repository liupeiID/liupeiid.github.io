title: "vs2005编译器报错“Cannot open include file: 'iostream.h': No such filor directory”"
date: 2015-10-15 19:17:04
tags: C++
---
<body>
<a name="1978"/>

<div>
<div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;">
//已验证<br/>
#include &lt;iostream.h &gt; 是VC6以前的写法。<br/>
改成<br/>
#include &lt;iostream &gt;<br/>
using namespace std;<br/><br/>
这个是标准库的写法。标准库把这些个文件都放到std这个namespace里面了
<div><br/></div><div>http://blog.sina.com.cn/s/blog_7050644f01011m4d.html</div></div>
</div></body></