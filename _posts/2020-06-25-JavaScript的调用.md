---
layout: post
title: JavaScript的调用
subtitle: 尝试在静态网页中调用JavaScript脚本
date: 2020-06-25
author: Unique_缪缪
header-img: img/post-bg-keybord.jpg
catalog: true
tags:
- 设计心得
---
 偶尔在知乎上看到了[3D-元素周期表](https://mumium.github.io/3d-periodic-table.html)，效果十分酷炫。

<img src="https://raw.githubusercontent.com/mumium/picture-bed/master/img/20200625121659.png" style="zoom:67%;" />

可以选择4种元素排列形式，过渡动画十分细腻流畅，于是玩了好久🙈，我已经将其放在我的博客下，想玩的同学可以点击上方的超链接进入，而且手机端也可以玩。

然后简单研究了一下，里面的特效依托于4个JavaScript脚本：

*three.min.js*

*tween.min.js*

*TrackballControls.js*

*CSS3DRenderer.js*

[three.js](https://github.com/mrdoob/three.js/) 是JavaScript编写的WebGL第三方库，是HTML中的3D引擎，可以实现在浏览器中运行三维场景，也是GitHub中的开源项目，作者为mrdoob。

<img src="https://raw.githubusercontent.com/mumium/picture-bed/master/img/20200625121108.png" style="zoom:67%;" />

于是尝试把这个周期表放到博客主页上，本以为找到4个js文件，添加代码就能完成的简单工作，没想到遇到了许多麻烦= =

### 工作流程

首先寻找源代码和4个js文件，辗转了许久后发现有不少人已经把源码挂在了GitHub上，且都是中文索引的。

<img src="https://raw.githubusercontent.com/mumium/picture-bed/master/img/20200625121217.png" style="zoom:67%;" />

于是随便找了一个fork，得到想要的东西后，将4个js文件放到博客js文件夹下，将源码稍加修改放到根目录下。我最初的想法是在博客首页专门添加一个菜单，将周期表放在菜单链接的新网页中，但随后碰到了数个问题：

* html文件放在根目录下无法生成菜单

  解：需要符合菜单的格式，加上模板代码后成功生成

* 进入页面后，发现页面保留了头部背景图、大标题和底部版权文字，无法显示3D模块

  解：目测是模板代码的样式问题，新建立了一个nulldefault的页面样式，将背景图、底部文字的部分代码去除后，用此样式替换原样式，提交后查看效果，果然除了页面标题，其余只剩下了黑乎乎一片，但还是不能显示3D模块
  
* 3D模块不能显示，推测是代码中相对路径书写错误，或博客页面默认不能加载JavaScript两种情况。

  解：GitHub中其他人的代码路径也是同样的书写方式，可以加载模块，所以不是相对路径的问题。
  
  

 那问题的关键应该是博客模板不能加载JavaScript。于是放弃在首页增加菜单的方式，改用超链接在本地链接静态网页。

尝试之后JavaScript加载成功：

<img src="https://raw.githubusercontent.com/mumium/picture-bed/master/img/QQ%E6%88%AA%E5%9B%BE20200625162713.png" style="zoom:67%;" />

点击首页这里就可以进入

