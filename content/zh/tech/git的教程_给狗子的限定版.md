+++
title = "git的教程_给狗子的限定版"
date = "2021-11-01T18:18:21+08:00"
tags = ["git", "windows", "tutorials"]
slug = "git-resources-for-someone"
+++

# 前言

本文是** Git 的一篇简单介绍**。我们从介绍版本控制工具的简单知识开始，然后简单讲解 git 的原理和工作流程 ，最后是关于如何设置 Git 以便立刻开始工作。出于对朋友的关心，添加如何把给 Git 融入日常工作流的一些例子。

---

# 关于版本控制

什么是“版本控制”？我为什么要关心它呢？

> 版本控制是一种记录一个或若干文件的内容变化，以便将来查阅特定版本修订情况的系统。

这是 Git 官方的介绍 .这个纯粹的定义大家可能都有点云里雾里.
我想在我们的日常生活中,我们其实不知不觉的也在使用版本控制系统的概念,比如你可能有着这样子的文件命名 😂
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641626065680-d2ed32bc-b864-4b15-b86c-2d173c9639a0.png)
我举得例子有点夸张,但其实特别是小组共同完成一个报告的时候,
你会觉得那实在是太灾难了(/▽＼)

---

如果你是位图形或者网页设计师,可能需要保存某一副图片或页面布局文件的所有修订版本,采用版本控制系统是个很机智的选择.

---

为了解决这类问题( 但更多原因是因为大型软件的开发需要一群人协作完成 , 手动合并代码问题太多了 ),
人们发明了两大类版本控制系统,
一类集中化的版本控制系统（Centralized Version Control Systems，简称 CVCS）,
一类分布式版本控制系统（Distributed Version Control System，简称 DVCS）,
**而本文要介绍的 Git 正是 DVCS 中最闪亮的一颗明星. **
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641626991754-3e3f4aa5-1f97-49a8-8515-2cfbddd44450.png)

---

# Git 的原理和工作流程

---

![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641629298568-b183dd50-55f3-4aa5-ba3a-72b663c2f31c.png)
Git 在逻辑上是有三个重要的空间 :

1. **working directory,**实际上的工作目录,存储实际的文件,是你在电脑上直接持有的文件
2. **index ,暂存区**,里面存储的就是第一张图里面那些文档的 1.0 ,2.0 版本的快照.

   > 举个例子,你正在写一个代码,你目前这个程序终于可以跑起来了,你很开心,可你觉得这个代码也就能跑,你还想着改的更好一点,并不是只能跑就行,可你害怕自己改着改着代码可能运行不了. 你就可以提交你可以运行的那个版本代码到 index 里，这样万一你不想改了，你最后还是有一个可以运行的版本，不至于竹篮打水一场空。

3. **Head，** 指向你最后提交到 index 的版本

题外话：
head 之后其实还有一个很重要的概念，云端仓库，你可以把你的代码提交到云端，这样你的所有版本代码都可以存储到云端，妈妈再也不用担心我的代码丢了 😀
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641630434026-c35a5d35-a7fd-43bc-95d3-cb401c7f2a1a.png)

---

还有一个比较重要的是分支概念
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641630486293-0cc7333f-c264-4d26-afb1-6c950199e39c.png)

> 比较通俗的例子就是小说，作者发现自己写死了一个人物后,很多人骂他，可他又不想丢弃那个写好的结局，他就可以无耻的告诉读者，我新开了一条剧情线，这次没有人死哦。让你可以享受两个故事。
> 还有最常用的就是代码了，毕竟一群人写代码嘛，总有人激进，有人保守，大家一起工作，总会有那种各执己见的情况，双方都无法说服彼此，那就只能开个分支，一个人搞个实验版本的，一个人继续稳定版。

---

希望你永远也用不上下面的命令，还有现在图形化界面很多，反正我是没咋用过命令行回退版本（偷笑）
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641630941760-574ee894-e385-41e6-86e0-bc5ecf8d508f.png)

---

# 如何设置 Git 以便立刻开始工作

1. 去官网下载[ Git](https://git-scm.com/downloads)
2. 安装对应的版本
3. 初始化你的 git
   > 推荐使用 git bash 进行下列设置

![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641627499332-fb8a794f-05de-4e36-92fa-f05f073faed7.png)
先设置下你的用户名和邮箱
这样做很重要，因为每一个 Git 的提交都会使用这些信息，并且它会写入到你的每一次提交中，不可更改：

使用命令行输入

```bash
git config --global user.name "everr"
git config --global user.email everr@test.com
```

> “everr”是你自己设置的名字，everr@test.com是你的邮箱地址,邮箱地址可以任意写.

然后回车确认即可

---

## 获取 Git 仓库

两种获取 Git 项目仓库的方法： 一是在现有项目或目录下导入所有文件到 Git 中； 二是从一个服务器克隆一个现有的 Git 仓库。

### 在现有目录中初始化仓库

进入该项目目录并输入：

```bash
git init
```

该命令将创建一个名为 .git 的子目录，这个子目录含有你初始化的 Git 仓库中所有的必须文件，这些文件是 Git 仓库的骨干。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641631285328-dacb5626-5c9e-42ad-aca9-3c65cc256049.png)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641631308894-025cee5f-a95f-43e6-9ec3-7f1ebcf46cc3.png)

### 克隆其他人的项目

在此我要向你隆重介绍一个网站 Github：
~~全球同性交友网站，~~

全球程序员代码托管网站。
大家秉承着开源精神，开放了自己的代码在网上，仅仅**为了学习的话你尽情可以下载和使用**，但根据不同的开源协议，对其他用途的使用做了严格规定。

简单来说，git 是一个版本控制软件，github 是一个代码托管平台。

> 因为在实际生活中我们都可能遇到电脑死机，所以代码一定要备份。github 提供了免费代码托管，你可以在上面分享自己的一切，不止代码**。只要你认为它值得分享。**

代码托管平台不止 github(国内常常访问不了，最好自行科学上网),还有 gitee（GitHub 国内版，速度很棒） gitlab （另一个很有名的代码托管平台）
找个空目录，右键打开 Git bash， 输入

```bash
git clone https://github.com/PyFPDF/fpdf2.git
# 或者
git clone https://gitee.com/MinJieLiu/web-standard.git
```

![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641633253863-dd234830-fed5-4141-b236-63b4a44ecf87.png)

## 提交 add 和 commit

把实际工作目录的文件的版本推送到索引区

```bash
git add 文件名
#例如
git add 1.txt
#把一个文件加入暂存区
git add .
#把所有文件加入暂存区
#.代表全部文件
```

把索引区的几个文件提交到 head

```bash
git commit -m "the first commit"
```

![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641635443841-c02fbcb3-5c1f-48da-8edd-970c3bfd8808.png)

---

## 把本地项目推送到 github

由于本地 Git 仓库和 Github 仓库之间的传输是通过 SSH 加密的，所以连接时需要设置一下：

- 创建 SSH KEY。先看一下你 C 盘用户目录下有没有.ssh 目录，有的话看下里面有没有 id_rsa 和 id_rsa.pub 这两个文件，有就跳到下一步，没有就通过下面命令创建

```bash
$ ssh-keygen -t rsa -C "youremail@example.com"
```

> 然后一路回车。这时你就会在用户下的.ssh 目录里找到 id_rsa 和 id_rsa.pub 这两个文件.

- 登录 Github --->点击右上角的图标 --->选择 Settings --->点击左边的 SSH and GPG KEYS --->点击右上角的 New SSH key --->Title 随便填 --->把刚才 id_rsa.pub 里面的内容复制到 Title 下面的 Key 内容框里面 --->最后点击 Add SSH key --->完成 SSH Key 的加密。具体步骤如下：

![](https://cdn.nlark.com/yuque/0/2022/webp/906866/1641635933527-ed4bed67-861e-4062-a8cd-5bdd2faa0f7a.webp)

- 在 Github 上创建一个 Git 仓库。
  > ![](https://cdn.nlark.com/yuque/0/2022/webp/906866/1641635942563-db010dde-b02a-4a38-81c7-af10afd9b878.webp)

在 Github 上创建好 Git 仓库后，存储好你的仓库地址
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641636419237-339819a8-7d15-4fd7-8b94-aa0cd369514b.png)，通过命令

```bash
git remote add origin   https://github.com/k88hudson/git-flight-rules.git
#自己把网址换成你自己新建的网址
#最好全程科学上网或者使用gitee
```

和本地仓库进行关联
注意 origin 后面加的是你 Github 上创建好的仓库的地址。

---

关联好之后通过命令

```bash
git push -u origin master
```

将本地库的所有内容推送到远程仓（Github）

由于新建的远程仓库是空的，所以要加上-u 这个参数，等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需

```bash
git push origin master
```

刷新 Github 页面进入刚才新建的仓库里面就会发现项目已经上传成功

## 剩下的慢慢写

。。。。。
限于篇幅和个人能力，
其实 git 挺复杂的
我目前也就打算写这么多，剩下的嘛
我相信狗子你自学能力可以的（认真脸）

## 推荐链接

[git 简明指南](https://www.runoob.com/manual/git-guide/)
[git 在线练习](https://learngitbranching.js.org/?locale=zh_CN)
[《github 漫游指南》](http://github.phodal.com/)
[git 官方教程](https://git-scm.com/book/zh/v2)
[使用 git 将本地项目推送到远程仓库 github](https://www.jianshu.com/p/b1f9f684fac8)

如何查看每个 commit 到底修改了什么，红色部分代表删除，绿色备份代表新增的
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641638765441-9137e2ac-704b-4855-b0e4-0ba60f885067.png)

例子：
add
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641638130062-3e201f87-37fc-496c-868d-b565ea4dfb6b.png)
commit
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641638176876-f2e894d7-540c-4a48-bd94-96975b0b18de.png)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641638243461-fa197b85-bfd1-42b7-9d52-fe7af5b9526c.png)
push
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641638311868-d9b762fd-2937-4f1b-a97c-f700380207f9.png)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/906866/1641638545525-1d045fd2-682f-4775-895b-06cbe379b81f.png)
