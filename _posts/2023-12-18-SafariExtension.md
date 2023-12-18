---
title: "Chrome Extension 转为 Safari Extension"
date: 2023-12-18 10:49:22 +0800
---

>   由于Safari对扩展的支持出现的较晚，在Safari上的扩展远不及Chrome的多，本文将以`CF Analytics`为例，介绍如何将Chrome扩展转为Safari扩展。

## 概述

基本步骤如下：

1.   导出Chrome扩展
2.   创建Safari扩展的Xcode项目
3.   导出Safari扩展

## 导出Chrome扩展

1.   进入Chrome的扩展管理界面

2.   找到扩展的id

     ![截屏2023-12-18-10](https://jsd.cdn.zzko.cn/gh/Heyya-x/picx-images-hosting@master/20231218/截屏2023-12-18-10.53.41.6mj5spd5jzeo.png)

3.   进入路径`~/Library/Application\ Support/Google/Chrome/Default/Extensions`，导出对应id的文件夹

## 创建Safari扩展的Xcode项目
打开终端，根据官网的步骤，使用的是命令：

```shell
xcrun safari-web-extension-converter /path/to/extension
```
其中`/path/to/extension` 是上文提到的扩展的目录。

实际可能会找不到`xcrun`，所以使用一下命令：

```shell
xcrun /Applications/Xcode.app/Contents/Developer/usr/bin/safari-web-extension-converter /path/to/extension
```

以上命令会创建一个新的Xcode项目。

## 导出Safari扩展

1.   在Xcode中将Scheme改为macOS。

     ![截屏2023-12-18-12](https://jsd.cdn.zzko.cn/gh/Heyya-x/picx-images-hosting@master/20231218/截屏2023-12-18-12.04.12.3vl4kvnbynls.png)

2.   此处运行前，需要打开Safari中的**允许未签名的拓展**。

     ![截屏2023-12-18-12](https://jsd.cdn.zzko.cn/gh/Heyya-x/picx-images-hosting@master/20231218/截屏2023-12-18-12.05.16.1zuv2k493e1s.png)

1.   编译运行项目后，会弹出`CF Analytics `程序，点击`Quit and Open Safari Extensions Preferences...`。

     ![截屏2023-12-18-12](https://jsd.cdn.zzko.cn/gh/Heyya-x/picx-images-hosting@master/20231218/截屏2023-12-18-12.06.54.4ff6rvq51se8.png)

此时，该扩展已经加入Safari中。
