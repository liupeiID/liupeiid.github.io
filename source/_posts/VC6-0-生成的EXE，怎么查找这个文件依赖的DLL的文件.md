title: VC6.0++生成的EXE，怎么查找这个文件依赖的DLL的文件
date: 2015-10-15 19:21:30
tags: C++
---
<body>
<a name="1965"/>

<div>
<div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;"><br/>
有时我们需要知道一个程序依赖哪些动态链接库（DLL）文件。实际上，有很多方法可以做到。下面就是三种实现方法：<br/>
1. 通过  Visual Studio 的 Dependency Walker 工具。进入 Visual Studio 的命令行（以Visual Studio 2005 为例，通过“开始--&gt;所有程序--&gt;Microsoft<br/><br/>
Visual Studio 2005--&gt;Visual Studio Tools--&gt;Visual Studio 2005 Command Prompt” <br/>
打开），输入&quot;depends&quot;，回车，打开“Dependency Walker”。然后通过“File--&gt;Open”打开要查询的程序文件，Dependency Walker就会显示该程序文件所依赖的<br/><br/>
DLL 文件。<br/>
2. 通过金山清理专家。安装金山清理专家，运行要检测的程序，然后打开金山清理专的安全百宝箱中的进程管理器，选中要检测的程序文件名，就选中“显示加载到<br/><br/>
进程中的DLL”，就可以看到该进程所调用的 DLL 文件。<br/>
3. 借助 IceSword 软件。先运行要检测的程序，然后打开 IceSword 软件，点击进程，找到要检测的程序，并右击该程序名，在弹出的菜单中选择“模块信息”。这<br/><br/>
时，软件就会弹出“进程模块信息”对话框，这里显示了程序所信赖的 DLL 文件。<br/>
参考来源： http://163n.blog.163.com/blog/static/5603555220113151113287/<br/><br/>
了解 Visual C++ 应用程序的依赖项<br/>
你可以查看项目属性来确定应用程序依赖于哪些 Visual C++ 库。（打开项目的快捷菜单，选择“属性”以打开“属性页”对话框。）你还可以使用 Dependency<br/><br/>
Walker (depends.exe)，以更全面地了解依赖项。<br/>
在“属性页”对话框中，你可以检查“配置属性”下的各个页面，以了解依赖项。 例如，你的项目使用 MFC 库并且你在“配置属性”-&gt;“常规”页面上选择“MFC<br/><br/>
的使用”-&gt;“在共享 DLL 中使用 MFC”，则你的应用程序在运行时依赖于 MFC DLL，如 mfc100.dll。 如果你的应用程序不使用 MFC，而你在“配置属性”-&gt;“C/C<br/><br/>
++”-&gt;“代码生成”页面上选择“运行库”为“多线程调试 DLL (/MDd)”或“多线程 DLL (/MD)”，则它可能依赖于 CRT 库。<br/>
确定你的应用程序依赖哪些 DLL 的更全面的方式是：使用 Dependency Walker (depends.exe) 打开该应用程序。 你可以从 Dependency Walker 网站下载该工具。<br/>
通过使用 depends.exe，你可以检查静态链接到应用程序的 DLL 的列表及延迟加载的 DLL 的列表。 如果要获取动态加载的 DLL 的列表，可在 depends.exe 中使用<br/><br/>
分析功能测试应用程序，直到你确定所有代码路径都执行过。 在结束分析会话时，Depends.exe 将显示哪些 DLL 是动态加载的。<br/>
使用 depends.exe 时，请注意，一个 DLL 可能依赖于另一个 DLL 或特定版本的 DLL。 可以在开发计算机上或目标计算机上使用 Depends.exe。 在开发计算机上，<br/><br/>
Depends.exe 将报告支持应用程序所需要的 DLL。 如果在目标计算机上运行应用程序时遇到问题，可以将 depends.exe 复制到计算机上，然后在该工具中打开应用<br/><br/>
程序，以便确定是否有任何必要的 DLL 丢失或不正确。<br/>
在你知道应用程序所依赖的 DLL 后，就可以在将应用程序部署到另一个计算机时确定哪些 DLL 必须与其一起重新发布。 在大多数情况下，你不必重新发布系统 DLL<br/><br/>
，但是可能必须重新发布 Visual C++ 库的 DLL。 有关详细信息，请参阅确定要重新分发的 DLL。<br/>
https://msdn.microsoft.com/zh-cn/library/ms235265(v=vs.120).aspx<br/><br/>
部署示例：<br/>
https://msdn.microsoft.com/zh-cn/library/ms235285(v=vs.120).aspx
</div>
</div></body></