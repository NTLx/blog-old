# 用Docker建立本地WordPress

众所周知，WordPress是一个以PHP和MySQL为平台的自由开源的博客软件和内容管理系统。很多人会有建立本地（局域网）内容管理系统的需求，主要用于测试（例如在本地测试好WordPress的配置，然后一键导入公开发布的服务器中），或者用于内部交流（可以建成内部资源分享平台）。

本文就以Mac OS X为例介绍了一种极其便捷、稳定的本地WordPress构建方法，~~爱折腾~~有需要的小伙伴可以直接使用。

另外，能够点开这篇文章查看的，想必已不需要什么背景介绍，本文只有纯粹的干货，保证实用。

## 下载Docker

[官网提供各种平台Docker的下载](https://www.docker.com/community-edition)

![](https://ws3.sinaimg.cn/large/006tNc79gy1fnog4r2fg8j311916igst.jpg)

## 安装Docker

![](https://ws4.sinaimg.cn/large/006tNc79gy1fnog1cvbfuj30n40ckgpa.jpg)

## Docker镜像提速

注册一个[阿里云](https://cr.console.aliyun.com)，获得其镜像加速器使用链接：

![](https://ws4.sinaimg.cn/large/006tNc79gy1fnogc49gdaj30vi0oatdu.jpg)

点击Docker图标进入设置：

![](https://ws3.sinaimg.cn/large/006tNc79gy1fnog8sw04bj307509it99.jpg)

目前新版是在Deamon标签页中输入加速器地址：

![](https://ws1.sinaimg.cn/large/006tNc79gy1fnogccb1hvj30h00iwjt0.jpg)

## 拉取镜像

```bash
docker pull wordpress
docker pull mysql
```

## MySQL

```bash
docker run --name mysql_wordpress -e MYSQL_ROOT_PASSWORD=wordpress -d mysql
```

## WordPress

```bash
docker run --name docker_wordpress --link mysql_wordpress:mysql -p 8085:80 -d wordpress
```

## 进行WordPress配置

浏览器输入：

```bash
http://localhost:8085
```

## 局域网访问

为了局域网能够正常访问，需进入WordPress常规设置页面，将`URL`中的`localhost`改为本机IP。

![](https://ws2.sinaimg.cn/large/006tNc79gy1fnogjzx4lzj30ox0frju7.jpg)

## 效果

![](https://ws4.sinaimg.cn/large/006tNc79gy1fnogyakxh1j310h16i4j5.jpg)

---

欧易的小伙伴们可以在公司电脑浏览器中输入`http://10.1.16.182:8085`来访问这个本地博客，其他小伙伴们如果感兴趣的话，欢迎来欧易生物体验哦~