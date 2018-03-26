***

NCBI旗下的Pubmed文献服对我们广大科研狗来说是极其重要的资源。虽说Pubmed的功能已经比较完善，搜索栏也支持高级检索，但仍有一个痛点没有替我们解决掉：按影响因子分类显示文献。虽说IF有日薄西山的趋势，但目前仍是权威的期刊质量参考标准。小编今天就为大家带来一篇教程，介绍如何自定义Pubmed过滤器，创建自己的IF过滤条件。

***

## 效果预览

不同于平常的Pubmed搜索结果页面，小编设置好Filter再进行搜索，出来的页面是下面这样的：

![introduce](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/introduce.png)

> 这里请大家注意了，红色框内就是过滤器了，“Free Full Text”和“Review”是Pubmed自带的默认Filter，接着下面“IF>=9”、“IF>=5”、“IF>=10”三个Filter就是小编自定义的过滤器，定义了不同的影响因子范围。唔，有同学问那个蓝框内是什么东东？为什么我们没有显示这个？小编在这里说明一下，蓝框内是Chrome浏览器插件”医学文献助手“的效果，如果大家普遍反馈需要介绍，小编会考虑为这个插件写个短文。

OK，现在我们想看影响因子大于10的文章，那么就点击“IF>=10”这个Filter，效果如下：

![filtered](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/filtered.png)

> 图中可以看到，经过Filter条件的筛选，查询结果已经减少到366条，并且都是高分文章。

这时候大家可以放心挑选感兴趣的文章，保证都是高分:smile:

## 自制Filter

其实达到上面的效果非常简单，请按小编教程一步步来。

### 注册账号

首先，我们要能够保存自己的Filter设置，需要在Pubmed有自己的账号。账号注册过程非常简单，小编自己是用Google账号登陆的。

### Manage Filters

登陆了账号之后，点击右上角的“My NCBI”就可以进入管理。

![where](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/where.png)

然后找到如下图红框所示的“Filters”：

![myncbi](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/My%20NCBI.jpg)

点击“Manage Filters”就能进入过滤器管理：

![managefilters](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/managefilters.png)

> 图中就是Filters的管理界面。左边是自定义区域，右边是内置筛选条件的搜索和启用/关闭管理。

如上图所示，小编已经建立了几个自定义Filters，filter list每个条目前面打钩的，就是激活使用的，不用的取消勾选即可。

这里先不着急Create custom filter，我们需要先建立好过滤条件。

## IF过滤配置文件

我们需要告诉Pubmed哪些文章点数高，这样才能建立过滤条件，IF过滤配置文件就是用来告诉Pubmed规则的。

### 获取IF信息

这里就不让大家自己去找了，小编直接为大家提供Journal-Impact-factor_2016的下载链接：http://url.cn/44wuNAg（微云）。

### IF点数筛选

打开“Journal-Impact-factor_2016.xlsx”文件：

![if](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/IF.png)

将“Journal Impact Factor”一列按从大到小排序（默认已经从大到小）。

### 定义IF筛选参数

如果需要IF大于10的文章，则：

1. 在IF表中将IF大于10的期刊名称全部选中

2. 复制

   > 此处仅复制期刊名这一列，将IF点数大于10的全部复制

3. 新建一个word文件

4. 在word中`无格式`粘贴

5. 全选（Ctrl+A）

6. 替换（Ctrl+H）

   > 按照下图所示：
   >
   > ![find](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/find.png)
   >
   > 将换行符（以^p表示，相信大家都能在键盘上找到这个乘方符号）替换为" [journal] or "，切记使用英文输入法，标点符号全是英文，三个空格一个也不能少。

7. 在开头添加一个英文的引号

8. 删掉末尾的[ or "]（中括号内是需要去掉的，or前面有一个空格，需要删掉），效果如下

   > ![ifshow](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/ifshow.png)
   >
   > 问题排查：如果设置好后出现点击Filter没效果的问题，建议看看配置参数中是不是缺失空格或者符号不是英文。

9. 将处理好的配置参数添加到Pubmed，见下文。


### 向Pubmed添加Filter配置

这时候就可以点击“Create custom filter”按钮了。点击后界面如下：

![add](http://ok0b31fkx.bkt.clouddn.com/Pubmed%E6%8C%89%E5%BD%B1%E5%93%8D%E5%9B%A0%E5%AD%90%E7%AD%9B%E9%80%89%E6%96%87%E7%8C%AE/add.png)

在“Query terms”文本框内`无格式`粘贴word中处理好的内容，在“Save filter as:”文本框内填写对该过滤条件的命名，例如“IF>=10”。然后在新添加的filter条目前面打钩，就激活该条件了，此时回到Pubmed进行搜索，就可以使用自定义的筛选条件了。

> 在添加Filter的时候，根据每个人所处的不同网络环境。每次点击之后可能都需要耐心等候，尤其是添加的配置参数较多时。

## 实战

教程已经提供给大家，对于懒得动脑的伸手党，小编这里也准备好了自用的几个filter文件，分享给大家自己添加一下就好：http://url.cn/44x8lCK（微云）。

至于不止要鱼还要渔的同学，小编斗胆布置个作业：试着自己添加个IF大于20或IF大于30的过滤器吧！

> 文中链接如果失效，记得来公众号提醒小编续期哈~

