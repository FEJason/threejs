# 开发和学习环境，引入 three.js 库

1. 开发环境：项目开发引入`three.js`，比如`vue`或者`react`
2. 学习环境：入门`three.js`阶段，`.html`文件中直接引入`three.js`

## 项目开发环境

`npm`安装特定版本`three.js`（注意使用哪个版本，查文档就查对应的版本）

下载安装146版本

```sh
$ npm install three@0.146.0
```

`npm`安装后，引入

```javascript
// 引入three.js
import * as THREE from 'three'
```

除了`three.js`核心库以外，在`three.js`文件包中`examples/jsm`目录下，还有各种不同功能的扩展库。

在项目中用到哪个扩展库，引入

```javascript
// 引入控制器 OrbitControls.js
import { OrbitControls } from 'three/addons/controls/OrbitControls.js'

// 引入 GLTFLoader.js ，用于加载.gltf模型文件
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js'
```

```javascript
// 扩展库引入——旧版本，比如122，新版路径addons替换了examples/jsm
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js'
```

## 学习环境：.html 文件中直接引入 three.js

在学习`three.js`时，完全没必要用`webpack`或`vite`搭建一个开发环境。

学习环境，只需创建一个`.html`文件，编写`three.js`代码，最后通过本地静态服务器打开`.html`文件就行。

## script 标签方式引入 three.js

学习中通过`script`标签把`three.js`当做一个 js 库引入项目即可。

```javascript
<script src="./build/three.js"></script>

<script>
// 随便输入一个API，测试是否已经正常引入three.js
console.log(THREE.Scene)
</script>
```

## ES6 import 方式引入（推荐）

给`script`标签设置`type="module"`，也可以在`.html`文件中使用`import`方式引入`three.js`

```javascript
<script type="module">
// 现代浏览器支持ES6语法，自然包括import方式引入js文件
import * as THREE from './build/three.module.js'
</script>
```

## type="importmap"配置路径

学习环境中，`.html`文件引入`three.js`，最好的方式就是参考`three.js`官方案例，通过配置`<script type="importmap">`，实现和`vue`或`react`脚手架开发环境一样的写法。这样在实际项目开发中可以直接复制引入代码。

```javascript
<script type="importmap">
  {
    "imports": {
      "three": "../three.js/build/three.module.js"
    }
  }
</script>

<script type="module">
import * as THREE from 'three'
// 浏览器控制台测试，是否引入成功
console.log(THREE.Scene)
</script>

```