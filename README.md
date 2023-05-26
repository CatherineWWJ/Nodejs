# Nodejs概念

> 开源的、跨平台的js运行环境
>
> 通俗解释：一款应用程序 / 软件，可以运行js

# 作用

## 1.开发服务器应用

服务器：可以理解为一个配置比较高的计算机

网页构建：html结构 + css样式 + js交互效果

流程：服务器可以保存我们写好的这些网页，然后用户通过url向服务器请求，服务器再将这些资源返回给浏览器，之后浏览器对页面进行解析，用户就可以看到这些网页了~

nodejs就运行在服务器端！！

## 2.开发工具类应用

例如：webpack、vite、babel

## 3.开发桌面端应用

vscode代码编辑工具

figma设计工具

postman接口测试工具

依赖结构如下：

![image-20230526150113662](D:\study\FrondEnd\Nodejs\README.assets\image-20230526150113662.png)

# 下载

LTS：long time service长期维护的版本

#  CMD常用命令

C盘切换到D盘：d:

看到D盘下的内容：dir

切换工作目录：cd xxx

当前目录：.

上一级目录：..

![image-20230526151535942](D:\study\FrondEnd\Nodejs\README.assets\image-20230526151535942.png)

查看当前目录下的所有文件（包括子目录）：dir \s

使用node运行js文件：node xxx.js

# 注意点

在nodejs中不可以使用DOM和BOM的api

![image-20230526152610684](D:\study\FrondEnd\Nodejs\README.assets\image-20230526152610684.png)

![image-20230526152629879](D:\study\FrondEnd\Nodejs\README.assets\image-20230526152629879.png)

![image-20230526152811377](D:\study\FrondEnd\Nodejs\README.assets\image-20230526152811377.png)

这些在nodejs中都不行~

![image-20230526153027969](D:\study\FrondEnd\Nodejs\README.assets\image-20230526153027969.png)

这些在nodejs中是可以执行的~

nodejs中的顶级对象是global，也可以用globalThis访问顶级对象

# Buffer

alloc：对旧的数据进行了归零清空

单个元素的查看：

![image-20230526154657118](D:\study\FrondEnd\Nodejs\README.assets\image-20230526154657118.png)

toString(2)：十进制转二进制

补充：

![image-20230526155031289](D:\study\FrondEnd\Nodejs\README.assets\image-20230526155031289.png)

# 计算机基本组成

CPU：中央处理器，是整个计算机运算和控制的中心

内存：存储数据的介质

硬盘

![image-20230526155346985](D:\study\FrondEnd\Nodejs\README.assets\image-20230526155346985.png)

主板：一块大的集成电路板，主板上有很多的插槽，上面的一些元器件都是通过插槽和主板连接在一起的

显卡：负责处理视频信号的

![image-20230526155615506](D:\study\FrondEnd\Nodejs\README.assets\image-20230526155615506.png)

![image-20230526155820630](D:\study\FrondEnd\Nodejs\README.assets\image-20230526155820630.png)

# 程序运行的基本流程

操作系统：一种应用程序，用来管理和调度硬件资源

装系统：将操作系统的程序安装到硬盘里面

计算机启动的基本过程：

1. 将windows相关的程序文件载入到内存中，cpu就可以去运行了
2. cpu执行的过程中发现有视频信号，需要在显示器呈现，就会交给显卡处理，处理完后交给显示器呈现
3. cpu执行的过程中发现有声音信号，需要播放，就会交给声卡处理，处理完后由外部的播放设备进行播放

程序运行的基本过程：

1. 应用程序载入内存，cpu去内存中读取指令并执行
2. cpu执行的过程中发现有视频信号，需要在显示器呈现，就会交给显卡处理，处理完后交给显示器呈现
3. cpu执行的过程中发现有声音信号，需要播放，就会交给声卡处理，处理完后由外部的播放设备进行播放

![image-20230526160754381](D:\study\FrondEnd\Nodejs\README.assets\image-20230526160754381.png)

# 进程和线程

进程：可以理解为进行中的程序，也是程序的一次执行过程

查看进程：任务管理器

线程：是一个进程中执行的一个执行流

关系：一个线程是属于某个进程的

查看当前进程所拥有的所有线程：pslist -dmx 进程PID

# fs模块

模块也可以理解为API

异步与同步：

![image-20230526162621424](D:\study\FrondEnd\Nodejs\README.assets\image-20230526162621424.png)

JS主线程会将磁盘写入给另一个线程，然后主线程继续执行后续的代码，IO线程执行完后会将回调函数放在任务队列中，等JS主线程执行完之后再执行IO线程的回调函数。

![image-20230526163417329](D:\study\FrondEnd\Nodejs\README.assets\image-20230526163417329.png)

注意：writeFile原本会覆盖写入，但是加入可选项，就可以实现追加写入

流式写入：与文件之间建立通道

关闭通道：ws.close()

二进制文件读取字符串：data.toString()

文件流式读取：就是文件按照一小块一小块加载进内存的，而不是一整个全部加载到内存中读取

![image-20230526215257622](D:\study\FrondEnd\Nodejs\README.assets\image-20230526215257622.png)

实现copy文件：其中一种方式，理解即可

![image-20230526220227834](D:\study\FrondEnd\Nodejs\README.assets\image-20230526220227834.png)

删除文件：

node14.4新版本引入的一个方法：rm			fs.rm(path, err=>{})

同理也有rmSync方法

创建文件夹 / 目录：mkdir

![image-20230526221131273](D:\study\FrondEnd\Nodejs\README.assets\image-20230526221131273.png)

> 目录不使用紧凑模式：vscode设置 --- compact --- 取消紧凑模式呈现文件夹

递归删除文件夹：推荐rm		不建议rmdir

查看文件状态：data.isFile()		data.isDirectory()

![image-20230526221937350](D:\study\FrondEnd\Nodejs\README.assets\image-20230526221937350.png)

linux系统下的根目录路径为： /

**相对路径的参照物**：不是当前js文件的路径，而**是命令行的工作目录**

# 学习进度：31