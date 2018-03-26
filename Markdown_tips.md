# Markdown标记语言

<span id="top"></span>

❝为纯粹写作而生的简化版网页编辑语言，通过编辑器实现丰富功能（包括几乎所有文档格式的转换），单纯写作不需要任何编辑器，其内容为纯文本。❞--本文使用Markdown编辑

---

[TOC]

---

**Markdown**由[Daring Fireball](http://daringfireball.net/)创造，原始版本在[这里](http://daringfireball.net/projects/markdown/syntax)，其语法随着版本和编辑器的不同而有细微差异。**Typora**使用的是[GitHub Flavored Markdown][GFM]. 

**注意：**尽管Markdown源码中的HTML语句是可以被识别的，但并不能保证一定会被正确识别&编译。

## 编辑器安装

这里推荐一个还处于beta版本的免费Markdown编辑器[Typora](https://typora.io)，是图形界面的编辑器，有“所见即所得”特性。可通过 `Help`->`Markdown Reference` 查看更多说明。支持Mac、Linux（Ubuntu）、Windows。请点击前面的链接去官网下载安装包（不科学上网速度慢，但安装包不大）。

> Markdown文件后缀为.md
>
> 生信部QQ群中上传有三个平台的安装包，但仍推荐去官网自行下载最新版。

![](https://ws4.sinaimg.cn/large/006tNbRwgy1fnbgvyebpjg30vu0s6qgf.gif)

事实上编辑器并不是必须的，它只是针对Markdown集成了丰富的附加功能，单纯写作不需要任何编辑器，纯文本即可。

## Typora设置

该软件本身有很多进一步方便Markdown使用的设置，默认并没有打开，推荐大家选择自己常用的打开。

![](https://ws2.sinaimg.cn/large/006tNc79ly1fnidli8szdj30fo0eijt8.jpg)

> 该选项卡中的字体设置在某些时候非常有用。

![](https://ws1.sinaimg.cn/large/006tNc79ly1fnidm8ri6jj30fo0ghaco.jpg)

> 该选项卡中的自动匹配在一般情况下是比较好用的。
>
> 关于进阶的图片插入功能如何实现，可以参考：http://support.typora.io/Images/，甚至有可能达到自动图床的效果。

![](https://ws1.sinaimg.cn/large/006tNc79ly1fnido2pjo8j30fo0dwac2.jpg)

> 原本Markdown中并没有上标、下标等对应的语法标记，只能使用HTML语法；但Typora软件定义了一种标记，可以在设置中开启。
>
> 代码块显示行号是比较实用的设置。

## 可视化主题

所谓可视化主题，即由Markdown编辑器生成的各种格式的可读文档的内容展现形式，本文所用为GitHub风格的CCS（没错，主题修改可以通过修改CCS完成，所以生成的网页文档中的字体是会被浏览器设置替换的）。例如文字对齐格式、图片是否居中、字体设置等。如有自定义主题的高级需求，请查阅网上的相关说明，或者Typora的帮助文档。

## Tips

###快速预览（Mac）

常用Mac OS 预览插件，安装后，按空格键预览可以支持很多格式：（homebrew安装）

```shell
brew cask install qlcolorcode qlstephen qlmarkdown quicklook-json qlimagesize webpquicklook suspicious-package quicklookase qlvideo provisionql quicklookapk quicklook-pat quicklook-csv
```

### 格式转换

Typora使用众所周知的Pandoc来进行，推荐安装使用（Typora软件自带安装指导）。

###文档（版本）管理

可以使用基于Git的版本管理，也可以使用网盘（推荐Dropbox，但需要科学上网）。也有自带版本和多文档管理的Markdown编辑器（如MWeb），但我们并没有Markdown Project的需求，所以使用各自系统自带的资源管理器即可（Typora不带文档管理功能）。

### 图床

最常用的是微博图床。

Mac OS上有一些图床软件支持一键上传图片并返回Markdown格式的图片链接，例如iPic，推荐使用。

---

***本文内容已经足够日常使用，更多相关资料请上网查阅或查看Typora帮助文档。***

**Markdown示例文档请参考`OE2017H2570N_README.md`或Typora帮助文档本身。**

[回到顶部](#top)

[GFM]: https://help.github.com/articles/github-flavored-markdown/
