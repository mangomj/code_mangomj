
---
title : Hexo next theme相关个性化设置
categorites : Hexo||next
---
>

<h3>1.Hexo-Next底部logo栏更改以及注意事项</h3>



1.首先，找到 \themes\next\layout\_partials\下面的footer.swig文件，打开会发现，如下图的语句：

<img src="/imgs/hexo_config/1.png" width=500>

看到划框的地方了吗？
<li>第一个框 是下面侧栏的“日期❤ XXX”</li>如果想像我一样加东西，一定要在双大括号外面写。如：xxx{{config.author}},当然你要是想改彻底可以变量都删掉，看个人意愿。
<li>第二个，是图一当中 “由Hexo驱动” 的Hexo链接，先给删掉防止跳转，如果想跳转当然也可以自己写地址，至于中文一会处理。注意删除的时候格式不能错，只把<a>...</a>标签这部分删除即可，留着两个单引号'',否则会出错哦。</li>
<li>第三个框也是最后一个了，这个就是更改图一后半部分“主题-Next.XX”,这个比较爽直接将<a>..</a>都删掉，同样中文“主题”一会处理，删掉之后在上一行 ‘-’后面可以随意加上你想显示的东西，不要显示敏感信息哟，请自重。</li>
2.接下来，处理剩余的中文信息。找到这个地方\themes\next\languages\ 下面的语言文件zh-Hans.yml（这里以中文为例，有的习惯用英文的配置文件，道理一样，找对应位置即可）
打开之后，如图：

<img src="/imgs/hexo_config/2.png" width=250>

看到了吧，这个就是传值传过去的，你想显示什么就在这里面大肆的去改动吧。其实在第二个框中，就可以把值都改掉，不用接受传值的方式，完全自己可以重写。不过我不建议那样做，因为传值这样只要是后续页面需要这几个值那么就都会通过取值去传过去，要是在刚才footer文件中直接写死，后续不一定哪个页面需要传值，但是值为空了或者还是原来的，可就尴尬了。所以还是这样改动吧。

作者：Codeagles
链接：https://www.jianshu.com/p/4fbc57269f1b
来源：简书


<h3>2.配置使用不蒜子计数</h3>
	

如果你使用的主题是NexT，那么你可以很方便的进行不蒜子的访客统计设置，仅仅只需要一步：

打开主题的配置文件/theme/next/_config.yml，找到如下配置：
# Show PV/UV of the website/page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi/
busuanzi_count:
  # count values only if the other configs are false
  enable: false
  # custom uv span for the whole site
  site_uv: true
  site_uv_header: <i class="fa fa-user"></i>
  site_uv_footer:
  # custom pv span for the whole site
  site_pv: true
  site_pv_header: <i class="fa fa-eye"></i>
  site_pv_footer:
  # custom pv span for one page only
  page_pv: true
  page_pv_header: <i class="fa fa-file-o"></i>
  page_pv_footer:

将enable的值由false改为true，便可以看到页脚出现访问量，上述配置表示：

site_uv表示是否显示整个网站的UV数

site_pv表示是否显示整个网站的PV数

page_pv表示是否显示每个页面的PV数
当然，对于不蒜子的配置可以随意更改，一下附上本人的配置：

# Show PV/UV of the website/page with busuanzi.
# Get more information on http://ibruce.info/2015/04/04/busuanzi/
busuanzi_count:
  # count values only if the other configs are false
  enable: true
  # custom uv span for the whole site
  site_uv: true
  site_uv_header: 访客数
  site_uv_footer: 人
  # custom pv span for the whole site
  site_pv: true
  site_pv_header: 总访问量
  site_pv_footer: 次
  # custom pv span for one page only
  page_pv: true
  page_pv_header: <i class="fa fa-file-o"></i>  阅读数
  page_pv_footer:

注意事项

两种方法选择一种使用即可，都使用可能会出现无法显示的问题
使用hexo s部署在本地预览效果的时候，uv数和pv数会过大，这是由于不蒜子用户使用一个存储空间，所以使用localhost:4000进行本地预览的时候会导致数字异常，这是正常现象，只需要将博客部署至云端即可恢复正常。
网站运行一段时间后想要初始化访问次数，官方回答是可以注册登录自行修改阅读次数，但是我登录官网依旧显示无法注册，如果有方法可以在评论中指出。

如果无法显示数据，解决方法:

到hexo的themes文件夹下, 进入

\themes\next\layout_third-party\analytics

打开: busuanzi-counter.swig

将src=“https://dn-lbstatics.qbox.me/busuanzi/2.3/busuanzi.pure.mini.js”

修改为src=“https://busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js”

--------------------- 
作者：韦人人韦 
来源：CSDN 
原文：https://blog.csdn.net/ddydavie/article/details/83020549 

作者：幽小鬼
链接：https://www.jianshu.com/p/c311d31265e0
来源：简书



<h3>3.hexo添加分类</h3>

当前博客主题用的是next最新版，最初是比较简陋的界面，一直放着没怎么动，测试了下Latex的显示效果没有达到在CSDN我的博客上的效果，就很失望，没再此地更新。

但是今年（2018）年突然发现hexo可以做出很酷的静态站点。

于是开始作为首发文章的地方。

下面开始细部的折腾，细节过程记录为文档，以供参考。

创建分类页面（page）
第一步是创建分类显示界面：

https://github.com/iissnan/hexo-theme-next/wiki/%E5%88%9B%E5%BB%BA%E5%88%86%E7%B1%BB%E9%A1%B5%E9%9D%A2

可以参考这个官方的链接，也可以看我摘出来的文字。

1.新建一个页面，命名为categories:

hexo new page categories

之所以命名为categories的原因是在next主题的配置文件中，categories是关键词。

2.编辑新建界面，将页面类型设置为categories，主题将会在这个页面上显示所有的分类：

title: categories
date: 2018-03-02 12:33:16
type: "categories"

这个步骤很有意思，编辑新建界面是什么？当然hexo熟悉一些自然会知道，但是小萌新还是比较懵逼的。实际上调用hexo new page xxx后，会在/source/categories/目录下生成一个index.md文档，在此文档头部加上上面这段即可。实际上，index.md里只需要有这个声明即可，其他内容并不会显示出来，写了也没用。

PS. 无论是page，还是post的文章，都是以.md格式结尾，在hexo g的过程中会产生对应的.html文档，然后hexo d到Github上的也只是html文档，不是.md格式的文档。

另外就是，需要注意一点：如果有启用多说 或者 Disqus 评论，默认页面也会带有评论。需要关闭的话，请添加字段 comments 并将值设置为 false，如：


title: categories
date: 2018-03-02 12:33:16
type: "categories"
comments: false


这个暂时不是很明白，再说吧。

3.在菜单中添加链接，此时需要编辑主题的_config.yml，hexo的配置文件事先写好了，但是处于注释状态，需要去除注释即可：

menu:
  home: / 
  tags: /tags
  categories: /categories
  archives: /archives

内容更少些。

我从自己的配置文件中拿出来的是这样的，注意通过或链接的内容，暂时我也不是很明白用意，猜测是多一种选择吧，官方文档给出的是：

menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags
  categories: /categories/ || th
  archives: /archives/ || archive

6
此时准备完毕，去网站上点开分类这栏，会发现没有任何分类，但是分类这栏已经是有内容的了，不再是404错误。因为还没有文章关联到分类。

添加文章分类关联
第二步是为写的post文章指定分类：

上面是next主题官方给出的配置方案，而如何为文章关联分类，是hexo官方给出的。

hexo的front-matter概念

即在xxx.md上方指定文章title, date, tag等的地方。 
仔细想想可以明白，分类也应该指定在这个地方。

就是在文章头部指定一个categories属性即可，注意，这些属性和属性值之间必须有一个空格，否则解析错误。

示例：


title: 杀死一只知更鸟观后感
date: 2018-03-01 21:46:12
tags:
categories: 电影评论

这样不仅本篇文章上会有分类名，点击菜单栏也会显示各个分类。


--------------------- 
作者：QUETAL 
来源：CSDN 
原文：https://blog.csdn.net/u011240016/article/details/79422462 



