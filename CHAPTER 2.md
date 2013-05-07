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



###设置Three.js

###一个简单的Three.js页面

###一个真实事例

####Shading the Scene

=========
Throughout the book, you will get to know Three.js in detail. For now, here is a summaryof what it has to offer:Three.js hides the details of 3D renderingThree.js abstracts out the details of the WebGL API, representing the 3D scene asmeshes, materials, and lights (i.e., the object types graphics programmers typicallywork with).Three.js is object-orientedProgrammers work with first-class JavaScript objects instead of just making JavaScript function calls.Three.js is feature-richMore than just a wrapper around raw WebGL, Three.js contains many prebuiltobjects useful for developing games, animations, presentations, high-resolutionmodels, and special effects.Three.js is fastThree.js employs 3D graphics best practices to maintain high performance, withoutsacrificing usability.Three.js supports interactionWebGL provides no native support for picking (i.e., knowing when the mousepointer is over an object). Three.js has solid picking support, making it easy to addinteractivity to your applications.Three.js does the mathThree.js has powerful, easy-to-use objects for 3D math, such as matrices, projections, and vectors.Three.js has built-in file format supportYou can load files in text formats exported by popular 3D modeling packages; thereare also Three.js-specific JSON and binary formats.18 | Chapter 2: Your First WebGL ProgramThree.js is extensibleIt is fairly easy to add features and customize Three.js. If you don’t see a data typeyou need, write it and plug it in.Three.js also works with the HTML5 2D canvasAs popular as WebGL has become, it is still not running everywhere. Three.js canalso render most content into a 2D canvas, should the 3D canvas context not beavailable, allowing your code to gracefully fall back to another solution.
It is important to note a few things Three.js doesn’t do. Three.js is not a game engine orvirtual world platform. It lacks some of the commonly used features you would find inthose systems, such as billboards, avatars, and physics. Nor does Three.js have the builtinnetwork support you would expect if you were writing a multiplayer game. If youneed those, you will have to build them yourself on top of Three.js. Still, its power andsimplicity make Three.js a great choice for getting started on your WebGL journey.So, without further ado, let’s get going and write some code!