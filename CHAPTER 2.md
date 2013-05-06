#第二章
##第一个WebGL程序

现在我们已经了解了核心概念，接下来，将开发基于WebGL的简单应用，现在是时候使用之前的知识了。
在接下来的一节中，，我们将会创建一个简单的WebGL事例页面，学习如何开发一个完整的程序。开始前，我们先来了解一下我们的技术核心：Three.js

###Three.js 一个JS三维引擎
需求是发明的动力，它不可能一直没被人解决。我们都不希望每次变化都要重复写几百行WebGL代码，都盼着它能被一个库支持，我们可以使用通用得三维编程接口。事实上，已经有多个大牛做到了。我们现在有不少很棒得开源库可以让我们操作WebGL。包括GLGE (http://www.glge.org/), SceneJS (http://www.scenejs.org/), and CubicVR (http://www.cubicvr.org/ )。每个库的运行方式有所不同，但他们的目标都一样，既完善原生WebGL对开发人员的用户友好性。

在本书中，我们使用的库是 Three.js 。这个库由巴塞罗那的西班牙程序员Ricardo Cabello Miguel网名Mr.doob创建并维护。Three.js对三维图形中的对象提供了简单直观的操作方法。它的速度很快，并且已经使用在很多非常棒的图形应用项目中。它功能强大，内建多个对象类型和方便的工具。它是开源软件，其代码已上GitHub，并且管理良好，有许多程序员在帮助Mr.doob。

我选择在本书中使用Three.js有两个原因，一是我自己目前使用它开发项目而且很喜欢它。二是现在它比其它库都要流行，已经被认为是事实上的领导者了。也许你会觉得更喜欢其它库，或者更适合你的项目。这没问题，作者的一点小不适应不代表它们不好。我相信它们都有各自的价值。甚至你也可以按照你的理解开发自己的引擎，但在此之前，还是请你看看现在已经完成的WebGL的伟大实现吧。

>象Three.js这样的库之所以能称为现实，是因为，不少网页浏览器在近几年里越来越多提供了强大的JavaScript虚拟机。在几年前，虚拟机的性能让实现三维引擎艰难到让人望而却步，甚至使用WebGL的机会都很渺茫。值得庆幸的是，现在虚拟机速度提升，并且有了类似Three.js的库，在我们这个星球上，已经有数百万的开发者可以使用WebGL了。

=========
I chose Three.js to write the examples in this book for a couple of reasons. First, I amcurrently using it in my own development projects and really like it. Second, it is quitepopular among these engines and is the perceived leader. You may find other libraries more to your liking, or better suited to the needs of your application. That’s OK. Onesize definitely does not fit all here. The other engines I mentioned are great and havetheir place. You may even want to build your own engine if that’s how you roll. But beforeyou do, you should take a look at the great engine work already being done for WebGL.
The fact that toolkits like Three.js exist at all is due, in no small part, tohow powerful web browsers’ JavaScript virtual machines (VMs) havebecome in recent years. A few years back, VM performance would havemade implementing such libraries prohibitive, and perhaps even madeWebGL a nonstarter for practical use. Thankfully, today’s VMs scream,and, with libraries like Three.js, WebGL has been made accessible tothe millions of web developers on the planet.