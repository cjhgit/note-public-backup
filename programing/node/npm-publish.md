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

问题： `npm publish` 提示：You do not have permission to publish "xxx". Are you logged in as the correct user? : xxx

解决：可能是模块名称已经被占用。

问题： `npm publish` 提示：you must verify your email before publishing a new package: https://www.npmjs.com/email-edit : xxx

解决：邮箱验证。








