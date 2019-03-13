# Markdown标记语言简介

<span id="top"></span>

## 编辑器

[Typora（点击下载）](https://typora.io#download)

## 常用Markdown语法介绍

### 目录

源码如下：

```markdown
[TOC]
```

### 强制换行

**源码如下：**

```Html
第一段文字<br/>第二段文字
```

**显示效果：**


第一段文字<br/>第二段文字

### 标题

**源码如下：**

```markdown
# 一级标题

## 二级标题

###### 六级标题
```

**显示效果：**

# 一级标题

## 二级标题

###### 六级标题

### 引用

**源码如下：**

```markdown
> 这一段就是引用的效果。
>
> 在Typora中，键入'>'后直接输入内容，<br/>点击回车即可。



> 不再继续输入引用格式，只需再次点击回车即可回到正文输入格式。
```

**显示效果：**

> 这一段就是引用的效果。
>
> 在Typora中，键入'>'后直接输入内容，<br/>点击回车即可。



> 不再继续输入引用格式，只需再次点击回车即可回到正文输入格式。

### 列表

**源码如下：**

```markdown
*   Red
*   Green
*   Blue
1.  Red
2. 	Green
3.	Blue
```

**显示效果：**

*   Red
*   Green
*   Blue

1.  Red
2.  Green
3.  Blue

### 任务列表

**源码如下：**

```markdown
- [ ] incomplete
- [x] completed
```

**显示效果：**

- [ ] incomplete
- [x] completed

### 代码块

**源码如下：**

```
​```shell
for i in `ls *.txt`
do
sed -i 's/|/_/g' $i
done
​```
```

**显示效果：**

```shell
for i in `ls *.txt`
do
sed -i 's/|/_/g' $i
done
```

**源码如下：**

```markdown
行内代码`echo Hello, World !`是这样的写法。
```

**显示效果：**

行内代码`echo Hello, World !`是这样的写法。

### 加粗（强调）

**源码如下：**

```markdown
**double asterisks**
```

**显示效果：**

**double asterisks**

### 斜体

**源码如下：**

```
*斜体*
```

**显示效果：**

*斜体*

### 下划线

**源码如下：**

```html
<u>下划线</u>
```

**显示效果：**

<u>下划线</u>

### 上标

**源码如下：**

```html
示例<sup>上标</sup>
```

**显示效果：**

示例<sup>上标</sup>

### 下标

**源码如下：**

```html
示例<sub>下标</sub>
```

**显示效果：**

示例<sub>下标</sub>

### 简单链接

**源码如下：**

```markdown
[点击这里阅读更多](http://www.oebiotech.com)
[点此查看OE2017H2570N项目的分析脚本](OE2017H2570N_README.html#header-n705)
```

**显示效果：**

[点击这里阅读更多](http://www.oebiotech.com)

[点此查看OE2017H2570N项目的分析脚本](OE2017H2570N_README.html#header-n705)

### 图片

**源码如下：**

```markdown
![image](image.png "备注：这是一张示例图片")
```

**显示效果：**

![image](image.png "备注：这是一张示例图片")

**源码如下：**

```markdown
![数学公式动图](http://typora.io/img/inline-math.gif)
```

**显示效果：**

![数学公式动图](http://typora.io/img/inline-math.gif)

> 虽然Typora支持拖拽直接插入图片等操作，但是不推荐这样做，因为这样插入的图片必须保持与.md文件的相对路径才可以显示。
>
> 推荐大家使用图床来插入图片。

如需更多图片相关的帮助，请查看：[http://support.typora.io//Images/](http://support.typora.io//Images/)

## Tips

### 格式转换

Typora使用众所周知的Pandoc来进行，推荐安装使用（Typora软件自带安装指导）。

###文档（版本）管理

可以使用基于Git的版本管理，也可以使用网盘（推荐Dropbox，但需要科学上网）。也有自带版本和多文档管理的Markdown编辑器（如MWeb），但我们并没有Markdown Project的需求，所以使用各自系统自带的资源管理器即可（Typora不带文档管理功能）。

### 图床

最常用的是微博图床。

Mac OS上有一些图床软件支持一键上传图片并返回Markdown格式的图片链接，例如iPic，推荐使用。

---

***本文内容已经足够日常使用，更多相关资料请自行上网查阅或查看Typora帮助文档或与他人交流。***

**Markdown示例文档请参考`OE2017H2570N_README.md`。**

[回到顶部](#top)
