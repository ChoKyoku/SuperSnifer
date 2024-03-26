# JavaBase Day01

## 1.Java介绍

### 1.1.1 什么是Java

Java是一门面向对象的编程语言，具有功能强大和简单易用两个特征。Java语言作为静态面向对象编程语言的代表，极好地实现了面向对象理论，允许程序员以优雅的思维方式进行复杂的编程。

<img src="Images\Day01\01.jpg" style="zoom:33%;" />

### 1.1.2  编程环境

#### 1.1.2.1  JDK

JDK(*Java Development Kit*) ，称为Java开发包或Java开发工具。是一个编写Java的Applet小程序和应用程序的程序开发环境。包括了Java运行环境(*Java Runtime Envrioment*) 以及一些Java工具和Java的核心类库(*Java API*)。

JDK发展至今，版本有很多，可以根据具体的需要而进行选择。

#### 1.1.2.2  JRE

JRE(*Java Runtime Envrioment*),JRE是为运行Java应用程序而设计的，它包含了Java虚拟机(JVM)和Java基础类库，是使用Java语言编写的程序运行所需要的软件环境。

JRE和JDK是有区别的，JDK是为了开发人员准备的，它里面包含了JRE以及额外的开发工具，比如编译器javac，调试器以及用于构建，测试和部署Java应用程序的软件

#### 1.1.2.3 安装JDK

由于JDK中包含了JRE，所以只要安装了JDK就会自动安装JRE，意味着既能开发Java程序，也能运行Java程序

本课程中使用的JDK11.0.21

JDK下载路径:https://www.oracle.com/jp/java/technologies/javase/jdk11-archive-downloads.html

![](Images\Day01\02.jpg)

安装操作具体步骤如下:

1.双击JDK安装文件进行安装

![](Images\Day01\03.jpg)

2.点击次へ进行安装

![](Images\Day01\04.jpg)

![](Images\Day01\05.jpg)

![](Images\Day01\06.jpg)

![](Images\Day01\07.jpg)

3.测试JDK是否安装成功

按Win + R 快捷键，调出控制台窗口

![](Images\Day01\08.jpg)

在控制台窗口中输入 

```
java -version
```

显示出下图所示效果即表示JDK安装成功

![](Images\Day01\09.jpg)

4.配置环境变量

如果安装好了JDK之后在控制台中无法正确显示java -version的效果的话，那么则需要手动配置下环境变量，让你的操作系统能够找到你的java运行环境

在PC上点击右键，选择プロパティ

![](Images\Day01\10.jpg)

在右侧选择 システムの詳細設定

![](Images\Day01\11.jpg)