# Vue

兼容性：IE 9+

vue init webpack lcadmin-front-vue

### 使用 scss

cnpm install node-sass --save-dev
cnpm install sass-loader --save-dev

import './sass/main.scss'


解决Error: ENOENT: no such file or directory, scandir 'D:\IdeaWork\code-front-jet\node_modules\.npminstall\node-sass\3.7.0\node-sass\vendor'

解决方案是执行以下方法：

```
npm rebuild node-sass
```


## 使用 Vue 创建项目流程

```
vue init webpack project-name
```

创建 `.npmrc`：

```
disturl=https://npm.taobao.org/dist
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
phantomjs_cdnurl=https://npm.taobao.org/mirrors/phantomjs/
chromedriver_cdnurl=http://cdn.npm.taobao.org/dist/chromedriver
```

修改 `.eslintrc.js`：

```
'indent': 0,
// 'indent': [1, 4, {"SwitchCase": 1}]
```

`index.html` normalize：

```
<link rel="stylesheet" href="/static/css/normalize.css">
<link rel="stylesheet" href="/static/css/reset.css">
<link rel="stylesheet" href="/static/font/iconfont.css">
```

main.css


```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
```


## material design 框架调研

## 框架的选择



### 纯 JS

* Materialize
	* 基于 jQuery
	* [Github 29K](https://github.com/Dogfalo/materialize)
	* http://materializecss.com/
	* 风格：class="waves-effect waves-light btn
* mdui
	* [Github 1644](https://github.com/zdhxiong/mdui)
	* 风格：<button class="mdui-btn mdui-color-theme-accent mdui-ripple">button</button>
* MUI
	* JS框架
	* [Github 3K](https://github.com/muicss/mui)
	* 风格：mui-container
* Material
	* Material Design for Bootstrap 4 
* vuematerial
	* 基于 vue 
	* [Github 4K star]()
* Muse UI — 基于 Vue2.0 的 Material Design UI 库
	* [Github 4K star](https://github.com/museui/muse-ui) star 47
	* [官网]()
* Material UI
	* 基于 React


