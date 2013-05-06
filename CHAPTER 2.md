#第二章
##第一个WebGL程序

现在我们已经了解了核心概念，接下来，我希望开发基于WebGL的简单应用，现在是时候使用之前的知识了。
在接下来的一节中，，我们将会创建一个简单的WebGL事例页面，学习如何开发一个完整的程序。开始前，我们先来了解一下我们的技术核心：Three.js

###Three.js 一个JS三维引擎
需求是发明的动力，它不可能一直没被人解决。我们都不希望每次变化都要重复写几百行WebGL代码，都盼着它能被一个库支持，我们可以使用通用得三维编程接口。事实上，已经有多个大牛做到了。我们现在有不少很棒得开源库可以让我们操作WebGL。包括GLGE (http://www.glge.org/), SceneJS (http://www.scenejs.org/), and CubicVR (http://www.cubicvr.org/)。每个库的运行方式有所不同，但他们的目标都一样，既完善原生WebGL对开发人员的用户友好性。

在本书中，我们使用的库是 Three.js 。这个库由巴塞罗那的西班牙程序员Ricardo Cabello Miguel网名Mr.doob创建并维护。Three.js对三维图形中的对象提供了简单直观的操作方法。它的速度很快，并且已经使用在很多非常棒的图形应用项目中。它功能强大，内建多个对象类型和方便的工具。它是开源软件，其代码已上GitHub，并且管理良好，有许多程序员在帮助Mr.doob。


=========
I chose Three.js to write the examples in this book for a couple of reasons. First, I amcurrently using it in my own development projects and really like it. Second, it is quitepopular among these engines and is the perceived leader. You may find other libraries more to your liking, or better suited to the needs of your application. That’s OK. Onesize definitely does not fit all here. The other engines I mentioned are great and havetheir place. You may even want to build your own engine if that’s how you roll. But beforeyou do, you should take a look at the great engine work already being done for WebGL.