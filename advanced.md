# 用Visual Studio Code进行Wallaby编程  
## 进阶篇  

* 在基础篇中，介绍了借助Visual Studio Code进行快速编程的方法，解决了函数难记的问题。但是它比较麻烦的是还需要复制粘贴代码到网页版程序中进行编译才能在机器人中运行。

* 在进阶篇中，你将学会直接远程登入Wallaby的Linux系统中进行编程的方法。

***本篇难度较大，要求有一定linux基础。***

### （一）安装OpenSSH连接Wallaby 
OpenSSL软件的下载地址：  
https://github.com/PowerShell/Win32-OpenSSH/releases  
或者  
https://sourceforge.net/projects/sshwindows/  

1. 安装openSSL  
![下载VSCode](/img/17.png)  

2. 安装好OpenSSH后，可以在CMD命令行中输入：ssh root@192.168.124.1登入Wallaby的linux系统。
![下载VSCode](/img/18.png)  

3. Wallaby网页版编程的源码存放在一个指定的目录中，该目录路径为“/home/root/Documents/KISS/Default User/”，用Linux命令进入其中查看目录结构，和网页上的工程是相对应的。
![下载VSCode](/img/19.png)  


### （二）Wallaby程序的编译运行   
1. 了解一下“工程目录”
![下载VSCode](/img/20.png) 

2. 编译程序  
进入src目录，执行命令“gcc -lwallaby -I ../include -o ../bin/botball_user_program main.c”可以把src里的代码编译成可执行程序，可执行程序存在bin目录下，名为“botball_user_program”。  
![下载VSCode](/img/21.png) 

3. 运行程序  
进入bin目录，执行“./botball_user_program”命令可以运行程序。  
![下载VSCode](/img/22.png)  

### （三）使用Visual Studio Code进行远程编程  
#### （1）安装Remote VSCode插件  
1. 下载插件![下载VSCode](/img/23.png)  

2. 完成插件的安装后，在Visual Studio Code中单击“文件”菜单，选择“首选项”，选择“设置”。
![下载VSCode](/img/24.png)  

3. 在弹出的设置页中，输入“remote”搜索插件相关的配置，然后相应地设置监听地址（127.0.0.1）和端口（52698）。
![下载VSCode](/img/25.png)  


#### （2）安装Remote VSCode插件以后，按以下步骤进行Wallaby端的配置。
1. 到[rmate官方地址](https://github.com/aurora/rmate)下载最新版本的rmate文件，它是一个bash脚本。  
![下载VSCode](/img/26.png)  

2. 在cmd窗口中使用命令上传rmate文件到Wallaby中。  
命令如：scp E:\rmate root@192.168.124.1:/usr/local/bin/

3. 在cmd中使用命令ssh root@192.168.124.1登入Wallaby的linux系统，并用chmod命令设置rmate权限。

![下载VSCode](/img/27.png)  

#### （3）按以下步骤测试是否能正常使用Remote VSCode插件进行远端编程。
1. 按F1键，然后在弹框中输入“remote”。选择“Start Server”，启动Remote服务。  
![下载VSCode](/img/28.png)  

2. 在终端窗口中输入：ssh -R 52698:127.0.0.1:52698 root@192.168.124.1。  
![下载VSCode](/img/29.png)  

3. 登录Wallaby的linux后，输入命令：rmate -p 52698 /home/root/Documents/KISS/Default\ User/test/src/main.c

4. 这时就可以看见VSCode中弹出代码了。

### （四）打造快速开发环境  

前面讲述的都是原理，具体实现的代码分别写在“bb.bat、bbl、bbp、bbr”四个文件中，各位不妨看看它们的代码。现在开始讲述如何快速搭建开发环境，所需要的文件[bb.bat](/src/bb.bat)、[bbl](/src/bbl)、[bbp](/src/bbp)、[bbr](/src/bbr)请自行下载。

1. 将附件中的bb.bat文件复制到C:\Windows目录下。这时就能在VSCode的终端窗口中使用bb命令连接Wallaby。
![下载VSCode](/img/30.png)  

2. 用scp命令上传附件中的bbl、bbp、bbr文件到Wallaby的/usr/local/bin/目录中。这三个文件是bash脚本程序，他们的作用是：bbl——列出有工程的名称；bbp——打开c代码进行编程；bbr——编译并运行程序。  

上传文件的命令如下：  
```
scp e:\bbp root@192.168.124.1:/usr/local/bin  
scp e:\bbr root@192.168.124.1:/usr/local/bin  
scp e:\bbl root@192.168.124.1:/usr/local/bin  
```
![下载VSCode](/img/31.png)  


3. 用chmod命令修改bbl、bbp、bbr文件权限。  

命令如下：  
```
chmod 777 /usr/local/bin/bbp
chmod 777 /usr/local/bin/bbr
chmod 777 /usr/local/bin/bbl
```
![下载VSCode](/img/32.png)  

4. 复制HelloWorld作为新建工程的模板。  

命令如下：  
```
cp -rf /home/root/Documents/KISS/Default\ User/HelloWorld/ /home/root/template
```

演示如下：  
* 使用“bb”命令连接botball，并使用“bbl”命令列出Botball中的工程。  
![bb and bbl](/show/02.gif)  

* 使用“bbp”命令编程，代码将直接显示在VSCode中，保存代码将自动更新Wallaby中的代码。  
![bbp](/show/03.gif)  

* 使用“bbp”命令，新建botball工程。  
![bbp new project](/show/04.gif)  

* 远程运行botball工程。  
![bbr](/show/05.gif)  