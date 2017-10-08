# Webpack

webpack 2

要求读者需要了解 node 相关的知识，以及安装了 Node.js。

## 开始

### 1. 初始化

打开 cmd，切换到项目根目录：

```cmd
npm init -y
```

### 2.安装 webpack

将 webpack 安装到当前目录：

```
npm install --save-dev webpack
```

### 3.项目结构

项目结构如下：

```workplace
app/
    components.js
    index.js
build/
node_modules
package.json
webpack.config.json
```

//webpack 非全局安装的情况
node_modules/.bin/webpack app/main.js build/bundle.js

//webpack 全局安装的情况
webpack app/main.js build/bundle.js

```text
Uncaught ReferenceError: undefinedFunction is not defined
    at module.exports (bundle.js:82)
    at Object.<anonymous> (bundle.js:72)
    at __webpack_require__ (bundle.js:20)
    at bundle.js:63
    at bundle.js:66
```

```text
Uncaught ReferenceError: undefinedFunction is not defined
    at module.exports (hello.js?6d8d:5)
    at eval (main.js?6a4b:3)
    at Object.<anonymous> (bundle.js:70)
    at __webpack_require__ (bundle.js:20)
    at bundle.js:63
    at bundle.js:66
```
http://blog.csdn.net/xiaocainiaoshangxiao/article/details/46882921


npm install --save-dev style-loader css-loader

## webpackage 热更新

## CSS

```cmd
npm install css-loader,style-loader --save-dev
```

require('./common.css');

### SASS

//在项目下，运行下列命令行
npm install --save-dev sass-loader
//因为sass-loader依赖于node-sass，所以还要安装node-sass
npm install --save-dev node-sass

## js 压缩

## Babel

安装 babel：

```text
npm install --save-dev babel-core babel-preset-es2015  
npm install --save-dev babel-loader  
```

```javascript
let a = 111;  
let b = 222;  
var xxx = (c,d) => c*d;  
console.log(xxx(a,b));  
```

webpack.config.js:
```javascript
module.exports = {  
    //...
    module: {  
        loaders: [{  
            test: /\.js$/,  
            exclude: /node_modules/,  
            loader: 'babel-loader'  
        }]  
    }  
}  
```

然后再创建一个用于babel调用的文件，名为.babelrc
里面写入:
```json
{
    "presets": [
        "es2015"
    ]
}
```

然后在当前目录打开cmd，
运行命令 webpack
如果出现绿色的，证明成功了

```javascript
var a = 111;  
var b = 222;  
var xxx = function xxx(c, d) {  
  return c * d;  
};  
console.log(xxx(a, b));  
```

证明转码成功~~~~


## TODO

* Webpack3