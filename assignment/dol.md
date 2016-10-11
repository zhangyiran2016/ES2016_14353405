## Lab2:DOL实例分析&编程 ##

### 实验任务 ###
1. 修改example2，让3个square模块变成2个, tips:修改xml的iterator
2. 修改example1，使其输出3次方数，tips:修改square.c

### 实验过程 ###

##### 1. 进入dol文件夹并编译dol，接着进入build/bin/mian 路径下，运行 example1 #####

    $ cd dol
    $ ant -f build_zip.xml all
    $ cd build/bin/main
    $ ant -f runexample.xml -Dnumber=1

![](http://i.imgur.com/93Z8Y1s.png)

example1 dot图：

![](http://i.imgur.com/8n3GQfO.png)

##### 2. 打开dol/examples/example1/src/square.c，将square_fire函数中的i = i * i修改i = i * i * i，并保存 #####

![](http://i.imgur.com/QX942y9.png)

##### 3. 将dol/build/bin/main文件夹中的example1整个文件夹删除 #####

##### 4. 进入dol文件夹并编译dol，接着进入build/bin/mian路径下，再次运行example1 #####

    $ cd
    $ cd dol
    $ ant -f build_zip.xml all
    $ cd build/bin/main
    $ ant -f runexample.xml -Dnumber=1

![](http://i.imgur.com/lc781Ez.png)

##### 5. 为区别原dot图，对example1各文件作如下修改： #####

首先进入dol/examples/example1/src，将square.c、square.h文件分别重命名为cubic.c、cubic.h，用记事本打开cubic.c、cubic.h、example1.xml、map_1.xml、map_3.xml，将其中所有的square改为cubic，并保存

* cubic.c

![](http://i.imgur.com/AeWTsZ5.png)

* cubic.h

![](http://i.imgur.com/hGUwyQF.png)

* example1.xml

![](http://i.imgur.com/A1ZfuEi.png)

![](http://i.imgur.com/bucBAiv.png)

* map_1.xml

![](http://i.imgur.com/hz2DAHI.png)

* map_3.xml

![](http://i.imgur.com/IrCaQmj.png)

修改后example1 dot图：

![](http://i.imgur.com/7bOfTDd.png)

##### 6. 运行example2 #####

    $ ant -f runexample.xml -Dnumber=2

![](http://i.imgur.com/QeBj4HM.png)

example2 dot图：

![](http://i.imgur.com/BrMYj2R.png)

##### 7. 进入dol/examples/example2，用gedit打开example2.xml，将变量N的值由3改为2，并保存 #####

![](http://i.imgur.com/74iXHEl.png)

##### 8. 同样，将dol/build/bin/main文件夹中的example2整个文件夹删除 #####

##### 9. 进入dol文件夹并编译dol，接着进入build/bin/mian路径下，再次运行example2 #####

    $ cd
    $ cd dol
    $ ant -f build_zip.xml all
    $ cd build/bin/main
    $ ant -f runexample.xml -Dnumber=2

![](http://i.imgur.com/5tJNHfj.png)

example2 dot图：

![](http://i.imgur.com/zJ2eAmv.png)

### 实验感想 ###

example1未修改前运行结果是0-19的平方，dot图中：generator产生0-19的整数（length为20，初始值为0），square对输入进行平方操作，consumer输出结果。
修改后，example1运行结果是0-19的立方，dot图中：cubic对输入进行立方操作。

example2未修改前运行结果是0-19的3次平方，即8次方，dot图中：square经过三次平方操作：square_0，square_1，square_2。
修改后，example2运行结果是0-19的2次平方，即4次方，dot图中：square经过两次平方操作：square_0，square_1。

这次实验完成的比较顺利。代码修改很简单，只改动了两行。为了让example1中平方操作和立方操作的dot图有所差别，对example1中的各个文件改动较多，比较繁琐。


