#1. 实现一个两栏布局，右侧固定宽度200px，左侧自适应宽度，附上预览链接。
[浮动布局](http://js.jirengu.com/lamaziceta/1/edit?html,css,output "null")
[使用 flex 布局](http://js.jirengu.com/lexix/edit?html,css,output "null")

#2. 实现一个三栏布局，两侧固定宽度200px，中间宽度自适应撑满，附上链接。
[浮动布局](http://js.jirengu.com/cerukusalo/1/edit?html,css,output "null")
[flex 布局](http://js.jirengu.com/xedax/edit?html,css,output "null")

#3. css reset 是什么？css 预编译器是什么？ 后编译器(post css)是什么？
- CSS Reset就是之前的样式我不要，a{color: red;}，抛弃默认样式

- CSS 预处理器用一种专门的编程语言，进行 Web 页面样式设计，然后再编译成正常的 CSS 文件，以供项目使用。CSS 预处理器为 CSS 增加一些编程的特性，无需考虑浏览器的兼容性问题

- PostCSS 本身是一个功能比较单一的工具。它提供了一种方式用 JavaScript 代码来处理 CSS。它负责把 CSS 代码解析成抽象语法树结构（Abstract Syntax Tree，AST），再交由插件来进行处理。插件基于 CSS 代码的 AST 所能进行的操作是多种多样的，比如可以支持变量和混入（mixin），增加浏览器相关的声明前缀，或是把使用将来的 CSS 规范的样式规则转译（transpile）成当前的 CSS 规范支持的格式。PostCSS 的主要功能只有两个：第一个就是前面提到的把 CSS 解析成 JavaScript 可以操作的 AST，第二个就是调用插件来处理 AST 并得到结果。




