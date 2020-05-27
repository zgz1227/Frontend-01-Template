# CSSLayout、渲染、CSS基础机制

## CSS Layout之 布局方式详解

```text
常见的布局有几种样式：传统盒模型布局、flex 布局、gird 网格布局

-[CSS 常见布局方式](https://juejin.im/post/599970f4518825243a78b9d5)

> 传统盒模型布局

- 盒子模型分为：普通盒子模型和怪异盒子模型
- 盒模型布局主要是使用 display 属性（文档流布局） + position 属性（定位布局） + float 属性（浮动布局）

> flex 布局样式属性汇总：

- react-native 已经实现了**只用**flex 来进行页面布局

- 作用在父容器上的属性：

  - flex-direction: row | row-reverse | column | column-reverse // 控制主轴的方向
  - flex-wrap: wrap | nowrap | wrap-reverse // 控制主轴上元素的换行方式
  - justify-content: center | flex-start | flex-end | space-between | space-around | space-evenly // 控制主轴上元素的对齐方式
  - align-items: center | flex-start | flex-end | stretch | baseline // flex 子项们相对于 flex 容器在垂直方向上的对齐方式
  - align-content: center | flex-start | flex-end | space-between | space-around | space-evenly // 控制垂直方向每行的对齐方式（只有多行的情况下才会起作用）

- 作用在子容器上的属性：
  - align-self 属性，可以覆盖父元素上的 align-items 属性
  - flex 是 flex-grow,flex-shrink,flex-basis 的简写

> gird 布局

- flex 布局虽然强大，但是只能一维布局，如果需要二维布局的话，那么我们还需要使用 gird.
- gird 布局牛逼在哪里？gird 布局是使用**CSS 而不是使用 HTML 控制的**，还可以依赖@media 来根据不同的上下文来获得新的布局。
  也就是说，不需要在 HTML 中使用特定的标签布局，所有的布局都是在 CSS 中完成的，你可以随意定义你的 grid 网格
```

## CSS渲染形成图像过程 包括 render 和渲染和绘制过程

> 有了 DOM with position 的话，就有下面三个过程

- render 过程 将 dom 树 生成 Bitmap

- 渲染 img.fill()

- 绘制 viewpoint.draw()

## CSS基础机制

- CSS总体框架，详见Xmind--CSS脑图

- 数据爬取,详见CSS/cssCrawler.js