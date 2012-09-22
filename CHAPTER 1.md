#第一章
##WebGL 概述

水母们一面在水中慢慢的挤着游着，浮浮沉沉，一面还折射着穿过海面的阳光，莹莹闪闪，美丽到让人震惊，这是一个由电脑实时生成的互动海底水母森林。

移动你的鼠标，你可以逐层浏览人体，皮肤、肌肉、血管、骨骼、神经，你还能通过搜索找到感兴趣的器官，并留下书签以做参考。

哦，一个用微博好友和关注者的名字组成的宇宙星系，你不是点错链接跑进了探索星空频道也不是在看星战的电影，这些都是可以运行在你的浏览器里的页面，这就是传说中的WebGL。

附图1－1 WebGL实现的模拟水母 ( http://chrysaora.com/ )，转载自Aleksander Rodic


WebGL是一个在互联网上实现三维图像的新标准。通过使用WebGL，程序员可以使用电脑显卡的全部资源和功能，只需要javascript、浏览器和一个标准的技术构架。在WebGL出现之前，开发三维网页必须依赖插件或者应用程序，而且要求用户下载安装特定软件后才能得到三维体验。

WebGL则是HTML5标准的一个子集，虽然现在还没有通过为官方规则，但是大部分浏览器都已经提供了支持。就象Web Workers、Web Sockets等一样，WebGL是W3C组织的官方建议，同样也是现代浏览器成为一流平台的重要组成部分。

WebGL可以工作在大部分台式机，以及越来越多的移动设备的浏览器。全球数百万台电脑中已经安装了支持WebGL的环境，也许你家里和公司里的电脑现在就可以运行。

WebGL正处在不断成长并且充满活力的系统的核心地位，这个生态系统使得网络体验能获得更加丰富的视觉效果而且更加引人入胜。从游戏开发到数据可视化，从计算机辅助设计到网上零售，现在已经有数以百计的网站、程序和工具正在开发之中。

当然在一开始WebGL API接口的底层工作方式会让人望而却步，不过现在已经有好几个开源的JavaScript库可以让我们避免那些枯燥的引用工作。我会注意不过渡宣扬三维开发的难度，有了这些工具大家能循序渐进的了解WebGL的运作机制。总而言之，这也许是你实现心中那个格斗游戏梦想的机会；或许这是你用眩目的三维网页让老板大开眼界的好机会了。

在这章里，我们会简单介绍WebGL的底层调用，而在其他大部分章节我们会使用一个封装了底层的工具：Three.js , 它会帮我们处理很多体力活。当然为了用好它们，我们仍然需要了解这些工具的实现机制，让我们开始探索的WebGL的的核心概念和API接口吧。

###WebGL的定义

WebGL是由科纳斯组织（Khronos Group）开发和管理的，这个组织还管理着OpenGL、COLLADA等一些你听说过的标准。以下是科纳斯组织网站上对WebGL的官方定义：
WebGL 是免授权费的，跨平台的应用程序接口API，它将OpenGL ES 2.0作为在HTML网页内的3D绘图环境，作为低级别文档对象模型接口开放。它使用OpenGL渲染语言GLSL ES，并可被整洁地与其他3D内容上层或下层的网页内容捆绑。它是使用JavaScript编程开发语言开发适合动态3D网页应用的理想工具，并已被主流互联网浏览器集成。


======================


WebGL is developed and maintained by the Khronos Group, the standards body that
also governs OpenGL, COLLADA, and other specifications you may have heard of. Here
is the official description of WebGL, from the Khronos website:
WebGL is a royalty-free, cross-platform API that brings OpenGL ES 2.0 to the web as a
3D drawing context within HTML, exposed as low-level Document Object Model inter
faces. It uses the OpenGL shading language, GLSL ES, and can be cleanly combined with
other web content that is layered on top or underneath the 3D content. It is ideally suited
for dynamic 3D web applications in the JavaScript programming language, and will be
fully integrated in leading web browsers.
2 | Chapter 1: An Introduction to WebGLhis definition comprises several core ideas. Let’s deconstruct them here:
WebGL is an API
WebGL is accessed exclusively through a set of JavaScript programming interfaces;
there are no accompanying tags like there are with HTML. 3D rendering in WebGL
is analogous to 2D drawing using the Canvas element, in that it is all done through
JavaScript API calls. In fact, access to WebGL is provided using the existing Canvas
element and obtaining a special drawing context specific to WebGL.
WebGL is based on OpenGL ES 2.0
OpenGL ES is an adaption of the long-established 3D rendering standard OpenGL.
The “ES” stands for “embedded systems,” meaning that it has been tailored for use
in small computing devices, most notably phones and tablets. OpenGL ES is the
API that powers 3D graphics for the iPhone, the iPad, and Android phones and
tablets. . WebGL’s designers felt that, by basing the API on OpenGL ES’s small foot
print, delivering a consistent, cross-platform, cross-browser 3D API for the Web
would be more achievable.
WebGL combines with other web content
WebGL layers on top of or underneath other page content. The 3D canvas can take
up just a portion of the page, or the whole page. It can reside inside <div> tags that
are z-ordered. This means that you develop your 3D graphics using WebGL, but all
your other elements are built using familiar old HTML. The browser composites
(combines) all of the graphics on the page into a seamless experience for the user.
WebGL is built for dynamic web applications
WebGL has been designed with web delivery in mind. WebGL starts with OpenGL
ES, but it has been adapted with specific features that integrate well with web
browsers, work with the JavaScript language, and are friendly for web delivery.
WebGL is cross-platform
WebGL is capable of running on any operating system, on devices ranging from
phones and tablets to desktop computers.
WebGL is royalty-free
Like all open web specifications, WebGL is free to use. Nobody will be asking you
to pay royalties for the privilege.
The makers of Chrome, Firefox, Safari, and Opera have committed significant resources
to developing and supporting WebGL, and engineers from these teams are also key
members of the working group that develops the specification. The WebGL specification
process is open to all Khronos members, and there are also mailing lists open to the
public. See Appendix A for mailing list information and other specification resources.
