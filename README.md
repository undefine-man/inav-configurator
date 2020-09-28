# INAV配置器

INAV Configurator是一款用于INAV飞行控制系统的跨平台配置工具。

它以应用程序的形式在谷歌浏览器中运行，允许您配置运行在任何支持的INAV目标上的INAV软件。

该工具和INAV支持各种类型的飞机，例如四翼飞机、六翼飞机、八翼飞机和固定翼飞机。

## INAV配置器启动时最小化，我应该怎么做？

你必须删除`C:\Users%Your_UserNname%\AppData\Local/inav-configurator`文件夹及其所有内容。

https://www.youtube.com/watch?v=XMoULyiFDp4

或者，在Windows上使用PowerShell，你可以使用post_install_cleanup.ps1脚本来进行清理。(谢谢你James Cherrill)

## 安装

根据目标操作系统的不同，INAV Configurator以独立应用程序或Chrome应用程序的形式发布。

#### Windows系统

1. 访问发布页面
2. 下载Windows平台的配置器（win32或win64）。
3. 解压ZIP档案
4. 从解压后的文件夹中运行INAV Configurator应用程序。
5. 配置器没有签名，所以你必须允许Windows运行不受信任的应用程序。第一次运行时可能会有一个提示。

#### Linux

1. 访问发布页面
2. 下载Linux平台的配置器(有linux32和linux64)
3. 解压tar.gz文件
4. 使inav-configurator文件可执行（chmod +x inav-configurator）。
5. 从解压后的文件夹中运行INAV Configurator应用程序。

#### Mac

1. 访问发布页面
2. 下载Mac平台的配置器
3. 解压ZIP档案
4. 运行INAV配置器
5. 配置器没有签名，所以你必须允许Mac运行不受信任的应用程序。在第一次运行时，可能会有一个提示。

#### ChromeOS

###### INAV配置器形式的ChromeOS可在Chrome网络商店中使用。

##### 在本地构建和运行INAV配置器（针对开发或Linux用户）。

本地开发时，使用node.js构建系统。

1. 安装node.js

2. 从项目文件夹中运行`npm install`

3. 构建JS和CSS文件并启动配置器。

   - 用NW. js： 运行`npm start`.

   - 在Chrome浏览器中：运行`npm start`。运行`npm run gulp`. 然后打开`chrome://extensions`，启用开发者模式，点击`Load unpacked extension...`按钮并选择inav-configurator目录。


其他任务也在`gulpfile.js`中定义。要运行一个任务，使用`./node_modules/gulp/bin/gulp.js task-name`。可用的有

- build：gulp.js 从其源头生成配置器使用的JS和CSS输出文件。每当对任何.js或.css文件进行更改时，必须运行它，以使这些更改出现在配置器中。如果添加了新文件，它们必须包含在gulpfile.js中。请参阅gulpfile.js顶部的注释来了解如何做到这一点。也请参见watch任务。
- watch：观察JS和CSS源的变化，并在它们被编辑时运行构建任务。
- dist：创建一个应用程序的发行版（有效）。在./dist/目录下创建应用程序的分发版（既可以打包成Chrome应用程序，也可以打包成NW.js应用程序）。
- 发布：为每个支持的平台（win32、osx64和linux64）在./apps目录下创建NW.js应用。在macOS或Linux上运行这个任务需要Wine，因为需要它来设置Windows应用的图标。如果你没有安装Wine，你可以通过运行release-only-linux任务来创建一个版本。

## 不同的地图提供商

- INAV Configurator 2.1允许选择OpenStreetMap、Bing Maps和MapProxy地图提供商。INAV Configurator没有Bing Maps的API密钥。这意味着：每个想使用Bing地图的用户必须创建自己的账户，同意Bing地图要求的所有条款和条件，并自行配置INAV配置器。


#### 如何选择地图提供商

1. 点击INAV配置器右上角的设置图标。
2. 选择提供者。OpenStreetMap、Bing或MapProxy。
3. 在必应地图的情况下，你必须提供你自己的，个人的，由你生成的，必应地图的API密钥。
4. 对于MapProxy来说，你需要提供一个服务器的URL和层名来使用

#### 如何获得必应地图API密钥

1. 转到必应地图开发中心https://www.bingmapsportal.com/。
   - 如果您有必应地图账户，请使用您用来创建账户的Microsoft账户登录，或创建一个新账户。对于新账户，请按照创建必应地图账户中的说明进行操作。
2. 选择 "我的帐户 "下的 "我的钥匙"。
3. 选择创建新钥匙的选项。
4. 提供以下信息来创建一个密钥。
   1. 应用程序名称：Application name: Required. 应用程序的名称。
   2. 应用程序的URL：应用程序的URL。这是一个可选字段，有助于你在将来记住该键的目的。
   3. 密钥类型：必填。选择您要创建的密钥类型。你可以在这里找到密钥和应用程序类型的描述。
   4. 应用类型：必填。选择最能代表将使用此密钥的应用程序的应用程序类型。您可以在这里找到密钥和应用程序类型的描述。
5. 单击 "创建 "按钮。新密钥显示在可用密钥列表中。按照您正在使用的 Bing Maps API 文档中的描述，使用此密钥来验证您的 Bing Maps 应用程序。
   如何设置MapProxy服务

## 作者

Konstantin Sharlaimov/DigitalEntity - INAV固件和配置器的维护者。

INAV配置器最初是Cleanflight配置器的一个分支，支持INAV而不是Cleanflight。

这个配置器是唯一支持INAV特定功能的配置器。它可能需要您在飞行控制器上运行最新的固件。如果您遇到任何问题，请确保您运行的是最新的固件版本。

## 注意事项

#### WebGL

确保设置->系统->"可用时的用户硬件加速 "被选中，以达到最佳性能。

##### Linux用户

1. 不要忘了将你的用户添加到拨号组 "sudo usermod -aG dialout YOUR_USERNAME "中，以便进行串行访问。
2. 如果你有3D模型动画的问题，请在Chrome的flags中启用 "覆盖软件渲染列表 "chrome://flags/#ignore-gpu-blacklist。

#### 支持

GitHub问题跟踪器是为bug和其他技术问题保留的。如果您不知道如何设置所有的东西，硬件不工作或有任何其他支持问题，请咨询。

- rcgroups主线
- Telegram集团

#### 问题跟踪器

对于INAV配置器的问题，请在这里提出

https://github.com/iNavFlight/inav-configurator/issues

对于INAV固件问题，请在这里提出

https://github.com/iNavFlight/inav/issues

#### 开发商

我们接受干净合理的补丁，请提交它们!

#### 鸣谢

ctn - Baseflight Configurator的主要作者和维护者。Hydra - Cleanflight Configurator的作者和维护者，该项目是从Cleanflight Configurator分叉出来的。