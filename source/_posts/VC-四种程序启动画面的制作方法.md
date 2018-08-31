title: VC++四种程序启动画面的制作方法
date: 2015-10-15 19:22:47
tags: C++
---
<body>
<a name="1960"/>

<div>
<div style="word-wrap: break-word; -webkit-nbsp-mode: space; -webkit-line-break: after-white-space;">
使用启动画面一是可以减少等待程序加载过程中的枯燥感（尤其是一些大型程序）；二是可以用来显示软件名称和版权等提示信息。怎样使用VC++制作应用程序的启动画面呢？本文提供四种方法，前三种适用于基于文档的应用程序，第四种适用于基于对话框的应用程序。<br/><br/>
  1.利用组件库中的Splash Screen组件实现<br/><br/>
  (1)用Photoshop等制作启动画面图像，保存为bmp格式。<br/><br/>
  (2)用Appwizard建一个基于单文档的工程Splash。<br/><br/>
  (3)在资源中插入位图资源<br/><br/>
  打开VC++的资源编辑器，用鼠标右键单击Resources文件夹，选择Import命令，插入所制作的位图。如果位图超过256色，VC会弹出一个对话框，提示位图已经插入但不能在位图编辑器中显示，确定即可。将位图ID改为IDB_SPLASH。<br/><br/>
  (4)添加Splash Screen控件<br/><br/>
  ①选择菜单“project”/“Add To Project”/“Conponents and Controls”打开对话框，在列表框中双击“Visual C++ Conponents”选项，选择“Splash Screen”控件，然后单击“Insert”。<br/><br/>
  ②确认或修改类名和位图资源ID，单击OK确认。<br/><br/>
  ③编译、连接，漂亮的启动画面就显示出来了。<br/><br/>
  (5)如果需要改变启动画面的停留时间，就修改SetTimer()函数的第二个参数，默认是750 毫秒。该函数所在位置：<br/><br/>
int CSplashWnd::OnCreate(LPCREATESTRUCT lpCreateStruct)<br/>
{<br/>
...<br/>
   // Set a timer to destroy the splash screen.<br/>
   SetTimer(1, 750, NULL); //修改第二个参数以调整画面停留时间<br/>
   return 0;<br/>
}<br/><br/><br/><br/>
2.利用无模式对话框显示启动画面<br/><br/>
(1)用Appwizard建一个基于单文档的工程Splash。<br/><br/>
  (2)导入用作启动画面的图片，更改ID为IDB_SPLASH。<br/><br/>
  (3)新建一个对话框，在其中添加启动画面。<br/><br/>
  在资源中新建一个对话框，创建对话框类CSplashDlg。在对话框中添加一个Picture控件，打开其“Properties”对话框，选General，在Type下拉列表中选择Bitmap，在Image下拉列表中选前面导入的位图资源ID值：IDB_SPLASH。<br/><br/>
  (4)修改对话框的显示效果<br/><br/>
  ①调整对话框大小，去掉两个自动生成的按钮，并在“Properties”的“Styles”页中去掉对Title bar的选取；<br/><br/>
  ②选中图像，调整大小使之适应对话框的可编辑区，修改其“Properties”的“Styles”<br/><br/>
  使之居中。<br/><br/>
  (5)在CMainFrame类的OnCreate()函数中添加创建、显示并销毁无模式对话框的代码。<br/><br/>
#include “SplashDlg.h” //加到MainFrm.cpp文件的头文件调用部位<br/>
int CMainFrame::OnCreate(LPCREATESTRUCT lpCreateStruct)<br/>
{<br/>
CSplashDlg *dlg = new CSplashDlg(this);<br/>
dlg-&gt;Create(CSplashDlg::IDD,this); //创建对话框<br/>
dlg-&gt;ShowWindow(SW_SHOW); //显示对话框<br/>
dlg-&gt;UpdateWindow();<br/>
Sleep(2000); //画面显示停留时间，单位为毫秒<br/>
…<br/>
dlg-&gt;DestroyWindow(); //销毁对话框<br/>
return 0;<br/>
}<br/><br/><br/><br/>
  3.通过发送消息显示和销毁启动画面<br/><br/>
  ①重复方法二的步骤1至步骤4。<br/><br/>
  ②使用Class Wizard为CMainFrame类添加消息响应函数WM_TIMER。<br/><br/>
  ③修改代码，通过发送WM_TIMER消息启动和销毁启动画面<br/><br/>
  1）定义对话框类的变量<br/><br/>
在MainFrm.h文件头部添加#include &quot;SplashDlg.h&quot;，并在CMainFram类的定义中加上公用变量CSplashDlg *Splash。<br/><br/>
  2）添加计时器消息相应函数代码<br/><br/>
void CMainFrame::OnTimer(UINT nIDEvent)<br/>
{<br/>
if(Splash-&gt;IsWindowVisible()){<br/>
Splash-&gt;SetActiveWindow(); //把启动画面设置为当前活动窗口<br/>
Splash-&gt;UpdateWindow();<br/>
Sleep(2000); //修改此处可更改画面显示时间<br/>
Splash-&gt;SendMessage(WM_CLOSE); //关闭对话框<br/>
}<br/>
else{<br/>
SetActiveWindow();<br/>
KillTimer(1) ; //清除WM_TIMER事件<br/>
}<br/>
}<br/><br/><br/><br/>
  3）修改框架生成函数OnCreate()<br/><br/>
int CMainFrame::OnCreate(LPCREATESTRUCT lpCreateStruct)<br/>
{<br/>
SetTimer(1,0,NULL); //添加ID为1的WM_TIMER事件<br/>
Splash=new CSplashDlg();<br/>
Splash-&gt;Create(IDD_DIALOG1);<br/>
Splash-&gt;ShowWindow(SW_SHOW);<br/>
…<br/>
}<br/><br/><br/><br/>
  4.制作基于对话框的应用程序启动画面<br/><br/>
  以上几种方法都不能给基于对话框的应用程序做启动画面，下面介绍一种方法给基于对话框的应用程序做启动画面。基于对话框的应用程序没有主框架，因此不能采用前面几种方法制作启动画面。不过我们可以把方法一建立起的启动画面文件移植过来，然后，对程序进行一些修改。<br/><br/>
  (1)参照方法一建立基于单文档的工程Splash。<br/><br/>
  (2)建立基于对话框的工程Cover。<br/><br/>
  (3)文件移植<br/><br/>
  ①将Splash1.cpp 和Splash1.h 两个文件从方法一建立的Splash工程拷贝到Cover工程中，并且分别加入到Source Files和Header Files中；<br/><br/>
  ②导入位图文件到工程的资源中，改ID为IDB_SPLASH。<br/><br/><br/><br/>
  (4)修改代码，实现启动画面的调用<br/><br/>
  ①添加CCoverApp 的InitInstance() 函数代码<br/><br/>
#include &quot;Splash1.h&quot; //加在Cover.cpp文件的头文件调用部位<br/>
BOOL CCoverApp::InitInstance()<br/>
{<br/>
CCommandLineInfo cmdInfo;<br/>
ParseCommandLine(cmdInfo);<br/>
CSplashWnd::EnableSplashScreen(cmdInfo.m_bShowSplash);<br/>
...<br/>
}<br/><br/><br/><br/>
  ②使用ClassWizard 添加OnCreate() 函数到对话框类CCoverDlg中，并修改代码#include &quot;Splash1.h&quot; //加在CoverDlg.cpp文件的头文件调用部位<br/><br/>
int CCoverDlg::OnCreate(LPCREATESTRUCT lpCreateStruct)<br/>
{<br/>
...<br/>
CSplashWnd::ShowSplashScreen(this); //显示启动画面<br/>
...<br/>
}<br/><br/><br/><br/>
  说明：启动画面停留时间的修改同方法一。<br/><br/>
  5.结束语<br/><br/>
  正如前面提过的，运用好启动画面可以给使用者留下一个强烈的印象，起到很好的宣传作用，以上程序均在Visual C++ 6.0、Windows2000调试通过。<br/><br/>
  参考文献：<br/><br/>
  1．胡哲源. 掌握Visual C++—MFC程序设计与剖析. 清华大学出版社，2001<br/></div>
</div></body>