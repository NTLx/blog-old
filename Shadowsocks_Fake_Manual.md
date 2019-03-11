# <span id="top">Shadowsocks科学上网</span>

[TOC]

## Shadowsocks

Shadowsocks 可以指：一种基于 Socks5 代理方式的加密传输协议，也可以指实现这个协议的各种传输包，并采用 Apache 许可证、GPL、MIT 许可证等多种自由软件许可协议开放源代码。shadowsocks 分为服务器端和客户端，在使用之前，需要先将服务器端部署到服务器上面，然后通过客户端连接并创建本地代理。目前包使用 Python、C、C++、C#、Go 语言等编程语言开发。[Wikipedia](https://zh.wikipedia.org/wiki/Shadowsocks)

Shadowsocks 的运行原理与其他代理工具基本相同，使用特定的中转服务器完成数据传输。

在服务器端部署完成后，用户需要按照指定的密码、加密方式和端口，使用客户端软件与其连接。在成功连接到服务器后，客户端会在用户的电脑上构建一个本地Socks5代理。浏览网络时，网络流量会被分到本地socks5代理，客户端将其加密之后发送到服务器，服务器以同样的加密方式将流量回传给客户端，以此实现代理上网。[维基教科书](https://zh.wikibooks.org/wiki/Shadowsocks)

### Software & App

Shadowsocks 支持广泛、版本众多，这里仅介绍常用平台客户端。

> App 安装时请确保系统为当前流行的最新版本，否则可能遇到依赖缺失甚至兼容性问题

- Windows
[`shadowsocks-windows`](https://github.com/shadowsocks/shadowsocks-windows)

- Mac OS
[`ShadowsocksX-NG`](https://github.com/shadowsocks/ShadowsocksX-NG)

- Android
[`shadowsocks-android`](https://github.com/shadowsocks/shadowsocks-android)
[`shadowsocksr-android`](https://github.com/shadowsocksrr/shadowsocksr-android)

- iOS
[`ShadowRocket`](https://itunes.apple.com/hk/app/shadowrocket/id932747118?l=en&mt=8)
> ShadowRocket 已在国区下架，请自行于其他地区 App Store 购买，或寻找其他替代 App

- 各平台的客户端列表
[`shadowsocks`](https://shadowsocks.org/en/download/clients.html)

## Shadowsocks线路代理商

如上所述，Shadowsocks 需要服务器端&客户端的部署+连接才能达到应有的效果，所以我们需要选择各种服务商提供的代理配置。

供 Shadowsocks 所用的代理有免费的也有付费的。免费的不一定慢，付费的也并不一直稳定。只是付费代理在出现线路问题后会及时调整。

> 由于本文作者使用的代理商有邀请奖励，所以请有需要而且找得到作者的小伙伴来找我要个邀请吧。。。

## Shadowsocks/ShadowsocksR客户端添加服务器配置

Shadowsocks/ShadowsocksR 客户端使用极其简便，且基本上看选项就能完全明白什么意思。这里仅以作者使用的平台做简要示范。

### 获取服务器代理配置

> 请在各自使用的免费/付费代理商处获得。此处展示二维码添加配置示范。

在代理商网站找到类似下图的菜单：

![](http://lx-public-pic.oss-cn-shanghai.aliyuncs.com/Shadowsocks/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-03-11%2011.06.38.png)

点击类似`我的账号`的按钮，进入类似下图的界面：

![](http://lx-public-pic.oss-cn-shanghai.aliyuncs.com/Shadowsocks/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-03-11%2011.10.07.png)

点击类似`查看详细信息（增加服务器节点）`的链接，进入类似下图的界面：

![](http://lx-public-pic.oss-cn-shanghai.aliyuncs.com/Shadowsocks/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-03-11%2011.11.40.png)

点击类似`查看详细信息（扫描二维码）`的链接，进入类似下图的界面：

![](http://lx-public-pic.oss-cn-shanghai.aliyuncs.com/Shadowsocks/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-03-11%2011.12.37.png)

点击类似`显示XXX二维码`的按钮，屏幕上出现二维码，此时转去操作Shadowsocks/ShadowsocksR客户端。

### Shadowsocks/ShadowsocksR客户端操作

安装并运行客户端App后，请在众多状态栏/任务栏图标中找到软件图标（图标形状可理解为三角形、纸飞机等）：

![](http://lx-public-pic.oss-cn-shanghai.aliyuncs.com/Shadowsocks/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-03-11%2011.14.04.png)

鼠标左键或右键单击（请自行尝试）后弹出类似下图的菜单：

![](http://lx-public-pic.oss-cn-shanghai.aliyuncs.com/Shadowsocks/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-03-11%2011.14.29.png)

> 上图所示`PAC模式`为自动代理模式，仅需要代理的流量才走代理服务器；`全局模式`即接管全部流量。

请在类似`服务器配置`的选项中找到类似下图的选项：

![](http://lx-public-pic.oss-cn-shanghai.aliyuncs.com/Shadowsocks/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-03-11%2011.15.33.png)

**扫描屏幕上的二维码即可。**

请自行在菜单中找到类似`更新PAC`的选项，经常更新PAC规则可以保持`智能代理`：

![](http://lx-public-pic.oss-cn-shanghai.aliyuncs.com/Shadowsocks/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-03-11%2011.16.04.png)

---

***请注意本文高频使用的`类似`，意即与各自实际情况类比即可***

[Back to Top](#top)