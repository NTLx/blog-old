---
typora-copy-images-to: ipic
---

<span id="top"></span>

# Git学习

学习资料：

<https://git-scm.com/book/zh/v2>

 `.gitignore`模板：

https://github.com/github/gitignore

> ***勿使用中文文件名和中文目录***

[TOC]

## 在现有目录中初始化仓库

```bash
git init
```

---

## 结合VS Code使用

建立好仓库的效果

![](https://ws4.sinaimg.cn/large/006tNc79gy1fnifarbtstj31kw0no495.jpg)

至此，一个简单的本地版本管理已经搭建起来并可以正常使用了。

> 搭配Microsoft Visual Studio Code可以省略后面的学习内容并可视化操作。

---

## 查看git状态

```bash
git status
```

## 添加对指定文件的跟踪

```bash
git add *.sh
```

## 提交快照

```bash
git commit -m 'initial project version'
```

> `-m`参数是直接添加提交说明，单引号内即为本次commit的说明

## 跳过使用暂存区域

```bash
git commit -a
```

## 移除暂存文件

```bash
git reset file
```

## 移除文件

```bash
$ rm PROJECTS.md
$ git rm PROJECTS.md
rm 'PROJECTS.md'
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    deleted:    PROJECTS.md
```

## 移动文件

```bash
git mv file_from file_to
```

## 查看提交历史

```bash
git log
```

### 显示每次提交的内容差异

```bash
git log -p -2
```

> `-2`表示显示最近2次提交

### 看每次提交的简略统计信息

```bash
git log --stat
```

### 限制 `git log` 输出的选项

`-(n)`

仅显示最近的 n 条提交

`--since`, `--after`

仅显示指定时间之后的提交。

`--until`, `--before`

仅显示指定时间之前的提交。

`--author`

仅显示指定作者相关的提交。

`--committer`

仅显示指定提交者相关的提交。

`--grep`

仅显示含指定关键字的提交

`-S`

仅显示添加或移除了某个关键字的提交



---



# 远程使用

> 本文以有“国内GitHub”之称的“[码云](https://gitee.com/)”为远程仓库做示范。

## 建立仓库

在码云注册好账户之后，新建项目。如下图所示：

![C25EC324-1748-4F69-90F0-AD8368AA9036](https://ws2.sinaimg.cn/large/006tNc79gy1foxhq75806j30bi0arjs3.jpg)

简单输入信息即可：

![D38B7D8F-3B8D-4EF4-A9C1-3AEAC5C5FE08](https://ws3.sinaimg.cn/large/006tNc79gy1foxhtshrzzj30pa0pi40g.jpg)

## 获取远程仓库操作权限

### 创建SSH公钥

大多数 Git 服务器都会选择使用 SSH 公钥来进行授权。系统中的每个用户都必须提供一个公钥用于授权，没有的话就要生成一个。生成公钥的过程在所有操作系统上都差不多。

SSH 公钥默认储存在账户的主目录下的 `~/.ssh` 目录。进去看看：

```bash
$ cd ~/.ssh
$ ls
authorized_keys2  id_dsa       known_hosts
config            id_dsa.pub
```

关键是看有没有用 `something` 和 `something.pub` 来命名的一对文件，这个 `something` 通常就是 `id_dsa` 或 `id_rsa`。有 `.pub` 后缀的文件就是公钥，另一个文件则是密钥。假如没有这些文件，或者干脆连 `.ssh` 目录都没有，可以用 `ssh-keygen` 来创建。该程序在 Linux/Mac 系统上由 SSH 包提供，而在 Windows 上则包含在 MSysGit 包里：

```bash
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/schacon/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/schacon/.ssh/id_rsa.
Your public key has been saved in /Users/schacon/.ssh/id_rsa.pub.
The key fingerprint is:
43:c5:5b:5f:b1:f1:50:43:ad:20:a6:92:6a:1f:9a:3a schacon@agadorlaptop.local
```

它先要求你确认保存公钥的位置（`.ssh/id_rsa`），然后它会让你重复一个密码两次，如果不想在使用公钥的时候输入密码，可以留空。

现在，所有做过这一步的用户都得把它们的公钥给你或者 Git 服务器的管理员（假设 SSH 服务被设定为使用公钥机制）。他们只需要复制 `.pub` 文件的内容然后发邮件给管理员。公钥的样子大致如下：

```bash
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAklOUpkDHrfHY17SbrmTIpNLTGK9Tjom/BWDSU
GPl+nafzlHDTYW7hdI4yZ5ew18JH4JW9jbhUFrviQzM7xlELEVf4h9lFX5QVkbPppSwg0cda3
Pbv7kOdJ/MTyBlWXFCR+HAo3FXRitBqxiX1nKhXpHAZsMciLq8V6RjsNAQwdsdMFvSlVK/7XA
t3FaoJoAsncM1Q9x5+3V0Ww68/eIFmb1zuUFljQJKprrX88XypNDvjYNby6vw/Pb0rwert/En
mZ+AW4OZPnTPI89ZPmVMLuayrD2cE86Z/il8b+gw3r3+1nKatmIkjn2so1d01QraTlMqVSsbx
NrRFi9wrf+M7Q== schacon@agadorlaptop.local
```

关于在多个操作系统上设立相同 SSH 公钥的教程，可以查阅 GitHub 上有关 SSH 公钥的向导：`http://github.com/guides/providing-your-ssh-key`。

### 向码云账户添加公钥

进入自己码云账户的设置：

![900699D8-ACDB-4545-8C5A-10E2FD224E6A](https://ws1.sinaimg.cn/large/006tNc79gy1foxjus86m2j304m06ht8q.jpg)

选择SSH公钥：

![445D5438-0803-4255-8B39-27695D11F506](https://ws3.sinaimg.cn/large/006tNc79gy1foxjvjwrkmj308f0fvjru.jpg)

直接将公钥内容添加进去即可，取一个有意义的名字来管理：

![40E4EECE-327E-4078-8074-072AFFEA19B3](https://ws3.sinaimg.cn/large/006tNc79gy1foxjwf5gkbj30p70al0t5.jpg)

## 终端使用远程仓库

### 本地初始化一个项目

首先，你需要执行下面两条命令，作为 git 的基础配置，作用是告诉 git 你是谁，你输入的信息将出现在你创建的提交中。

```bash
git config --global user.name "你的名字或昵称"
git config --global user.email "你的邮箱"
```

然后在你的需要初始化版本库的文件夹中执行：

```bash
git init 
git remote add origin <你的项目地址> //注:项目地址形式为:https://gitee.com/xxx/xxx.git或者 git@gitee.com:xxx/xxx.git
```

这样就完成了一次版本你的初始化。

如果你想克隆一个项目，只需要执行：

```bash
git clone <项目地址>
```

### 完成第一次提交

进入你已经初始化好的或者克隆项目的目录,然后执行：

```bash
git pull origin master
<这里需要修改/添加文件，否则与原文件相比就没有变动>
git add .
git commit -m "第一次提交"
git push origin master
```

然后如果需要账号密码的话就输入账号密码，这样就完成了一次提交。

> 此时，你可以在你的个人面板、项目主页查看到你的提交记录。

按照本文档新建的项目时，在码云平台仓库上已经存在 readme 文件，故在提交时可能会存在冲突，这时需要选择的是保留线上的文件或者舍弃线上的文件，如果舍弃线上的文件，则在推送时选择强制推送，强制推送需要执行下面的命令：

```bash
git push origin master -f
```

如果选择保留线上的 readme 文件,则需要先执行：

```bash
git pull origin master
```

然后才可以推送,如果发生冲突，则需要先解决冲突,关于如何处理冲突，请参阅[如何处理代码冲突](http://git.mydoc.io/?v=16912&t=66902)。

## [可选]开启静态网站托管功能

在项目页`服务`标签可以找到`Pages`：

![8EF5EF67-9F2C-4311-8FC3-4F1579D17816](https://ws3.sinaimg.cn/large/006tNc79gy1foxhwt1lmmj30za0hljud.jpg)

点击`启动服务`即可：

![6157CECF-315A-4E2A-9EDA-D2D10C151F54](https://ws3.sinaimg.cn/large/006tNc79gy1foxhxvek3hj30sy083gmi.jpg)

以本示例仓库为例，静态网站访问地址即为：

![9E64AB6A-7EF0-45F0-939A-1D83ECFAA646](https://ws3.sinaimg.cn/large/006tNc79gy1foxhyu2mw2j30c706jq3g.jpg)

### 建立可访问页面

在仓库根目录下建立`index.html`即可建立静态网站首页：

![9A1850A4-B7D2-4DD8-98D4-8F6B595A6725](https://ws1.sinaimg.cn/large/006tNc79gy1foxi1dykgej30zg0ftdig.jpg)

首页即为`index.html`内容。

自行添加`html`文件即可完成网站建设。

---

[Back to top](#top)