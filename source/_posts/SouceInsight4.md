---
title: Source Insight 4.0 破解和使用
date: 2019-10-21 21:44:45
tags: [图像处理]
---

图像格式及Matlab的格式转换
<!--more-->
转自博客：https://blog.csdn.net/xiaoxu2050/article/details/82752799

### Source Insight 4.0 破解安装
第一步：安装    安装sourceinsight4.0 （可从下文地址下载）
第二步：替换     用下文地址中的 sourceinsight4.0.exe 替换安装后路径下的 sourceinsight4.0.exe
第三步：破解     运行sourceinsight4.0，选择破解文件破解

安装：如果需要全部重新安装，请下载  完全安装包+破解exe+lisence 压缩包：
https://pan.baidu.com/s/1eSZtsbw            密码: 3kjj
解压密码: biu 
下载解压后先找到安装文件进行安装，然后用解压后的“source insight 4.0.exe”替换安装路径下的source insight 4.0.exe，然后运行SI4，在弹出的对话框中选择第三项并将下载的文件 si4.pediy.lic选中并“Next”即可破解！


![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_1.png)

![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_2.png)

![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_3.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_4.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_5.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_6.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_7.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_8.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_10.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_11.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_12.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_13.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_14.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_16.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_17.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_18.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_19.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_20.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_21.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_30.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_31.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_32.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_33.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_34.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_35.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_36.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_37.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_38.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_39.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_40.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_41.png)

![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_42.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_43.png)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_source_44 .png)



## 安装卸载附录： 
如果安装或者安装后提示有问题，请进行完全卸载后，再重装一遍即可。
完全卸载方式：
1、清除注册表信息：
“win ”+ R  或者  “开始” -> “运行”，输入“regedit”，回车；
在弹出的注册表管理器中，选择“编辑”-> “查找”->“source insight”，或按照下述路径展开：HKEY_CURRENT_USER -> software -> Source Dynamics -> Source Insight;
将该项下面的source insight 需要清除的对应版本项目选中，右键“删除“。
2、删除全局配置信息：
在 ./user/document/source insight 3.0/4.0 下的所有文件及该文件夹
 注意此处的路径可能不同  也可能是:“库”->“用户”(也可能是你的名字) -> 文档 -> source insight3.0/4.0
 或者  你上次安装的时候所指定的其他位置
Source Insight4.0软件打开C程序中文注释乱码的解决方法
更改Options—Preference—Files中最下面的Default encoding中程序默认的UTF-8改为System Default（windows ANSI）。
附录：source insight 安装序列号（如果以上没用）
SI3US-751793-52670
SI3US-205035-36448
SI3US-466908-65897
SI3US-368932-59383
SI3US-065458-30661
SI3US-759512-70207
SourceInsight4.0的使用
创建一个SI工程管理代码
整体思路：告诉SI要解析哪些文件 -> 告诉SI这些文件在哪 -> 告诉SI文件选好了，解析它吧 。
首先，这里演示的是C代码工程，其它编程语言也差不多。
在解析C代码工程时，你可能希望SI连 .CC 和 .S结尾的文件也一同解析。那么点击 option -> File Type Options -> C/C++ Source File，我们在右边添加 *.S;*.cc。这里 *号是通配符，用英文;号隔开。
 
                                                  代码类型设置

## 创建工程
选择我们的代码工程位置，比如我选择了 D:\linux-to-windows-share\target 这个目录，我的工程代码全在这个目录下（注意不是SI的工程目录），然后点击 OK 继续。

## 导入项目
点击Project->New Project。
点击Browse，选择你的源代码所在目录。
给新建的Source Insight工程取个名字，然后点击OK。
弹出窗口点击OK，然后点击Add Tree，添加目录结构下所有文件到工程。最后点击Close，项目就建立完成。
SynchronizeFile，双击Project Files窗口中的文件，即可打开文件，进行阅读或编辑。
新建一个项目
快捷键Alt+Shift+N可以打开新建项目对话框，然后根据提示填好项目存储位置，源文件位置等，然后会出现添加删除项目文件对话框，选中自己想要编辑和浏览的文件添加即可，这样就建好了一个项目。
添加和删除项目文件
（1）在添加删除文件前，可以先设置文件过滤器，菜单栏-选项-文档选项，就可以看到文件过滤器了，怎么设置应该是一目了然的。
（2）菜单栏-项目-添加或删除文件，即可打开添加和删除项目文件对话框。
同步文件 SynchronizeFile
快捷键Alt+Shift+S可以同步文件，同步文件后就可以自动找到源代码之间的依赖关系了（如：可以自动找到调用某个函数或变量的位置）
项目报告
菜单栏-项目-项目报告，获取当前项目的文件个数，代码行数等。
重建项目
菜单栏-项目-重建项目，重新同步代码依赖关系。
具体操作如下：
依次点击 Project -> new project ，弹出对话框分别是SI的 工程名字 和 工程目录，如：工程名QCA4020，目录名SI_Proj。



## 选择代码工程目录*
这一步，进一步确定你要添加哪些代码到你的SI工程中，如果你要添加 target 这个目录下的全部，就选中它，点击 Add Tree 就好。后面你要是增删文件，也在这里。添加好了，就点击 Close 吧。

解析代码选择
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
添加以后，解析它吧。这一步会把代码加到SI数据库中，使得后面查找、关联更快。解析过程有点慢，耐心等待吧。点击Project -> SynchronizeFile， 并选择1，3，4打钩（勾上会强制添加和解析），点击 start 。

解析代码
如果解析完了，你突然发现忘记添加某些文件了，或者本来不用添加的你却添加了。不要担心，点击 Project -> Add and Remove Project Files，再次进行添加删除，然后 再进行解析SynchronizeFile 操作才会生效。

添加和删除解析文件
解析完，点一下那个书本一样的图标（Project Sympol List），尝试一下，你的代码就出来：
 

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
SourceInsight 的窗口设置
这里对SourceInsight进行一些设置，你完全可以不用设置，默认就好。
选择主题：Option -> Visual Theme （选择你喜欢的）。
设置字体大小：Option -> Preference -> Colors & Fonts -> Style -> size 。
显示文件全路径：Option -> Preference -> Display ， 去掉 trim long path names with ellipes。
添加配置文件（别人配置好的）：Option -> Load configuration（前提是你下载了别人的配置文件）。
显示行号：view -> Line Numbers 。
使用技巧
如果要 搜索字符位置，选中该字体，点击 工具栏的R图标 或者 Ctrl + F。
在Project Window（默认右边）的对话框中输入文件名，可以搜索到文件。
 没有正确显示在右边的file list列表框
需要在View菜单下找到Panels级联菜单下的Project Windows，把它勾选上。
Source Insight4.0软件打开C程序中文注释乱码的解决方法
更改Options—Preference—Files中最下面的Default encoding中程序默认的UTF-8改为System Default（windows ANSI）。
高亮显示选中的单词
高亮显示：F8。取消高亮：再按一次F8。
效果如下：

打开Source Insight相关窗口
（1）打开Symbol Window。
View->Symbol Window。快捷键：Alt+F8。
（2）打开Context Window。
View->Panels->Context Window。
（3）打开Relation Window。
View->Panels->Relation Window
Source Insight窗口布局我一般设置如下：

窗口字体大小与样式设置步骤：
Preferences->Colors&Fonts->Set Panel Fonts and Colors。
这里设置只对上面窗口1：符号窗口（Symbol Window）和窗口4：项目文件夹浏览窗口（Project Folder Browser）有效，另外两个窗口无效。
窗口2：上下文窗口（Context Window）字体大小设置如下：
在面板内右击->Context Window Options->scaling。
窗口3：引用关系窗口（Relation Window）字体大小设置如下：
窗口内右击->Relation Window Options->Font。
Source Insight的7种窗口的使用。

1、文档窗口
（1）、修改窗口颜色属性：菜单栏-选项-参数-颜色标签，可以修改背景颜色、默认字体颜色、修改标记颜色等，如背景颜色改为护眼模式：R199 G237 B204。

（2）、Alt+Y打开文档类型选项窗口，修改字体显示大小、是否显示行号、解析语言选择、工程文件过滤、扩展tab键、是否显示符号窗口等。

扩充1：Source Insight可以定义风格，菜单栏-选项-风格，即可以打开风格窗口，可以新建一个风格或修改一个风格。风格可以继承（和C++继承差不多）。
扩充2：如何使用风格。当选中某种语言解析文档的时候，可以定义一些固定字符以不同的风格显示出来。菜单栏-选项-参数-语言标签，选中解析文档的语言，点击关键字按钮，打开语言关键字窗口，在样式这一栏选中一种风格，然后添加关键字即可。这样文档中这个关键字就以那种风格显示了。
扩充3：如何查看和修改符号（如函数名、变量等）的风格，右击该符号，选择风格，打开窗口就可以看到该符号的风格是什么，然后进行修改。
（3）、快速更名ctrl+'，选中某个函数名，然后按ctrl+'，弹出快速更名窗口，然后根据相应的选项，可以快速更换函数名。（包括函数的声明处，定义处，引用处等）。
（4）、F8，高亮
（5）、ctrl+左击，进入函数定义或变量声明处。
（6）、Alt+，：后退
（7）、Alt+.   ：前进
（8）、ctrl+g：调到固定行
（9）、Alt+左击拖动：可以进行列编辑
（10）、自动缩进：Alt+T打开文档选项窗口，点击自动选项，选中第三个smart缩进，并把后面的两个勾都去掉，这样配置比较好。可以尝试一下勾上的效果，然后和不勾的效果对比一下。

（11）、编码格式设置，设置完毕后需要重新打开文件进行浏览。

（12）、Ctrl+F打开查找界面，配置好查找选项，然后关闭查找界面，选中一个单词，按一次Shift+F3，然后只要按F3和F4即可进行查找上一个和下一个。
2、符号窗口
这个窗口是显示文档的符号的，那么文档内容哪些是符号呢，这个应该是看文档窗口是设置哪种语言来解析文档的。
（1）、Alt+F8：打开/关闭当前文档的符号窗口。
（2）、Alt+Y打开文档选项窗口，配置所有文档是否打开符号窗口。

（3）、右击符号窗口-符号窗口选项-符号类型，可以选择显示的符号种类。
（4）、右击符号窗口-符号窗口选项，可以修改字体、背景颜色等。
3、项目窗口
这个窗口可以使用各种模式来显示文件名、文件目录等。
（1）、右击窗口选项，修改字体或背景颜色、不显示文件大小、目录、日期等。
4、关联窗口
这个窗口用来显示文档中的符号在哪些地方进行了引用。如哪些地方调用了函数，或该函数调用了哪些函数等。关联窗口可以有好多个。
（1）、右击关联窗口-窗口属性，可以修改字体、背景颜色等。
（2）、右击关联窗口-新建窗口，则可以打开一个新的关联窗口。
（3）、关联窗口的功能修改，右击关联窗口-窗口属性，可以修改对应符号的关系类型，选择Reference，则该窗口显示调用该函数或变量的地方，选择calls，则该窗口显示该函数调用了哪些函数。

（4）、如何使用该窗口：选中某个函数或变量，关联窗口会自动显示对于内容，如果不想它自己变，就锁上，然后需要找的时候刷新。（锁定、刷新按钮应该可以看到吧）
5、上下文窗口
这个窗口一般配合关联窗口使用，单机关联窗口的某一项，可以自动在上下文窗口显示该项的上下文，双击上下文内容，则可以在文档窗口打开上下文。
（1）、右击窗口-属性，修改字体、背景颜色等。
6、剪辑窗口
这个窗口的作用相当于是定义了好多粘贴板的意思。一个剪辑相当于一个粘贴板。
（1）、右击窗口-属性，修改字体、背景颜色等。
（2）、新建、修改、删除一个剪辑。
（3）、如何使用新建的剪辑：菜单栏-编辑-粘贴自剪辑/拷贝到剪辑。
7、代码片段窗口
（1）、右击窗口-属性，修改字体、背景颜色等
（2）、可以自定义一些代码片段，使用时直接插入即可。
打开上下文窗口context window
在view / panels/ context window

三、自定义命令
菜单栏-选项-自定义命令，可以添加一条命令，定义该命令的名字、执行命令语句。
如何运行命令：可以将命令显示在菜单栏（参考第五点菜单分配）或者给命令定义一个快捷键（参考第六点键分配）。
望君举一反三。
1、定义使用gvim打开当前文档的命令，前提是要先安装一个gvim程序。
命令名：editWithGvim
执行命令："C:\Program Files\Vim\vim63\gvim.exe" --remote-silent +%l %f
备注：--remote-silent 是如果已经打开了对应文件，就不会打开第二次，而是在已经打开的文件里跳转到对应行；%l 是当前行；%f是当前文件。
2、在资源管理器中显示当前文档，即打开当前文档位置。
命令名：explorer
执行命令：explorer /select,%f
备注：不知道，再说吧。
四、宏的使用
宏语言是SourceInsight定义的一种可编程语言。安装好一个SourceInsight后，打开SourceInsight，可以看到有一个base项目。打开base项目，可以看到有一个Utils.em文件，该文件就是宏语言文件，在里面可以自己写一些宏，也可以新建一个.em文件写宏，或者下载一个别人写好的.em文件如quiker.em(lushengwen写的，用的人比较多)。新建的.em或别人的.em文件要加载到base工程中（如何加载：菜单栏-项目-添加/删除文件）。
如何调用宏：可以将宏显示在菜单栏（参考第五点菜单分配）或者给宏定义一个快捷键（参考第六点键分配）。
1、宏语言语法
这个再说
2、quiker.em的使用（从网络下载）
（1）、首先要把这个文件搞到手，然后将其加载到Base工程中，其次要定义一个快捷键调用quiker.em中的宏AutoExpand。quiker.em中写了那么多宏，为什么只调用AutoExpand宏就可以。因为调用AutoExpand宏后，AutoExpand会根据当前文本内容自动调用其他宏。一般情况下都用快捷键ctrl+enter调用AutoExpand宏。
（2）、输入文本config，然后执行AutoExpand，根据提示完成语言、姓名配置。
（3）、输入文本fu，然后执行AutoExpand，根据提示完成函数的注释。（在函数名的上一行执行）
（4）、输入文本if，然后执行AutoExpand，可以自动完成语法。其他类似。
（5）、输入文本file，然后执行AutoExpand，可以自动生成.c文件描述。
（6）、输入文本hdn，然后执行AutoExpand，根据提示完成.h文件宏定义。
（7）、在.c文件里输入hd，然后执行AutoExpand，可以自动生成.c文件对应的头文件。
（8）、后续补充
3、自己写的宏
（1）、自动注释，给这个宏定义一个快捷键，然后选中几行文本，执行快捷键，即可以进行注释与反注释操作。
macro MultiLineComment()
{
    hwnd = GetCurrentWnd()
    selection = GetWndSel(hwnd)
    LnFirst =GetWndSelLnFirst(hwnd)      //取首行行号
    LnLast =GetWndSelLnLast(hwnd)      //取末行行号
    hbuf = GetCurrentBuf()
    if(GetBufLine(hbuf, 0) =="//magic-number:tph85666031"){
        stop
    }
    Ln = Lnfirst
    buf = GetBufLine(hbuf, Ln)
    len = strlen(buf)
    while(Ln <= Lnlast) {
        buf = GetBufLine(hbuf, Ln)  //取Ln对应的行
        if(buf ==""){                   //跳过空行
            Ln = Ln + 1
            continue
        }
        if(StrMid(buf, 0, 1) == "/"){       //需要取消注释,防止只有单字符的行
            if(StrMid(buf, 1, 2) == "/"){
                PutBufLine(hbuf, Ln, StrMid(buf, 2, Strlen(buf)))
            }
        }
        if(StrMid(buf,0,1) !="/"){          //需要添加注释
            PutBufLine(hbuf, Ln, Cat("//", buf))
        }
        Ln = Ln + 1
    }
    SetWndSel(hwnd, selection)
}
五、菜单分配
菜单栏-选项-菜单分配，可以将自定义命令、宏等显示到菜单栏列表里。

六、健分配
菜单栏-选项-键分配，定义快捷键，可以将自定义命令、宏等定义一个快捷键。
七、配置的保存和载入
菜单栏-选项-载入配置或保存配置，可以把自己的配置保存下来，或者发给别人让别人使用。获取我的配置文件：http://pan.baidu.com/s/1pKViFHp。
八、布局使用
软件提供了四个布局的保存，当配置好一个界面布局后可保存到一个布局当中，这样可以方便切换软件布局。

九、文件名标签设置为最近的使用靠左显示

10、显示/去掉overview

附：代码格式化，自己调整，本来想上传配置文件的，我看还是算了，自己调整吧



面是SI4.0版本官网的使用说明介绍网页。
https://www.sourceinsight.com/doc/v4/userguide/index.html#t=Manual%2FFrontMatter%2FFrontMatter.html

第一用户界面
第二：功能和概念
1项目 2项目窗口
3符号和语言分析 4条件分析和预处理器支持
5名称片段匹配符号名称 6源代码管理
7文件类型 8浏览和分析
9语法格式和样式 10上下文窗口
11关系窗口 12代码片段
13剪辑窗口 14书签
15搜索和替换文本 16常用表达
17比较文件和目录 18与选择历史导航
19滚动和选择文本 20概述和折叠文本
21代码美化 22从项目源生成HTML
23文件编码 24文件缓冲区基础
25从崩溃中恢复 26命令行语法
27用户级命令 28自定义命令
29自定义的设置和配置 30视觉主题
31使用布局保存窗口排列 32保存和恢复工作区
33性能调整 34预定义的路径变量
35 Source Insight创建的文件
功能和概念->一项目
项目：
1项目功能 2在一个项目里面
3当前项目 4项目目录
5规范化的文件名称 6创建一个新项目
7将文件添加到项目 8从项目中删除文件
9使用主文件列表 10打开和关闭项目
11删除项目 12复制项目
13只读项目 14更改项目设置
15符号和项目 16同步项目文件
17基地项目 18创建项目的Web版本
19重建项目
① 项目功能：
● Source Insight项目有几个重要的特点：
● 一个项目逻辑上分组相关的文件。
● 当你想打开一个文件，你不必指定它的驱动器或目录。
● Source Insight维护一个符号数据库，其中包含有关项目中所有符号声明和引用的数据。
您可以使用Source Insight来快速定位符号及其引用。保存源文件时，符号数据库会自动
更新，以便Source Insight始终“知道”符号的位置。当文件在外部进行更改（例如通过
源代码管理系统）时，Source Insight将自动将这些文件与项目符号数据库同步。
请参阅：符号和语言分析。
● Source Insight可以在项目中显示符号关系，如调用树，引用树和类层次结构。
● Source Insight维护了一个参考索引，大大加快了项目范围内对符号引用的搜索速度。
在编辑和保存文件时，参考索引会逐步更新。
● 每个项目都有自己的会话工作区。当一个项目被打开时，所有的会话状态被恢复。
当一个项 目关闭时，所有打开的文件都关闭，工作区被保存。
② 在一个项目里面：
● 一个项目基本上由两部分组成：您的源文件和Source Insight维护的项目数据文件。

图3.1 Source Insight项目的组件
每个项目都包含一个指向源文件的列表文件路径。项目还包含由Source Insight维护的符号数据库。您的源文件由Source Insight和符号声明和定义进行分析，并且引用记录在符号数据库中。您只需将源文件添加到您的项目中; 您不必生成任何其他“标签”文件。Source Insight自动执行此操作。每个项目都有自己的会话工作区。工作区包含会话信息，例如打开的文件列表和窗口位置。





附简易使用说明：
Source Insight导入源代码流程如下：
1）打开Source Insight；
2）选择Project->New Project，填写工程的名字，工程文件存放路径，点击OK后即创建Source Insight工程相关文件(相应目录会生成*.PR等工程文件)；
3）不断Next，你会发现Add and Remove Project Files对话框，在左边列表中选择你的源代码所在的文件夹，然后点击Add Tree，将源代码中所有文件添加到新创建的Source Insight工程中(即添加到右边列表中)，添加完成后你可以关闭该对话框，点击Project->Rebuild Project,这时你的源代码中的所有源文件全部都同步到Source Inight工程中了，这时你就可以使用Source Insight阅读源代码了；
点击Project->New Project，就会出现以下界面

再New project name里面写一个项目名字，然后点击Browse，选择到你那个项目的文件夹，此次以我的一个项目为例：

点击确定，然后出现一直ok

直到出现这个界面


然后点击Add Tree，出现这个界面

点击确定，然后出现这个界面

，然后把这个界面关掉就加载了项目

然后点击右边操作栏中，下面被选中这个按钮

然后会弹出一个提示框，是否要将这些代码关联，确认，然后加载完就可以，此时出现的是所有识别的函数名的列表，然后点击第一个按钮，回到下面这个界面，显示的是文件代码

双击其中Main.cpp文件，出现这个界面

然后随便选择这个文件中一个函数，就可以在下面看到他的定义

下面查看这个函数的全部调用，右击这个函数，选择Lookup References

然后选择Search

如果有弹出下面的框，可以随便选择Replace还是Append

然后就出现下面的界面

阅读python代码
首先从http://www.sourceinsight.com/public/languages/下载Python的配置文件Python.CLF ，然后对SourceInsight作如下配置：
（1）选择Options > Preferences，单击Languages选项；
（2）单击import按钮，装载并导入Python.CLF；
（3）这时可以看到，左栏语言列表多了一项Python Language；
（4）单击Document Types按钮，打开文档选项对话框；
（5）添加Document Type为Python，File filter为“*.py”，Passer组中Language选项设置为Python Language；
（6）单击文档选项对话框的close按钮；
（7）单击Preferences窗口OK按钮，退出Preferences窗口，完成设置。

来源：https://blog.csdn.net/biubiuibiu/article/details/78044232
https://www.jianshu.com/p/adca6c2f94f6
https://blog.csdn.net/qq_39660930/article/details/77499455
https://baijiahao.baidu.com/s?id=1608656406591755295&wfr=spider&for=pc
https://zhuanlan.zhihu.com/p/32754019
https://www.sourceinsight.com/doc/v4/userguide/index.html#t=Manual%2FFrontMatter%2FFrontMatter.htm
https://zhuanlan.zhihu.com/p/36543793
---

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


