#第二章
##第一个WebGL程序

现在我们已经了解了核心概念，接下来，将开发基于WebGL的简单应用，现在是时候使用之前的知识了。
在接下来的一节中，，我们将会创建一个简单的WebGL事例页面，学习如何开发一个完整的程序。开始前，我们先来了解一下我们的技术核心：Three.js

###Three.js 一个JS三维引擎
需求是发明的动力，它不可能一直没被人解决。我们都不希望每次变化都要重复写几百行WebGL代码，都盼着它能被一个库支持，我们可以使用通用得三维编程接口。事实上，已经有多个大牛做到了。我们现在有不少很棒得开源库可以让我们操作WebGL。包括GLGE (http://www.glge.org/), SceneJS (http://www.scenejs.org/), and CubicVR (http://www.cubicvr.org/ )。每个库的运行方式有所不同，但他们的目标都一样，既完善原生WebGL对开发人员的用户友好性。

在本书中，我们使用的库是 Three.js 。这个库由巴塞罗那的西班牙程序员Ricardo Cabello Miguel网名Mr.doob创建并维护。Three.js对三维图形中的对象提供了简单直观的操作方法。它的速度很快，并且已经使用在很多非常棒的图形应用项目中。它功能强大，内建多个对象类型和方便的工具。它是开源软件，其代码已上GitHub，并且管理良好，有许多程序员在帮助Mr.doob。

我选择在本书中使用Three.js有两个原因，一是我自己目前使用它开发项目而且很喜欢它。二是现在它比其它库都要流行，已经被认为是事实上的领导者了。也许你会觉得更喜欢其它库，或者更适合你的项目。这没问题，作者的一点小不适应不代表它们不好。我相信它们都有各自的价值。甚至你也可以按照你的理解开发自己的引擎，但在此之前，还是请你看看现在已经完成的WebGL的伟大实现吧。

>象Three.js这样的库之所以能称为现实，是因为，不少网页浏览器在近几年里越来越多提供了强大的JavaScript虚拟机。在几年前，虚拟机的性能让实现三维引擎艰难到让人望而却步，甚至使用WebGL的机会都很渺茫。值得庆幸的是，现在虚拟机速度提升，并且有了类似Three.js的库，在我们这个星球上，已经有数百万的开发者可以使用WebGL了。

通过本书，你将会了解Three.js的细节。现在这里是其提供的功能简介：
* Three.js隐藏了三维渲染的细节
* Three.js抽象出WebGL的API细节，提供三维场景的网格，材质和光照等（这些对象是图形程序员日常操作的对象）
* Three.js是面向对象的。
    程序员开始使用JavaScript类对象而不仅仅局限使用JavaScript函数调用。
* Three.js功能丰富
    不仅是封装了WebGL，Three.js保函很多预设对象，可用于开发游戏、动画、演示文档、高分辨率的模型和特效。
* Three.js快
    Three.js使用三维图形的最佳实践，在不牺牲可用性的基础上保持尽可能高的性能。
* Three.js支持互动
    原生WebGL中并为提供采集支持（即何时鼠标指向一个对象）。Three.js提供了响应，使你可以更容易的在程序中添加交互。
* Three.js完成数学运算
    Three.js提供强大宜用的对象帮你完成三维运算，例如矩阵、投影和向量。
* Three.js支持多种文件格式
    你可以加载由各种流行三维建模软件导出的文本格式文件，也可以使用Three.js制定的JSON和二进制格式。
* Three.js使可扩展的
    给Three.js增加功能和定制很容易。如果你发现有的数据类型不支持，你可以自己写并作为插件使用。
* Three.js也可以和HTML5的二维canvas一起工作
    虽然现在WebGL正值当红，但它不是适合所有场合。在三维canvas不能使用时，Three.js也能提供二维canvas内容。让代码能优雅降级到另一种解决方案。
    
请注意有几件事是Three.js不做的：
Three.js不是一个游戏引擎或者虚拟世界平台。它缺少在其它系统中常见的功能，如：告示、头像、物理。如果你在编写一个多人网游，你会发现没有期待中的内置网络支持等。如果你需要这些，你将不得不在Three.js上自己开发。尽管如此，用简单而强大的Three.js开始我们的WebGL旅程仍然不失为一个伟大的选择。

因此，事不宜迟，让我们去写hello world吧！（笑）

###设置Three.js

你需要做的第一件事，就是从GitHub上下载最新的Three.js。截至撰写本文时，Three.js库URL是https://github.com/mrdoob/three.js/。下载完Git后，你会发现压缩过的精简版是在 build/Three.js。完整源文件是在src目录中。API文档在GitHub上，不过文档都是很基础的介绍，所以你可能会需要保留源文件方便将来参考。

>Three.js是使用Google Closure 编译发布的，这个包中包含了Three.js库的几个单独的源文件。如果你不了解Closure，想了解更多，请去http://code.google.com/closure/compiler/。如果你不想去知道这些细节，你现在可以把Three.js当成一个黑盒子。

花点时间了解源文件和文档会让你熟悉Three.js。

当然你也可能象我一样打算忽略这些，因为你已经忍不住要开始折腾了。好吧，在此之前，请至少看看我为本书做的例程。

在examples目录中，有近100个WebGL和几个二维canvas演示，它们涵盖了一系列的功能和效果。

你不会后悔的。

最后，所有例程要放在Web服务器上。本书的大部分程序页面需要你放在服务器上才能访问。

我是用我的MacBook上的LAMP来存放页面的，其实你需要的是A，也就是例如Apache之类的网页服务器。

###一个简单的Three.js页面

现在可以开始了，这次是第一个WebGL程序。从这个练习中，你会看到，使用Three.js是很简单的。例2－1是第一章中画方形离子的更新版，但是只有30行，而不是150行，现在代码大大的精炼了。

*例2－1 一个简单的Three.js 页面*

    <!DOCTYPE html>
    <html>
    <head>
        <title>A Simple Three.js Page</title>
        <script src="../libs/Three.js"></script>
        <script>
            function onLoad()
            {
                // Grab our container div
                var container = document.getElementById("container");
                // Create the Three.js renderer, add it to our div
                var renderer = new THREE.WebGLRenderer();
                renderer.setSize(container.offsetWidth, container.offsetHeight);
                container.appendChild( renderer.domElement );
                // Create a new Three.js scene
                var scene = new THREE.Scene();
                // Create a camera and add it to the scene
                var camera = new THREE.PerspectiveCamera( 45,
                container.offsetWidth / container.offsetHeight, 1, 4000 );
                camera.position.set( 0, 0, 3.3333 );
                scene.add( camera );
                // Now, create a rectangle and add it to the scene
                var geometry = new THREE.PlaneGeometry(1, 1);
                var mesh = new THREE.Mesh( geometry,
                new THREE.MeshBasicMaterial( ) );
                scene.add( mesh );
                // Render it
                renderer.render( scene, camera );
            }
        </script>
    </head>
    <body onLoad="onLoad();">
        <div id="container" style="width:500px; height:500px; background-color:#000000">
            20 | Chapter 2: Your First WebGL Program
        </div>
    </body>
    </html>

我们来看看它是怎么工作的。

首先，我们通过<script>调用了Three.js库。

接下来我们通过脚本画出了正方形。整个程序包含在一个onLoad()函数中，通过页面的onload时间出发。

在函数中，我们首先找到需要WebGL渲染的页面元素，并将其保存在变量里。然后我们初始化Three.js渲染对象。渲染器负责所有的Three.js绘图（当然是指WebGL）。

###一个真实事例

####Shading the Scene

=========
Then, we supply our script that draws the square. The entire program is contained in asingle function, onLoad(), triggered by the page’s onLoad event.In the body of the function, we first find the page element that we are going to use torender the WebGL, and save that in the variable container. Then, we initialize theThree.js renderer object. The renderer is responsible for all Three.js drawing (via WebGLcontext, of course). We construct the renderer object, size it to the same size as thecontainer, and add it as a DOM child element of the container.Next, we create a scene. The scene is the top-level object in the Three.js graphics hierarchy. It contains all other graphical objects. (In Three.js, objects exist in a parent-childhierarchy. More on this in later chapters.) Once we have a scene, we are going to add acouple of objects to it: a camera and a mesh. The camera defines where we are viewingthe scene from: in this example, we use a transform to set its position property to 3.3333units (a little bit back) from the origin. Our mesh is composed of a geometry object anda material. For geometry, we are using a 1 × 1 rectangle created with the Three.jsPlaneGeometry object. Our material tells Three.js how to shade the object. In this example, our material is of type MeshBasicMaterial (i.e., just a single simple color witha default value of pure white). Three.js objects have a default position of 0, 0, 0, so ourwhite rectangle will be placed at the origin.Finally, we need to render the scene. We do this by calling the renderer’s render()method, feeding it a scene and a camera.