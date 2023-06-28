# 第一个3D案例——创建3D场景


入门`Three.js`的第一步：认识3个基本概念
1. 场景 Scene
2. 相机 Camera
3. 渲染器 Renderer

只要能把第一个3D案例搞明白，后面的学习会非常顺利。

我们开始搭建一个场景，其中包含一个正在旋转的立方体。

## 创建三维场景

可以把三维场景`Scene`对象理解为虚拟的3D场景，用来表示模拟生活中的真实三维场景，或者说是三维世界。

```javascript
// 创建3D场景对象Scene
const scene = new THREE.Scene()
```

## 创建相机

```javascript
// 创建相机
// three.js里有几种不同的相机，在这里，我们使用的是PerspectiveCamera（透视相机）
const camera = new THREE.PerspectiveCamera(
  // 第一个参数：视野角度（FOV）
  75,
  // 第二个参数：长宽比（aspect ratio）
  // 比如，当你在一个宽屏电视上播放老电影时，可以看到图像是被压扁的。
  window.innerWidth / window.innerHeight,
  // 当物体某些部分比摄像机的远截面远或者比近截面近的时候，该这些部分将不会被渲染到场景中。
  0.1, // 近截面（near）
  1000 // 远截面（far）
);
```

## 创建渲染器

```javascript
// 创建渲染器
// three.js同样提供了其它几种渲染器
const renderer = new THREE.WebGLRenderer();
// 设置渲染器的尺寸
renderer.setSize( window.innerWidth, window.innerHeight );
// 将 renderer（渲染器）的dom元素（renderer.domElement）添加到我们的HTML文档中。
// 这就是渲染器用来显示场景给我们看的 <canvas> 元素
document.body.appendChild( renderer.domElement );
```

## 添加立方体
```javascript
// 添加立方体
const geometry = new THREE.BoxGeometry(50, 50, 50);
// 给立方体一个材质，来让它有颜色
const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
// 创建一个Mesh（网格）。网格包含一个几何体以及作用在当前几何体上的材质
const mesh = new THREE.Mesh( geometry, material );
scene.add( mesh ); // 将网格添加到场景中

// 默认情况下，调用scene.add()的时候，物体将会被添加到(0,0,0)坐标。
// 这样会导致相机和立方体在一起。会导致看到的是一片漆黑。
// 为了防止看不到物体，我们只需要将相机稍向外移动一些即可
camera.position.z = 100;
```

## 动画循环
```javascript
// 到这一步，你不会看到任何东西，这是因为我们还没有对它进行真正的渲染。
// 我需要使用一个动画循环
function animate() {
  // requestAnimationFrame有很多的优点。
  // 最重要的一点或许就是当用户切换到其它的标签页时，它会暂停，
  // 因此不会浪费用户宝贵的处理器资源，也不会损耗电池的使用寿命。
  requestAnimationFrame( animate );

  mesh.rotation.y += 0.01; // 让立方体绕Y轴旋转

  // 在每次屏幕刷新时对场景进行绘制，大多数屏幕上，刷新率一般是60次/秒
  renderer.render( scene, camera );
}

animate();
```

到这里，我们可以看到一个绕Y轴旋转的立方体

## 预览地址
https://fejason.github.io/threejs/examples/01-first_3d.html