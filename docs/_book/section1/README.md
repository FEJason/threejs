# Three.js 文件包下载和目录简介

学习`Three.js`之前，先做一些必要的准备工作，下载`Three.js`官方文件包，`Three.js`官方文件包提供了很多有用的学习资源。

## Three.js 版本问题

`Three.js`处于飞速迭代中，过去几年和现在`Three.js`基本上每个月都会发布一个新的版本，主要是增加一些新的功能，也可能废弃或更名某些`API`。

在开发中一般会固定`Three.js`版本号，防止有大的更新影响到项目中使用的`API`

[Three.js 官网](https://threejs.org/)可以下载`Three.js`文件包，不过默认是最新版本的，`Three.js`官网的文档一般也是当前最新版本。

## Three.js 官方文件包所有版本下载地址

https://github.com/mrdoob/three.js/releases/

在这里可以下载到对应版本的文件包

## 如何在本地预览任何你想要的版本文档

比如我现在用的版本是 146

打开官方文件下载地址：https://github.com/mrdoob/three.js/releases/

选择需要的版本文件包下载，然后解压，就可以预览里面的很多学习资源

## Three.js 文件资源目录介绍

```
three.js 文件包
  |-- build            three.js相关库文件
  |-- docs             文档
  |-- examples         案例
  |-- src              three.js源码，有兴趣可以阅读
```

## 本地静态服务器

预览文档、案例的时候需要使用静态服务器。

作为前端工程师，大家都知道，web 项目开发，往往会用`webpack`或`vite`或者其它方式搭建一个开发环境。

如果是学习`three.js`的话，没必要这么麻烦，最简单的方法，比如使用`vscode`安装`live-server`插件即可。

如果你想预览代码 3D 效果，打开对应`.html`文件，右键点击`Open with Live Server`即可

## 扩展：nodejs 配置本地静态服务器

如果不用代码编辑器创建本地静态服务器，也可以用`nodejs`配置

全局安装`live-server`

```sh
$ npm install live-server -g
```

安装后，进入`Three.js`官方文件跟目录，输入`live-server`命令即可预览
