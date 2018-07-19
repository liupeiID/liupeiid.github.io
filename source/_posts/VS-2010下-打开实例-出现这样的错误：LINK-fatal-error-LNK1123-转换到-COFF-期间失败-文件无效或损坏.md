title: "VS 2010下 打开实例 出现这样的错误：LINK : fatal error LNK1123: 转换到 COFF 期间失败: 文件无效或损坏"
date: 2015-10-15 19:25:47
tags: C++
---
<body>
<a name="1925"/>

<div>
<div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;"><div style="widows: 1;">解决方法如下：<br/>
项目\属性\配置属性\清单工具\输入和输出\嵌入清单：原来是“是”，改成“否”。</div><div style="widows: 1;">http://bbs.csdn.net/topics/390121452</div></div>
</div></body>