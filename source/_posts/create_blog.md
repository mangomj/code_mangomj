---
title: 几分钟，搞定部署一个个人blog
categories: Hexo
---
>这篇文章来教大家部署一个属于自己的blog。首先介绍一下Hexo，
1.介绍
<font color="red">Hexo</font>是一个基于node.js制作的一个博客工具，而并非是一个开源的博客系统。一般hexo不需要部署在服务器上，
我们用markdown来编写一个md类型的文章，再通过hexo生成对应的静态html文件，然后再上传到服务器。
总之hexo是一个html生成和上传的工具。<font color="red">github</font>就不多说了>,我们的项目需要push上去。
2.准备工作
注册一个github账号，最后的域名会是username.github.io。注册好了就可以create a repository，创建一个仓库，

接下来是安装，首先安装<font color="red">git</font>
    可以使用$ sudo apt-get install git自动安装,也可以自己下载安装包安装。

然后安装Nodejs
    $ sudo apt-get install nodejs

再安装非常重要的Hexo

    $ sudo apt-get install npm 安装npm
    $ npm install -g hexo-cli 安装hexo

3.发布
    创建博客
    $ hexo init username.github.io

更改设置
    主题安装
    为了使博客不太难看，我们需要安装一个主题，切换至刚刚生成的Hexo 目录，安装主题
    $ cd username.github.io
    $ git clone https://github.com/iissnan/hexo-theme-next themes/next
这里选了一个极简的主题，也是Hexo众多主题中最受欢迎的一个。上面出现的喵神的主题 在这里。Hexo也有更多主题供你选择。

基础配置
     打开文件位置username.github.io/_config.yml修改几个键值对，下面把几个必须设置的列出来按需求修改，记得保存， 还有注意配置的        键值之间一定要有空格

    title: mango仓库   //你博客的名字
    author: mangomj  //你的名字
    language: zh-Hans    //语言 中文
    theme: next   //刚刚安装的主题名称
    deploy:
    type: git    //使用Git 发布
    repo: https://github.com/username/username.github.io.git  

写文章

    在username.github.io/source/_posts下创建你的第一个博客,例如，创建一个名为first.md的文件


    ---
    title: First Night
    ---
    > 我有一头**小毛驴**，可是我从来都不骑。


测试

    $ hexo s

    测试服务启动，你可以在浏览器中输入https://localhost:4000 访问了。

安装hexo-deployer-git自动部署发布工具

    $ npm install hexo-deployer-git --save

发布
测试没问题后，我们就生成静态网页文件发布至我们的Github pages 中
   $ hexo clean && hexo g && hexo d  


本文借鉴csdn博客
--------------------- 
作者：惟爱妮 
来源：CSDN 
原文：https://blog.csdn.net/u012907783/article/details/79229759 