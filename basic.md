# 用Visual Studio Code进行Wallaby编程    
## 基础篇  
* Wallaby原版的编程是在网页中进行的，输入代码时没有代码的自动完成提示，加上Wallaby的函数库内容非常多，同学们难以记住。为了降低学习难度，改进编程体验，在此介绍使用开源的编程软件Visual Studio Code来编程的方法。  

* VsCode编程的效果演示如下：   
![基础篇演示](/show/01.gif)  


### （一）下载并安装Visual Studio Code  
VS Code官方网站：https://code.visualstudio.com/
![下载VSCode](/img/01.png)

下载并安装后，可以给它配置中文界面。配置中文界面的步骤如下：  
1. 左侧栏选择插件图标。
2. 在插件搜索框中输入“chinese”，搜索名为“Chinese（Simplified）Language Packfor Visual Studio Code”的插件，此插件即为中文语言包。
3. 选择绿色的“install”按钮安装中文包。  
![配置中文界面示意图](/img/02.png)  

4. 关闭并重新启动Visual Studio Code，就能看见中文界面了。  
![中文界面的VSCode](/img/03.png) 


### （二）配置Botball代码片段
1. “文件” > “首选项” > “用户代码片段”  
![VSCode代码片段首选项](/img/04.png)   

2. 在弹出的窗口中，选择“新建全局代码片段文件”。  
![新建全局代码片段文件](/img/05.png)   

3. 在弹出的对话框中，“文件名”框中输入botball，保存类型选择Code Snippets，然后单击“保存”按钮。  
![保存botball.code-snippets文件](/img/06.png)  

4. 这时会自动打开botball.code-snippets文件，初始状态下有一大段代码。  
![botball.code-snippets文件初始内容](/img/07.png)  

5. 里面介绍了代码片段的配置例子，根据该例子可以配置Wallaby的函数代码片段。我们把原来的配置代码重写，替换为如下的代码段，并保存botball.code-snippets文件。  
![botball.code-snippets文件初始内容](/img/08.png)  

#### 为了验证是否已经配置成功，可以新建一个文件试试效果：  
1. 新建一个空白文件。  
![新建空白文档](/img/09.png)  

2. 在新建的文件中输入“bb”，将会弹出一个代码提示框。
![代码提示](/img/10.png)  

3. 按键盘Enter键，就能在该文件中生成代码。  
![自动生成代码片段](/img/11.png)  

4. 将该文件保存为.c的文件（如main.c），就能看见代码着色了。  
![C语言文件代码着色](/img/12.png)  

5. 在代码提示框中，用鼠标单击后面的蓝色感叹号图标，可以弹出代码的说明框，让您清楚的看到代码片段和说明。  
![蓝色感叹号显示代码片段和说明](/img/13.png)  
![蓝色感叹号显示代码片段和说明](/img/14.png) 

#### 通过以上讲解，相信你已经知道代码片段的作用了，下面我们详细介绍代码片段的配置方法：
![botball.code-snippets文件初始内容](/img/08.png)  

1. 代码片段详解  

|代码|含义|
|:---:|:---:|
|prefix|输入的前缀|
|body|代码片段主体|
|description|代码片段描述|
  
![蓝色感叹号显示代码片段和说明](/img/15.png)  

2. body代码中的格式符

|格式符|含义|
|:---:|:---:|
|\\n|换行|
|\\t|左缩进|
|$1|光标的第一个位置|
|$2|光标的第二个位置。按<Tab>键会从光标的第一位置跳到第二位置|


#### 更多的样例请查看附件“[botball.code-snippets](/src/botball.code-snippets)”文件。


### （三）把代码复制到网页编程环境中使用  

![蓝色感叹号显示代码片段和说明](/img/16.png)  
