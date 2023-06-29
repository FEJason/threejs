# 使用three.js实现全景图查看

## 创建场景、相机
```javascript
// 场景
scene = new THREE.Scene();

// 相机
camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 1, 1100 );
// 初始相机位置
// 这里想要全景图显示初始位置，设置 x 0.01
camera.position.set(0.01, 0, 0);

```

## 创建球，并贴图

```javascript
/**
 *  创建球:
 *	radius — 球体半径，默认为1。
 *	widthSegments — 水平分段数（沿着经线分段），最小值为3，默认值为32。
 *	heightSegments — 垂直分段数（沿着纬线分段），最小值为2，默认值为16。
*/
const geometry = new THREE.SphereGeometry( 100, 80, 80 );
geometry.scale( - 1, 1, 1 ); // 反转x轴上的几何图形，使所有面都指向内侧

// 加载材质
const texture = new THREE.TextureLoader().load( 'textures/panorama/2294472375_24a3b8ef46_o.jpg' );
const material = new THREE.MeshBasicMaterial( { map: texture } );

const mesh = new THREE.Mesh( geometry, material ); // 创建网格，将全景图贴在球上

scene.add( mesh ); // 将网格添加到场景

```

## 创建渲染器

```javascript
renderer = new THREE.WebGLRenderer(); // 渲染器
renderer.setPixelRatio( window.devicePixelRatio ); // 设置像素比率
renderer.setSize( window.innerWidth, window.innerHeight ); // 设置渲染器大小
container.appendChild( renderer.domElement ); // 将渲染器添加到容器元素中
```

## 添加轨道控制器

```javascript
// 添加轨道控制器，可以使得相机围绕目标进行轨道运动
const controls = new OrbitControls(camera, container);
controls.rotateSpeed = -0.25; // 修正方向
```

## 动画渲染
```javascript
// 动画渲染
function animate() {
  requestAnimationFrame( animate );
  
  renderer.render( scene, camera );
}
```

## 预览地址
https://fejason.github.io/threejs/examples/02-全景图查看.html