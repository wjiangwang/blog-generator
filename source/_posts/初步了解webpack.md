---
title: 初步了解webpack
date: 2018-08-19 20:58:23
tags: webpack
---
### webpack基本安装 
首先我们创建一个目录，初始化 npm，然后 在本地安装 webpack，接着安装 webpack-cli（此工具用于在命令行中运行 webpack）
```bash
mkdir webpack-demo && cd webpack-demo
npm init -y
npm install webpack webpack-cli --save-dev
```
建立如下目录
```
  webpack-demo
  |- package.json
+ |- index.html
+ |- /src
+   |- index.js
```
#### 配置文件
```js
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist')//将src/index.js 作为入口起点，生成 dist/main.js 作为输出。
  }
};
```
#### 执行
```
npx webpack --config webpack.config.js
```
会将我们的脚本 src/index.js 作为 入口起点，也会生成 dist/main.js 作为 输出。

### babel-loader
#### 安装
```
npm install --save-dev babel-loader babel-core
```
#### 配置
在 `webpack` 里的 `webpack.config.js` 文件 同添加
```js
module: {
  rules: [
    { test: /\.js$/, exclude: /node_modules/, loader: "babel-loader" }
  ]
}
```
#### 创建 .babelrc 配置文件
虽然已经配置好了 Babel ，但并没有让它真正生效。在项目的根目录中创建一个 .babelrc 文件并启用一些插件。
首先，可以使用转换 ES2015+ 的 env preset 
```
npm install babel-preset-env --save-dev
```
为了让 preset 生效，你需要像下面这样定义你的 .babelrc 文件：
```js
{
  "presets": ["env"]
}
```
### sass-loader
#### 安装
```
npm install sass-loader node-sass webpack --save-dev
```
node-sass 和 webpack 是 sass-loader 的 peerDependency，因此能够精确控制它们的版本。
#### 配置
```js
  module: {
    rules: [{
      test: /\.scss$/,
      use: [{
          loader: "style-loader" //将 JS 字符串生成为 style 节点
      }, {
          loader: "css-loader" // 将 CSS 转化成 CommonJS 模块
      }, {
          loader: "sass-loader" //将 Sass 编译成 CSS
      }]
    }]
  }
```
### 使用
此时目录应该如下
```
  webpack-demo
  |- /node_modules
  |- package.json
  |- index.html
  |- /dist
    |- bundle.js
  |- /src
    |- index.js
    |- main.scss
    |- moudle-1.js
```
使用 `import` 在 `index.js` 中导入 `main.scss`  `moudle-1.js`
```js
import x from './moudle-1'
import y from './main.scss'
console.log(3)
x()
```
再次运行
```
npx webpack --config webpack.config.js
```
### 参考
[文章中的wenpack-demo](https://github.com/wjiangwang/webpack-demo)
[webpack中文网站](https://webpack.docschina.org/guides/getting-started/)
[babel中文网站](https://www.babeljs.cn/docs/setup#installation)