---
title: ubuntu onedriver
date: 2018-07-20 20:38:23
tags: linux
---
**系统信息**：

- 操作系统：`Ubuntu 18.04`

  本教程通过安装开源社区的`onedrive-d`，实现在linux操作系统中将本地文件同步到微软`OneDrive`云存储。
    `onedrive-d`不仅支持`Ubuntu/Debian`，同时也支持`CentOS/Fedora/RHEL`。

**第1步**：废话不多说，直接从`github`下载安装

```
$ git clone https://github.com/xybu92/onedrive-d.git
$ cd onedrive-d
$ ./install.sh
```
  安装过程中，会自动安装必要的软件，例如`pip3`等但是安装需要`python-3`，不过`ubuntu`都会自带的，所以无须担心。

**第2步**：安装后，你会看到这样的消息：

```
onedrive-d installed successfully.
Please run command `onedrive-pref` to set up the program.
```
根据提示，在终端输入`onedrive-pref`进行初始化配置 ，如

```
u@rs:~/onedrive-d$ onedrive-pref 
Loading configuration ... OK
[2018-07-20 20:29:47,347] DEBUG: thread_mgr: started.
Setting up onedrive-d...
(STEP 1/4) Do you want to authorize sign in with your OneDrive account? [Y/n] y

You will need to visit the OneDrive sign-in page in a browser, 
log in and authorize onedrive-d, and then copy and paste the 
callback URL, which should start with 
"https://login.live.com/oauth20_desktop.srf".

The callback URL is the URL where the sign-in page finally goes blank.

Please visit the sign-in URL in your browser:

https://login.live.com/oauth20_authorize.srf?client_id=000000004010C916&scope=wl.skydrive+wl.
skydrive_update+wl.offline_access&response_type=code&redirect_uri=https%3A%2F%2Flogin.live.
com%2Foauth20_desktop.srf&display=touch&locale=en

Please paste the callback URL:
https://login.live.com/oauth20_desktop.srf?code=Mf922a696-9e63-551f-98c5-61c9d1c4c168&lc=1033
/usr/lib/python3/dist-packages/urllib3/connectionpool.py:860: InsecureRequestWarning: 
Unverified HTTPS request is being made. Adding certificate verification is strongly advised.
See: https://urllib3.readthedocs.io/en/latest/advanced-usage.html#ssl-warnings
  InsecureRequestWarning)
[2018-07-20 20:31:04,635] DEBUG: MainThread: config saved.
onedrive-d has been successfully authorized.
```

```
(STEP 2/4) Do you want to specify path to local OneDrive repository? [Y/n] y
Please enter the abs path to sync with your OneDrive (default: /home/u/OneDrive): 
The path "/home/u/OneDrive" does not exist. Try creating it.
[2018-07-20 20:31:39,905] DEBUG: MainThread: config saved.
Path successfully set.
```

```
(STEP 3/4) Do you want to change the numeric settings? [Y/n] n
Skipped.
```

```
(STEP 4/4) Do you want to edit the ignore list file? [Y/n] n
Skipped. You can manually edit "/home/u/.onedrive/ignore_v2.ini" at your convenience.

All steps are finished.
[2018-07-20 20:31:49,593] DEBUG: MainThread: config saved.
```
***第3步***：帮助

`$ onedrive-d --help`

```
Commands:
     start    Start the daemon.
     stop     Stop the daemon.
     restart  Stop then start the daemon.
     status   Get the status of the daemon.
```
终端输入

`$ onedrive-d start`

至此，你会在`home`文件夹下找到`onedrive`文件夹，里面已经同步了你的onedrive 文件。

REF: https://blog.csdn.net/skylark0924/article/details/80251753
