---
layout: post
title: github构建博客的解决方案
date: 2019-05-09
categories: 各种应用的解决方案
tags: [各种应用的解决方案]
#description: 简单介绍本博客。
---

想在github page上构建自己的博客，前几个星期就动手搞了起来，但由于自己对于前端这些东西不是很熟，所以断断续续的，直到今天才把所有东西都搞懂，而且构建出自己的github博客了。

最终效果，大家可以参考一下我构建好的博客 [济沧海](https://chenjx85.github.io/) 以后可能很多博客都会在上面写啦哈哈哈。

教程如果每一步都详细地配图来写，太长了，以下一些步骤可以参考其他教程。本教程主要写，**整一套逻辑是怎么回事，加上笔者踩过的坑**。

过程如下。

1、申请一个github账号，比如笔者的github账号是chenjx85。

2、创建自己的仓库，改好仓库名，选择一个模板。这部分网上有很多教程，同学们尽量选择时间上近一些的教程，久一些的可能页面选项都不一样了。  
最终输入自己的账号名对应的网址，能够看到构建的页面，就算第一步成功了。  
比如笔者输入https://chenjx85.github.io，可以看到自己的页面。

3、下载并安装github desktop软件，登陆上自己的账号，把自己的仓库克隆到本地。

4、到这一步，我们可以开始写博客啦，但是笔者还觉得github提供的模板不好看，要有自己的模板，那么开始折腾吧！不想折腾的同学到这里就可以不用看啦。

5、选择一个好看的博客模板。笔者看了很多模板，最满意的是 [这个模板](https://www.cnfeat.com/)，模板的代码在 [这里](https://github.com/cnfeat/cnfeat.github.io)。  
这个模板简洁又好看，而且_config.yml中写了详细的注释，对于笔者这种纯新手很友好。  
同学们如果也喜欢这个模板的话，可以自己去下载。  
下载好了模板之后，肯定要来修改成自己想要的样子啦。

6、说一下github page大概的运行逻辑。  
我们提交_config.yml、html、md这些文件，推送到远程的服务器仓库上，github内置的jekyll程序会帮我们，利用这些提交的文件，生成html的静态页面。这些静态页面就是github page博客上看到的东西。  
既然逻辑是这样的，那么我们就要根据jekyll的规则来写_config.yml和html、md这些文件。 

7、说下模板文件夹里面的每个文件分别代表什么。  
①同学们如果使用上面的这个模板，可以在_config,yml中看到详细的注释，标题啊、头图啊、浏览器小图标啊等等，这个跟着修改就可以了。  
jekyll会根据_config.yml中的说明来生成静态页面。  
_config.yml是全局的一些配置。

②在根文件夹下还可以看到about、tags等等md文件，这些用markdown写成的文件对应的是博客中一个个的页面。  
我们打开about.md这些md文件，可以看到最上面有title、description，这些对应的是博客中about页面的文字。  
还有一个选项叫做layout，这个代表这个页面采用的布局。about.md中的layout是page。 

③这个page的布局在_layouts文件夹里面，对应的是page.html。  
文件夹中还有post.html，default.html这两个布局。  
我们打开page.html，可以看到layout选项是default，也就是说，page这个布局是在default.html的基础上改的。  
post.html也是在default.html基础上改的。 

④_post文件夹放置的是自己的文章，也都是用markdown格式写的。  
要写markdown，得有一个好用的编辑器。笔者今天尝试了几款编辑器，最终还是回到了visual code上。平时也是使用这一个编辑器。而且今天发现可以下载一个插件，实时地预览markdown写成的样子。  
如下图，选择鼠标所在位置的插件，安装。github风格的编辑器！

<center>
<img src="https://upload-images.jianshu.io/upload_images/17769309-efe91cc97d1736fc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="50%">
</center>

安装完之后，点击右上角的按钮（自己找一下啦），就可以实时预览了，如下图。

<center>
<img src="https://upload-images.jianshu.io/upload_images/17769309-5f6c3d36cf14b2f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="100%">
</center>

简单好看又好用！

⑤文件夹中还有css、fonts、js、less这些文件夹，这些笔者都没有去改过，维持原状。

⑥_includes文件夹放的是三个html文件，页面的一些布局，可以理解成是_layout文件夹中html文件引用的头文件。
 同学们如果需要修改这部分的话，自己学习一下html的语法，看懂了之后对应修改就可以了。

8、说下markdown写作的一些方法。
 插入图片，markdown的语法是

    ![](图片路径)

笔者最开始把图片包含在文件夹里面，推送到远程仓库，图片路径就写文件夹的相对路径，结果发现图片没有显示出来。
 后来分析了一下博客模板作者的博客，发现她把图片上传到简书了，取得一个外链之后，把外链地址当作图片路径写进去了，这样就可以显示图片。
 所以同学们也可以参照这个方法。

 图片想要居中和调整大小，笔者如下这样写就可以啦。

    <center>
    <img src="https://upload-images.jianshu.io/upload_images/17769309-2b71af7662530506.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" width="50%">
    </center>

非常简单。width也可以写成50px什么的，同学们自己根据需要调整。

 9、写完全部之后，推送到远程仓库，看下效果。嗯，很不错。哈哈哈。
 
笔者对于前端这些东西也是纯新手一个，很多都是半猜半推得到的结论，有哪里写得不对的，请尽管指出，谢谢同学们的指正~