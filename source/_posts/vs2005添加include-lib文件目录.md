title: vs2005添加include lib文件目录
date: 2015-10-15 19:19:12
tags: C++
---
<body>
<a name="1987"/>

<div>
<div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;"><b>1. 添加编译所需要的 lib 文件</b><br/>
[解决方案资源管理器]“项目-&gt;属性-&gt;配置属性-&gt;连接器-&gt;输入-&gt;附加依赖项”里填写“winsock.lib”，多个 lib 以空格隔开。<br/>
（等同于“#pragma comment(lib, &quot;winsock.lib&quot;) ”语句）
<div><br/><b>2. 添加库（Libs）文件目录</b><br/>
方法 1：[解决方案资源管理器]“项目-&gt;属性-&gt;配置属性-&gt;连接器-&gt;常规-&gt;附加库目录”<br/>
方法 2：[菜单]“工具-&gt;选项-&gt;项目和解决方案-&gt;C++ 目录”，选择对应平台，然后添加所需“库文件”目录</div><div><br/><b>3. 添加包含（include）文件目录</b><br/>
方法 1：[解决方案资源管理器]“项目-&gt;属性-&gt;配置属性-&gt;C/C++-&gt;常规-&gt;附加包含目录”<br/>
方法 2：[菜单]“工具-&gt;选项-&gt;项目和解决方案-&gt;C++ 目录”，选择对应平台，然后添加所需“包括文件”目录</div><div><br/></div><div>http://blog.sina.com.cn/s/blog_79489160010145wb.html、</div></div>
</div></body>