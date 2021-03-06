
#Relax 0.9.0.0

Relax 是为提高骑马与砍杀战团mod汉化效率而制作的一款工具软件。正如它的名字表示的那样，我希望你在使用它进行汉化工作时感受到前所未有的轻松愉快。

本文分为三部分，第一部分是本工具及mysql的安装和配置，第二部分是Relax的界面、功能和使用说明，第三部分是开发环境介绍和合作开发方法。

##软件安装和配置


##Relax 使用说明

###界面和功能

一个Mod的汉化是成千上万次的重复劳动，但除了翻译本身需要人脑，其他步骤其实都可以用计算机完成。汉化之所以繁琐，是因为汉化者在工作过程中需要将手从键盘换到鼠标，将眼睛从一个窗口换到另一个窗口，然后又把手和眼换回来，如此反复多次，注意力势必涣散，耐心势必耗尽，然后……就没有然后了。Relax的理念是简洁和轻松。它采用柔和护眼的豆绿色作为背景色，100%的视觉集中在一个大窗口，99%的文本输入集中在一个主工作区，不用自己加空格，懒得动手摸鼠标。工作效率只取决于你的思维和码字速度。

![](http://i.imgur.com/zjt592x.jpg)

自上而下，自左而右分别是文本显示区，原文显示区，副工作区，主工作区。每次在文本选择区选择一行，程序自动根据原文和缩写从数据库取出一条或0条参考译文（如果你已经向数据库里压入了一些项目的话），将其显示在副工作区。如果译文完全正确，你可以直接在副工作区按Enter提交译文，或者在除主、副工作区的其他区域按Ctrl+Enter提交；如果译文需要少量修改，你可以直接在副工作区修改译文（需要自己添加空格）然后提交；如果译文完全不能用或者没有译文，你可以在主工作区输入你的翻译，此时副工作区会同步显示加空格后的翻译，满意后在主工作区按Enter提交。请注意，副工作区是从属于主工作区的，任何主工作区的变化都会同步反应到副工作区，因此，当你决定在副工作区工作时，除非已经提交当前译文或者打算放弃当前译文，否则不要进入主工作区。其他快捷键在主工作区介绍中有详细说明。

提交并非保存，在退出程序前，请不要忘记将当前文件保存或者另存为其他文件。为了使用数据库功能，你应该在首次使用Relax时向数据库中添加一些项目。

1. 文本显示区：用于按条显示所打开文件的所有项目。

	![](http://i.imgur.com/MGcCgBB.jpg)
	
2. 原文显示区：用于显示文本显示区当前选择条目的原文。原文不可编辑

	![](http://i.imgur.com/MQg7G91.jpg)

3. 副工作区：用于显示加空格后的中文翻译和从数据库中读取的译文，同时也可以在此工作区编辑译文，主工作区的快捷键在此工作区可用。

	![](http://i.imgur.com/jSi41hH.jpg)

	副工作区功能：

	1. 每当文本显示区选中一行时，程序自动从数据库中取出可能符合要求的一条译文并显示在副工作区。
	
	2. 副工作区译文可编辑，可使用主工作区的快捷键。


4. 主工作区：使用者在此工作区输入译文。

	![](http://i.imgur.com/gsdmcE3.jpg)

	主工作区有以下功能：

	1. 对输入的译文即时加空格，并将其同步显示在副工作区中。
		
	2. 输完一条译文，确认副工作区译文无误后，按Enter键提交译文并将其显示在文本显示区中，同时自动跳到文本显示区下一行。
	 
	3. Ctrl+Z 撤销最近一次提交，并跳转到文本显示区相应行，Ctrl+Y 重做最近一次提交，并保持文本显示区当前行。
		
	4. 使用方向键控制文本显示区当前行，方向键Up和Down分别向上、下跳转一行，方向键Left和Right分别向上、下跳转五行。
	 
	通过组合使用以上快捷键，主工作区可以不借助鼠标完成所有文本翻译操作。

###数据库使用方法

####向数据库中添加项目


此功能的作用是将已经汉化mod的英文原文和中文译文一一对应按条存入数据库，以便在翻译新mod时使用数据库完成自动翻译。

使用此功能前需要做以下准备工作：

1. 准备英文原文文件夹：以英文模式进入游戏，然后alt+enter进入窗口模式，开一个新档，左上窗口依次选择【view】、【create language template】、【default】，此时在战团根目录下会生成一个new language文件夹，这个就是英文原文文件夹。
	
2. 准备译文文件夹：对于已经完全汉化的mod，你可以在mod下language文件夹中找到cns文件夹，此即译文文件夹。如果你只有未汉化完全的译文，也是可以使用的，程序会自动识别未翻译的条目，不会把这些条目压入数据库。
	
3. 注意，原文、译文文件夹里的文件可以不包括所有语言文件，但是两个文件夹里的文件数量、名称必须一一对应。
	

在Relax下的resources文件夹里有native_en和native_cns两个文件夹，分别是战团native的英文原文和译文，如果你想体验数据库的强大功能，现在就按以下步骤将native的原文和译文压入数据库。


在Relax菜单依次选择【Tools】、【Add dictionary】。

![](http://i.imgur.com/jSttbG0.jpg)

在en directory项和cns directory项分别选择或者键入英文原文、译文文件夹地址。

![](http://i.imgur.com/vNgsKo1.jpg)

点击OK后会显示进度条，视mod语言文件大小时间从10~30秒不等。

####利用数据库自动翻译

此功能的作用是将待翻译的英文原文或者半汉化译文与数据库所存记录一一对比，如有相同项则用已有译文替换原文。你可以用Relax下resources文件夹里的native_en作为英文原文，按以下步骤体验自动翻译的便利。

使用此功能前需要做以下准备工作：

1. 准备英文原文或者半汉化译文文件，英文原文获取方法如向数据库添加项目时一样。半汉化译文的概念是：Mod更新版本，增加或者删除了一些文本，导致当前版本的译文不堪使用。此时你需要在当前版本的译文下，以中文模式进入游戏，获取中英掺杂的半汉化文件。
	
2. 关于半汉化译文，有一点需要补充的是，你可以将当前版本的译文压入数据库，Mod更新版本后，通过自动翻译可以快速获取之前版本的译文。
		
在Relax菜单依次选择【Tools】、【Use dictionary】。
	
![](http://i.imgur.com/jpd0LuI.jpg)

在en directory项和 save directory项分别选择英文原文/半汉化译文、保存译文文件夹地址。

![](http://i.imgur.com/R8MxoZr.jpg)

点击OK后会显示进度条，视mod语言文件大小时间从10~30秒不等。


####日志文件log.log

#####使用notepad++转换文件编码

每次使用Relax，Relax会自动记录工作过程中遇到的错误并将错误信息保存在根目录下的日志文件log.log中，你可以通过日志提供的信息手动修改语言文件。

要使用日志功能，你需要一款能打开多种编码文本的编辑器。我推荐notepad++。它非常适合用来替代Windos的记事本打开csv文件，最重要的是它可以转换文件编码，而统一的文本编码对Relax来说是极其重要的。虽然我已经针对编码做了很多预防措施，但是如果你能在使用Relax前花点时间将原文、译文文件都转换成UTF8无BOM格式的话，那么Relax就能更好的完成工作。

notepad++ v6.6.7 下载地址：[http://notepad-plus-plus.org/download/v6.6.7.html](http://notepad-plus-plus.org/download/v6.6.7.html)

使用notepad++查看文件编码，此文件是utf8编码的，在Windows下这种编码格式的文件开头会有一个标记（即BOM)。我们需要将此文件的编码转换为utf8无BOM格式。

![](http://i.imgur.com/1ilnXam.jpg)

选择【转为UTF-8无BOM编码格式】、【保存】，即可。

如果你没有转码，可能会在日志文件里找到这样的错误（程序会自动忽略出错文本，继续执行）。

![](http://i.imgur.com/RSa2aBT.jpg)




#####使用日志纠正编码错误。

日志本来是用来调试程序的，但是你也可以通过它手动纠正原文、译文里的一些编码错误。有时候Mod作者会不小心在文本里添加错误编码的字符，导致文本无法读取。程序会自动忽略这些错误编码的条目，但是你可以根据日志文件的记录找到这些条目，删除错误编码的字符。注意，因为日志文件里存在异常编码，一些编辑器可能不能正常打开它。你最好安装notepad++，有备无患。

一个文本存在错误编码字符的例子：

![](http://i.imgur.com/tomTkaz.jpg)

每一条错误记录都会以类似形式记录在程序根目录下的*log.log*文件中，日志提供的信息有：
	
	1. 错误类型：'utf8' codec can't decode byte 0x96 in position 107: invalid start byte 表示0x96不是utf8编码的字符，不能像该条目中其他字符一样正常转码。
	2. 文件地址：E:\Github\translation\available source\潘德的预言\en\quick_strings.csv 表示该条目所在语言文件。
	3. 条目所在行：1847 实际打开文件查看时应该加1，是第1848行。
	4. 具体条目：qstr_Watch_the_horizon_tra|Watch the horizon traveller, you never know who you may stumble across out here ֠or who may stumble across you.

把该条目复制粘贴到这里可以看出here旁边有个奇异字符，手动进原文件删除它即可。

##### 开发

Relax是开源软件，你可以在Github上找到clone源码：[https://github.com/mirror-riddle/Relax](https://github.com/mirror-riddle/Relax)

1. python 2.7，需要安装wxpython3和pymongo
	* 安装wxpython3 Phoenix版本
		
		参考 http://wxpython.org/Phoenix/snapshot-builds/README.txt
		
	* 安装pymongo
	
		pip install pymongo

2. mongodb 3.2, 下载[mongodb](https://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/)
	
	下载并安装mongodb
	
	打开windows命令提示符，输入 md /data/db

4. 运行程序
	
	先启动mongodb: 双击C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe 这里假设mongodb安装在该目录C:\Program Files\MongoDB下）。
	python menu.py
	
5. 安装notepad++, 用于查看csv文件，可选。

#####bug提交

你可以在Relax的发布帖中提交BUG和建议，或者直接发到我的邮箱：hejinhj@foxmail.com