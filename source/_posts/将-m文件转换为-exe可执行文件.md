title: 将 .m文件转换为 .exe可执行文件
date: 2015-10-15 11:29:57
tags: MATLAB
---
<body>
<a name="1992"/>

<div>
<div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;">
第一步：安装C编译器。<br/>
在MATLAB的command下,<br/>
输入：mbuild -setup<br/>
输入：y<br/>
输入：2 （选VC6.0）<br/>
输入：y<br/>
完成。<br/>
第二步：在MATLAB下使用：mcc -m 文件名.m  ，将 .m 文件编译成 .exe 文件。<br/>
注意：<br/>
（1）如果有多个 .m文件，只需编译主函数，其他的被调用函数文件保持不变；<br/>
（2）其他的 .m文件必须与主函数在一个文件夹内，不要将其他 .m文件放入当前目录（主函数所在目录）的子文件夹中，可能会出现error。<br/>
（3）将每一个.m文件都改成函数形式，包括主函数（需在首尾加上 function mainGUI 和end），否则无法将其编译成 .exe文件（只有函数才可被编译为 .exe文件）。<br/>
（4）执行 mcc -m mainGUI.m ，出现warning:No matching builtin  function avilable ...，解决方法：将\MATLAB7\toolbox\compiler\deploy\matlabrc.m中的第81和82行注释掉：<br/>
      %  set_param(0,'PaperType',defaultpaper);<br/>
      %  set_param(0,'PaperUnits',defaultunits);<br/>
第三步：在目标计算机上安装MCRinstaller.exe。<br/>
(1)该文件位于matlab安装目录下的\toolbox\compiler\deploy\win32内,安装到任意目录下。<br/>
(2)将“MCRinstaller.exe的安装目录\runtime\win32”这个路径添加到目标计算机的环境变量path中，通常是自动加载。如果没有，也可手动安装，添加的方法是：右击“我的电脑”“属性”“高级”“环境变量”“添加”指定一个变量名，然后将上述路径复制到里面就可以了。<br/>
第四步：点击执行被编译的 .exe文件即可。
<div><a href="http://blog.sina.com.cn/s/blog_6c945ecb0100prs4.html">http://blog.sina.com.cn/s/blog_6c945ecb0100prs4.html</a></div><div><br/></div></div>
</div></body>