---
layout: post
title:  Three.js basic - creating and rendering 3D objects in the browser
date:   2021-04-22 15:00:09 GMT+0800
image:  '/images/02/02.jpg'
tags:   [three.js, 3d, blog]
---

![Three.js]({{site.baseurl}}/images/02/threejsorg.jpg)
*Cool projects / [Three.js](https://threejs.org/)*


## Before get started
For this time, I didn't use any bundlers, modules. Because it's just to demonstrate how to create a basic cube in the brower. So all we need is index.html file and two script files.

![Three.js]({{site.baseurl}}/images/02/download.jpg)
*Code-download / [Three.js](https://threejs.org/)*

🔗 <a href="https://threejs.org/">https://threejs.org/</a>
<br>
Hit the download as you see in the above picture and it will give you .zip file


![Three.js]({{site.baseurl}}/images/02/min.jpg)
After you uncompress it, take one file called three.min.js and put into your project directory.

And navigate to the index.html and write those scripts (don't forget to load other scripts before your script)
{% highlight html %}
<body>
    <script src="three.min.js"></script>
    <script src="main.js"></script>
</body>
{% endhighlight %}

Let's test if our script works well by using .log(THREE). That's all we need for now and let's create 3d scene.
{% highlight js%}
// THREE contains most of classes and properties for three.js
// it's uppercase
console.log(THREE);

/* And you can see the object and three.js classes in the console 
Object
ACESFilmicToneMapping: 4
AddEquation: 100
AddOperation: 2
AdditiveAnimationBlendMode: 2501
AdditiveBlending: 2
AlphaFormat: 1021
AlwaysDepth: 1
AlwaysStencilFunc: 519
AmbientLight: class Wl
AmbientLightProbe: class hc
AnimationClip: class qo
AnimationLoader: class extends
AnimationMixer: class Uc
AnimationObjectGroup: class Fc
AnimationUtils: {arraySlice: ƒ, convertArray: ƒ, isTypedArray: ƒ, getKeyframeOrder: ƒ, sortedArray: ƒ, …}
ArcCurve: class ol
*/

{% endhighlight %}


## Creating the scene
* a Scene
* Objects
* a Camera
* a Renderer

#### 1. Scene
{% highlight js%}
//Scene
const scene = new THREE.Scene();
{% endhighlight %}

#### 2. Mesh

🔗 <a href="https://threejs.org/docs/index.html?q=mesh#api/en/objects/Mesh.geometry">Mesh</a>
, class representing triangular polygon mesh based objects. Also serves as a base for other classes such as SkinnedMesh.

{% highlight js%}
//Code ex from three.js documentation

const geometry = new THREE.BoxGeometry( 1, 1, 1 );
const material = new THREE.MeshBasicMaterial( { color: 0xffff00 } );
const mesh = new THREE.Mesh( geometry, material );
scene.add( mesh );
{% endhighlight %}
🔗 <a href="https://threejs.org/docs/index.html?q=box#api/en/geometries/BoxGeometry">BoxGeometry</a>
<br>
🔗 <a href="https://threejs.org/docs/index.html?q=meshbasi#api/en/materials/MeshBasicMaterial">MeshBasicMaterial</a>

My code for mesh and don't forget to add to the scene! always!
{% highlight js%}
//Cube
const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshBasicMaterial({ color: 'blue' });
const mesh = new THREE.Mesh( geometry, material);
scene.add(mesh);

{% endhighlight %}

#### 3. Camera
🔗 <a href="https://threejs.org/docs/index.html?q=camera#api/en/cameras/PerspectiveCamera">PerspectiveCamera</a>, this projection mode is designed to mimic the way the human eye sees. It is the most common projection mode used for rendering a 3D scene.
<br>
<br>
** Arguments
<br>
PerspectiveCamera( fov : Number, aspect : Number, near : Number, far : Number )
fov — Camera frustum vertical field of view.
aspect — Camera frustum aspect ratio.
near — Camera frustum near plane.
far — Camera frustum far plane.
<br>
<br>
** Aspect ratio
<br>
In most cases, the aspect ratio is the width of the canvas divided by its height. (Don't get confused with screen, window. it's viewport)

{% highlight js %}
//Sizes
const sizes = {
    width: 800,
    height: 600
}

//Camera
const camera = new THREE.PerspectiveCamera(75, sizes.width/sizes.height);
scene.add(camera);
{% endhighlight %}

#### 4. Renderer

🔗 <a href="https://threejs.org/docs/index.html?q=renderer#api/en/renderers/WebGLRenderer">WebGLRenderer</a> it takes canvas property.
<br>
First, you need to add 'canvas' tag in your body html.

{% highlight html%}
<body>
    <canvas class="webgl"></canvas>
    <script src="three.min.js"></script>
    <script src="main.js"></script>
</body>
{% endhighlight %}



{% highlight js%}
//Renderer
const canvas = document.querySelector('.webgl');
const renderer = new THREE.WebGLRenderer({
    canvas: canvas
})
{% endhighlight %}

![Three.js]({{site.baseurl}}/images/02/render.jpg)
*screenshot*
Then you will see the render section in the browser, if you open live server. But..wait, it's too samll tho. So we need to define render ratio by using 🔗 <a href="https://threejs.org/docs/index.html?q=render#api/en/renderers/WebGLRenderer.setSize">.setSize()</a> method.
<br>

{% highlight js%}
renderer.setSize(sizes.width, sizes.height);
{% endhighlight %}

![Three.js]({{site.baseurl}}/images/02/render2.jpg)
*screenshot*

And now it's bigger.Then let's move on to render. By usign
🔗 <a href="https://threejs.org/docs/index.html?q=render#api/en/renderers/WebGLRenderer.render">.render()</a> method, we will render scene and camera.
<br>

{% highlight js%}
renderer.render(scene, camera);
{% endhighlight %}

#### what? I can't see anything tho..
As soon as you render it, you will find out nothing is seen on the screen but only the same black box. it' because our camera is set on the 0, 0, 0 axis. Basically, we are right inside cube!

#### Getting position of camera moved

{% highlight js%}
//Camera
const camera = new THREE.PerspectiveCamera(75, sizes.width/sizes.height);
scene.add(camera);
camera.position.z = 4;
camera.position.x = 1;
camera.position.y = 1;
{% endhighlight %}


## Result

#### Finally, we done creating a basic object into our web browser!🔷

![Three.js]({{site.baseurl}}/images/02/cube.jpg)
*3D Cube*

🔗 <a href="https://kimbumi.github.io/threejs/basic/index.html">Demo</a> 