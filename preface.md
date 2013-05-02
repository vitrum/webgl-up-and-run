

##序言：
=========
最初在1994年，Tim Berners-Lee，也就是Web的奠基人，他公开征集基于在互联网的虚拟现实应用，Mark Pesce和我提交了我们名为”Cyberspace”的论文。当时我们只够买一张机票，所以Mark带着我们的Labyrinth原型去参加在日内瓦举办的第一届全球万维网开发者大会。在拥挤的房间里，Mark高调的宣布：“我们做到了！”

当时我们的演示简单而直接——在窗口中旋转的三维物体，如果点击它，就会打开一个网页浏览器并且跳转到指定的超链接。

几周之后，我们有了邮件列表和VRML（虚拟现实标记语言）。更多开创性的将三维放在互联网上的努力仍然在进行
。
15年过去了，现在浏览器终于开始支持三维，这远超出了Mark和我在当初的构想。VRML是一个严谨构思的语言，可惜出现的太早，当时的网络带宽和显卡等硬件都制约了它。VRML的继任者和模仿者们也遇到了同样的问题，最后都回天乏力。

终于，2009年，历史的车轮转动了：诞生了整个行业都为之兴奋的新标准——WebGL。

时至今日，2012年，WebGL坚强的生存并壮大起来。WebGL真正把3D引入浏览器，支持JavaScript接口调用电脑显卡辅助运算。基于OpenGL ES (主要用于手机和平板电脑显卡的OpenGL 3维图形子集)，它支持市场主流的桌面和移动浏览器。通过使用WebGL ，任何程序员都可以创建令人惊叹的三维网站，并能支持百万用户访问，例如，无需下载的在线三维游戏、大数据可视化应用、产品展示、模拟培训等等举不胜举。

现在已经有几十个在线的WebGL资源分享站，并且有很多的库提供对WebGL的支持，但是这也造成了相关信息的分散和不完整。同时WebGL的API接口相对来说更接近底层，并不适合普通的程序员，它要求开发者有丰富的三维项目开发经验。

但在最初制定标准的前提和共识是，WebGL是一个提供给所有人都能用得上的三维：包括任何有主流硬件配置和现代浏览器的访问者，任何有想象力即使是在用记事本做开发的程序员。

我们需要通过某种方法来弥补开发能力上的差距，通过知识和工具来进行WebGL的实践。

这也就是为什么我要写这本书。

###读者
如果你是一个网站开发人员或者设计师，这本书能让你把WebGL页面跑起来。

本书假定你有HTML、CSS和JavaScript的经验，熟悉jQuery和Ajax。但仅此而已，并不需要三维图形经验。

在第一章有一份简单的三维规则教程，请放心，不需要你是专业三维开发人员。

###本书是如何组织的
本书有三个主要部分，共有8章，和一个附录：

第1和第2章介绍 WebGL API接口，并且介绍Three.js，开源的JavaScript库的编程实例。

第3到第6章通过深入介绍编程图形的细节动画，和互动，探索的WebGL在集成无缝的二三维用户体验中的强大能力。

第7章和第8章将进行WebGL的项目实例，使用内容制作工具和文件格式创建健壮可靠的WebGL应用。第8章里，我们会创建第一个完整的WebGL应用：赛车游戏。

附录A中是参考资源，你可以通过这些资源，了解更多WebGL的发展，WebGL的标准，以及相关的技术和工具。

大部分章节都遵循一个模式：解释一个概念，深入分析一些代码来说明，再回顾之前的知识，然后才继续下一个主题。偶尔我会顺便展开讨论一些我觉得很重要的问题，或者是简单的强调哪些是最佳方案等等。我希望我能在教学和说教当中取得适当的平衡，随时欢迎大家提醒我这一点我已经做到了。

如果你卡在某个例程上，那么建议你先将它抛在脑后，回头再来看它。你可以把概念部分做为一个整体来阅读，等你准备好后再看代码。然后不要犹豫，直接在你喜欢的支持WebGL浏览器里打开例程，然后不断调试修改直到通过。通常，这是最有效的学习方法。

大多数例程中，我使用Three.js开发包，它是一个基于WebGL的优秀开源引擎。在本书开始编写的时候，我不得不为例程使用的引擎作出选择，事实上除了Three.js之外还有一些引擎，它们使用了更多WebGL底层调用，更灵活高效，但是对读者来说并不通俗易懂，很难让人轻易理解并创建应用。我的选择很明确，就是让大家轻松入门快速上手。

如果你有兴趣了解更多WebGL的实现机制，可以参考我们的附录。

附录中收集了一些基于WebGL开发创造的独特和惊人的应用：浏览器里的三维效果，同页面信息的无缝融合，展现全世界信息的混合式应用。在WebGL的平台上，唯一限制你的，就是你的想象力。

WebGL不仅仅是它所有模块的整合，它实现的是一个媒体和全新的游戏体验。WebGL编程刚开始可能并不容易，但是相信我，只要努力钻研，你很快就能发现一个全新的令人兴奋的世界。

###本书中的约定

本书的印刷约定：

*斜体*

表示新的条款，网址，电子邮件地址，文件名和文件扩展名

等宽字体

程序清单，以及段内的程序元素，如变量或函数名，数据库，数据类型，环境变量，语句和关键字

**等宽粗体**

显示命令或其他文本用户应该输入字面上的

***等宽斜体***

显示文本应替换为由用户提供的值或由上下文决定的值

这个图标表示一个提示，建议或一般的注意。

本书的例程文件可以在以下网址获得

https://github.com/tparisi/WebGLBook


