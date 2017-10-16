# Node.js 学习笔记 - NPM 发布模块

![](https://www.npmjs.com/static/images/wombat.box.svg)

## 前言

本文主要介绍如何发布一个 NPM 模块给其他人使用。

## 步骤

第零步，注册 NPM 账号。

在 NPM 官网 [https://www.npmjs.com](https://www.npmjs.com ) 注册一个账号。注意必须邮箱验证，否则无法发布模块。

第一步，想好一个模块名称。

名字尽量简单好记，并且不能和已有的模块重名。

我们可以在官网首页的搜索框里输入模块名称，看看名称是不是已经被占用了。

第二步，创建项目。

我们可以使用 `npm init` 来初始化项目。填写好相关的信息后，编写代码。

`index.js`：

```
exports.sayHello = function () { 
	return 'Hello world!'
}
```

第三步，添加用户。输入注册时填写的用户名和密码，以及邮箱（邮箱会公开）

```
$ npm adduser
Username: 用户名
Password: 密码
Email: (this IS public) 邮箱
Logged in as xxx on https://registry.npmjs.org/
```

第四步，上传包。

```
$ npm publish
```

## 补充

> 如果还没使用过 .npmignore，会默认使用 .gitignore 文件，加上一些更健全的默认选项。

> 很多人不明白都是，一旦在项目中添加了 .npmignore 文件，.gitignore 的规则就会被忽略（好讽刺，出乎意料啊）。结果就是，发布项目时，不得不审查两个文件是否同步，防止敏感信息的泄露。


取消发布

npm unpublish --force

> 说点题外话，主要是处于安全性考虑，在Azer NPM 撤包事件后，npm公布了一版新的规则，如下：

> * 版本更新少于24小时的包允许下架；
* 超过24小时的包的下架需要联系npm维护者；
* 如果有npm维护者参与，npm将检查是否有其他包依赖该包，如果有则不允下架；
* 如果某个包的所有版本都被移除，npm会上传一个空的占位包，以防后来的使用者不小心引用怀有恶意的替代者。


问题： `npm publish` 提示：You do not have permission to publish "xxx". Are you logged in as the correct user? : xxx

解决：可能是模块名称已经被占用。

问题： `npm publish` 提示：you must verify your email before publishing a new package: https://www.npmjs.com/email-edit : xxx

解决：邮箱验证。

问题：You cannot publish over the previously published version 1.0.0. : yunser

原因：版本号不能跟上一次发布的版本号相同。

问题：No name provided

原因：`package.json` 缺少 `name` 属性。



问题：

```
npm ERR! publish Failed PUT 400
npm ERR! Windows_NT 10.0.15063
npm ERR! argv "C:\\Program Files\\nodejs\\node.exe" "C:\\Program Files\\nodejs\\node_modules\\npm\\bin\\npm-cli.js" "publish"
npm ERR! node v6.11.0
npm ERR! npm  v3.10.10
npm ERR! code E400

npm ERR! Repository does not allow updating assets: npm-releases : repository
npm ERR!
npm ERR! If you need help, you may report this error at:
npm ERR!     <https://github.com/npm/npm/issues>

npm ERR! Please include the following file with any support request:
npm ERR!     C:\project\新建文件夹\node_modules\liangchuan-ui\npm-debug.log
PS C:\project\新建文件夹\node_modules\liangchuan-ui>
```

解决：




 auth required for publishing
npm ERR! need auth You need to authorize this machine using `npm adduser`



  "publishConfig": {
    "registry": "http://192.168.3.111:8081/repository/npm-releases/"
  }