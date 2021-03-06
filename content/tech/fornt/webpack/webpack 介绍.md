## webpack 介绍

对于 [webpack](https://webpack.js.org/) 相信大家即使没有用过也多少听过他的大名。

前端这些年发展速度迅速上升，应用范围也越发广泛。项目管理越来越复杂。于是出现了一些常见的模块化解决方案。

## 模块化历程

### CommonJS

最早出现的模块化方案，可在 node 环境中运行。最近看到的地方是 webpack 的配置文件

### AMD

和 `commonjs` 相比最大的优势是可以在浏览器直接运行。支持异步。缺点不能直接使用还需要导入 AMD 的库才能使用

### ES6 模块化

是目前最通用的解决方案，模块化方面没有明显短板。

### TypeScript

2020 vue 3.0 会正式发布，将会全面采用 typescript ，模块化目前的最终方案，优点静态类型检查，定义类的时候时候定义 privete 方法，更强的语义化代码。

### SCSS

css 模块化方案。可定义变量，函数，拆分模块等

> 上面说到的模块化解决方案，除了 AMD 都需要用到 webpack 进行打包。除了打包，还可以进行代码压缩，图片压缩。CDN 加速等。使网站的性能提高很多。
