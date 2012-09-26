#第一章
##WebGL 概述

水母们一面在水中慢慢的挤着游着，浮浮沉沉，一面还折射层层阳光，莹莹闪闪，美丽到让人震惊，这是一个由电脑实时生成的互动海底水母森林。

移动你的鼠标，你可以逐层浏览人体，皮肤、肌肉、血管、骨骼、神经，你还能通过搜索找到感兴趣的器官，并留下书签以做参考。

哦，这是一个用微博好友和关注者的名字组成的宇宙星系，你可不是点错链接跑进了探索星空频道，也不是在看星战的电影，这些都是可以运行在你的浏览器里的页面，这就是传说中的WebGL。

附图1－1 WebGL实现的模拟水母 ( http://chrysaora.com/ )，转载自Aleksander Rodic


WebGL是一个在互联网上实现三维图像的新标准。通过使用WebGL，程序员可以使用电脑显卡的全部资源和功能，只需要javascript、浏览器和一个标准的技术构架。在WebGL出现之前，开发三维网页必须依赖插件或者应用程序，而且要求用户下载安装特定软件后才能得到三维体验。

WebGL是HTML5标准的一个子集，虽然现在不是官方规则，但是大部分浏览器都已经提供了支持。就象Web Workers、Web Sockets等一样，WebGL是W3C组织的官方建议，同样也是现代浏览器成为一流平台的重要组成部分。

WebGL已经工作在大部分电脑，以及越来越多的移动设备的浏览器上。全球数百万台电脑中已经安装了支持WebGL的环境，也许你家里和公司里的电脑现在就能运行。

WebGL正处在不断成长并且充满活力的系统的核心地位，这个生态系统使得网络体验能获得更加丰富的视觉效果而且更加引人入胜。从游戏开发到数据可视化，从计算机辅助设计到网上零售，现在已经有数以百计的三维网站、程序和工具正在开发之中。

当然在一开始WebGL的API接口底层工作方式会让人望而却步，不过现在已经有好几个开源的JavaScript库可以让我们避免那些枯燥的引用工作。我会注意不过渡宣扬三维开发的难度，有了这些工具大家能循序渐进的了解WebGL的运作机制。总而言之，这也许是你实现心中那个格斗游戏梦想的机会；或许这是你用眩目的三维网页让老板大开眼界的好机会了。

在这章里，我们会简单介绍WebGL的底层调用，而在其他大部分章节我们会使用一个封装了底层的工具：Three.js , 它会帮我们处理很多体力活。当然为了用好它们，我们仍然需要了解这些工具的实现机制，让我们开始探索的WebGL的的核心概念和API接口吧。

###WebGL的定义

WebGL是由科纳斯组织（Khronos Group）开发和管理的，这个组织还管理着OpenGL、COLLADA等一些著名标准。以下是科纳斯组织网站上对WebGL的官方定义：

*WebGL 是免授权费的，跨平台的应用程序接口API，它将OpenGL ES 2.0作为在HTML网页内的3D绘图环境，作为低级别文档对象模型接口开放。它使用OpenGL渲染语言GLSL ES，并可被整洁地与其他3D内容上层或下层的网页内容捆绑。它是使用JavaScript编程开发语言开发适合动态3D网页应用的理想工具，并已被主流互联网浏览器集成。*

这个定义包含了以下几个核心思想：
####WebGL是个API
WebGL完全是通过特定的JavaScript接口访问，而没有新增HTML标签。WebGL的三维渲染使用二维渲染也使用的Canvas元素，它是通过JavaScript API调用。实际上，WebGL的机制就是通过上下文，在Canvas元素上做特定的图像渲染。

####WebGL基于OpenGL ES 2.0
OpenGL ES是从 OpenGL 裁剪定制而来的，ES表示嵌入式系统（embedded systems）。意指其针对多种嵌入式系统专门设计，它已应用与大部分手机和平板。OpenGL ES更是iPhone、iPad、Android等平板的三维力量之源。基于OpenGL ES的低能耗，WebGL的设计者们认为，提供一个一致的、跨平台、跨浏览器的三维API接口是可以实现的。

####WebGL能融入页面
显示WebGL的层可以设置在其他层的上方或者下方。 三维画布可以只是部分的页面，也可以整个页面。它所在的\<div\>标签能通过Z-index排序。这意味着，您可以用WebGL开发三维图形，而页面里其他元素都使用原来的HTML。浏览器会把网页上的图形有机的整合在一起，让用户得到无缝的体验。

####WebGL为动态网页而生
WebGL在设计时就已经考虑到网页交互。虽然起源与OpenGL ES，但它定制了特别的功能，能很好适应网页浏览器和JavaScript，提供友好的网页交互。

####WebGL就是跨平台
WebGL能够运行在任何操作系统上，设备上，从手机和平板电脑台式电脑。

####WebGL完全免费
就象所有开放式网络规范一样，WebGL是免费使用的。没人能跑来问您收取特许权使用费。

Chrome，火狐，Safari和Opera等浏览器的开发商都致力于开发和提供支持WebGL的重要资源，并且这些团队的工程师也是工作组的主要成员，他们参与编写规范。 WebGL的规范流程是开放给所有科纳斯组织成员的，并提供向公众开放的邮件列表。如您需要，请参阅附录A中的邮件列表信息和其他规范资源。


###三维图形--一个惊雷
“数学太难了！”--芭比娃娃。这是句臭名昭著的性别歧视者常说的话，事实上，我和芭比的感觉一样，希望能通过沉迷在购物来治疗在三维开发中受的伤。哪些数学运算实在太难了！幸运的是，你不需要成为数学神童才能理解WebGL；我们有一个库可以替我们干那些麻烦的运算，我们可以省下时间撮火球了！不过在开始用之前，我们还是要了解一下在渲染引擎之下发生的事情，这挺重要的。以下几页内容是我总结的三维图形基础。





=============================================
3D Coordinate Systems
3D drawing takes place, not surprisingly, in a 3D coordinate system. Anyone familiar
with 2D Cartesian coordinate systems such as you find on graph paper, or in the window
coordinates of an HTML document, knows about x and y values. These 2D coordinates
define where <div> tags are located on a page, or where the virtual “pen” or “brush”
draws in the case of the HTML Canvas element. Similarly, 3D drawing takes place in a
3D coordinate system, where there is an additional coordinate, z, which describes depth
(i.e., how far into or out of the screen an object is drawn). The WebGL coordinate system
is arranged as depicted in Figure 1-2, with x running horizontally left to right, y running
vertically bottom to top, and positive z coming out of the screen.
If you are already comfortable with the concept of the 2D coordinate system, I think the
transition to a 3D coordinate system is pretty straightforward. However, from here on,
things get a little complicated.
