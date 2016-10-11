## Lab1: DOL开发环境配置

### 一、DOL框架描述 ###

The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

The DOL consists of basically three parts:

* DOL Application Programming Interface
* DOL Functional Simulation
* DOL Mapping Optimization

### 二、DOL安装笔记 ###

本次实验环境在linux下进行，使用虚拟机安装Ubuntu
#### 1. 安装一些必要的环境(ubuntu为例) ####
	$ sudo apt-get update
	$ sudo apt-get install ant
	$ sudo apt-get install openjdk-7-jdk
	$ sudo apt-get install unzip
#### 2. 下载文件 ####
	$ sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
	$ sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
#### 3. 解压文件 ####
	$ mkdir dol  //新建dol的文件夹
	$ unzip dol_ethz.zip -d dol  //将dolethz.zip解压到 dol文件夹中
	$ tar -zxvf systemc-2.3.1.tgz  //解压systemc
#### 4. 编译systemc ####
	$ cd systemc-2.3.1  //解压后进入systemc-2.3.1的目录下 
	$ mkdir objdir  //新建一个临时文件夹objdir
	$ cd objdir //进入该文件夹objdir
	$ ../configure CXX=g++ --disable-async-updates //运行configure

下图为运行configure之后的截图

![](http://i.imgur.com/Yh1wvsI.png)

	$ sudo make install //编译
	$ pwd //记录当前的工作路径(会输出当前所在路径，记下来，下面步骤有用)
编译完后文件目录如下：

![](http://i.imgur.com/rwbSv2S.png)

当前的工作路径为：

![](http://i.imgur.com/gLCLuno.png)

#### 5. 编译dol ####
进入刚刚dol的文件夹:

	$ cd ../dol 
修改build_zip.xml文件:

找到下面这段话，把YYY改成pwd的结果

（注意，对于64位系统的机器，lib-linux要改成lib-linux64）

> property name="systemc.inc" value="YYY/include"/

> property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/

然后是编译

	$ ant -f build_zip.xml all

若成功会显示build successful

试着运行第一个例子

	$ cd build/bin/main //进入build/bin/mian路径下
	$ ant -f runexample.xml -Dnumber=1

成功结果如图：

![](http://i.imgur.com/1HT9XQ2.png)

#### 6. 至此完成DOL的开发环境配置 ####

### 三、实验感想 ###
这次的配置实验只要跟着实验文档走就能比较顺利地完成，但比较麻烦的是用Markdown写实验报告。我选用的编辑器是MarkdownPad 2，虽然Markdown语法很简单，上手很快，但是添加图片比较麻烦，需要先将图片上传到图床中，再将生成的图片链接添加到插入图片的语法中。不过相较于word文档编辑，个人觉得Markdown更加好用。

