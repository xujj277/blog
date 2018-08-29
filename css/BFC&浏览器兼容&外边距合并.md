# 1. BFC 是什么？如何生成 BFC？BFC 有什么作用？举例说明。
i. BFC 即 Box Formatting Context，每个渲染区域用formatting context表示，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。
块级格式化上下文，创建了BFC的元素就是一个独立的盒子，盒子里布局不受外部影响，也不影响外部元素的布局。

ii. 1.根元素
2.float的属性不为none
3.position为absolute或fixed
3.display为inline-block，flex或者inline-flex
4.overflow不为visible

iii. 1.解决外边距合并问题。[http://js.jirengu.com/maseneyava/1/edit](http://js.jirengu.com/maseneyava/1/edit "null")
2.清理浮动。[http://js.jirengu.com/cofevimoce/1/edit?html,css,output](http://js.jirengu.com/cofevimoce/1/edit?html,css,output "null")

# 2. 在什么场景下会出现外边距合并？如何合并？如何不让相邻元素外边距合并？
一，1,相邻元素合并。2.父子合并。3.自己合并。

二， 当两个外边距都是正数时，取两者之中的较大者；当两个外边距都是负数时，取两者之间绝对值较大者；当两个外边距一正一负时，取的是两者的和。

三，1.设置浮动元素float，但添加了浮动的特性，位置发生变化。
2.最好是不要管合并的问题，都统一用magin-top等。

# 3. 什么是 CSS hack？在哪个网站查看标签(属性)的浏览器兼容情况。
由于不同厂商的浏览器，比如Internet Explorer,Safari,Mozilla Firefox,Chrome等，或者是同一厂商的浏览器的不同版本，如IE6和IE7，对CSS的解析认识不完全一样，因此会导致生成的页面效果不一样，得不到我们所需要的页面效果。

这个时候我们就需要针对不同的浏览器去写不同的CSS，让它能在不同的浏览器中也能得到我们想要的页面效果。

实际项目中CSS Hack大部分是针对IE浏览器不同版本之间的表现差异而引入的。

[https://caniuse.com/](https://caniuse.com/ "null")

# 4. 渐进增强和优雅降级分别是什么意思？
- 渐进增强(progressive enhancement): 针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验

- 优雅降级 (graceful degradation): 一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。

# 5.以下工具/名词是做什么的？

- 条件注释：(conditional comment) 是于HTML源码中被IE有条件解释的语句。条件注释可被用来向IE提供及隐藏代码。

- IE Hack：主要是针对ie浏览器不同版本的特性，编写适应兼容不同ie浏览器的代码方案

- js 能力检测：测检测浏览器是否支持某种特定的能力，然后给出特定的解决方案。

- html5shiv.js：用于解决ie低版本浏览器对HTML5新增标签不识别导致CSS不起作用的脚本。

- respond.js：模拟css3的媒体查询，主要是解决ie低版本浏览器不支持媒体查询，解决低版本浏览器的响应式问题

- css reset：CSS Reset用来清除所有浏览器默认样式，这样更易于保持各浏览器渲染的一致性。

- normalize.css：对normalize.css进行引用，可以让不同浏览器在渲染的时候样式更加统一，为浏览器的渲染方式提供了高度一致性。
Normalize.css 只是一个很小的CSS文件，但它在默认的HTML元素样式上提供了跨浏览器的高度一致性。相比于传统的CSS reset，Normalize.css是一种现代的、为HTML5准备的优质替代方案。Normalize.css现在已经被用于Twitter Bootstrap、HTML5 Boilerplate、GOV.UK、Rdio、CSS Tricks 以及许许多多其他框架、工具和网站上。

- Modernizr：Modernizr是一个检测用户浏览器HTML5和CSS3能力的JavaScript库。Modernizr在页面加载时快速运行来检测功能，然后创建一个保存检测结果的JavaScript对象，接着页面中的html标签上添加一系列class属性来接通你的CSS。

- postCSS：一个使用 JS 插件来转换 CSS 的工具。这些插件可以支持使用变量，混入(mixin)，转换未来的 CSS 语法，内联图片等操作。PostCSS使CSS变成JavaScript的数据，使它变成可操作。PostCSS是基于JavaScript插件，然后执行代码操作。PostCSS自身并不会改变CSS，它只是一种插件，为执行任何的转变铺平道路。