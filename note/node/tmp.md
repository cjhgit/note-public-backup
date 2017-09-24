

## node.js
1. 安装
2. 命令提示符分别输入node -v以及npm -v如果返回版本号说明你安装成功了
./npm/npmrc:
registry = https://registry.npm.taobao.org

npm install less -g”，然后npm就自动开始下载并安装LESS。

lessc all.less > all.css

## 安装grunt

npm install -g grunt-cli

这时候要验证一下grunt-cli是否安装完成并生效，你只需要继续在命令行中输入“grunt”命令即可。如果生效，则会出现以下结果：
或者完成后测试grunt --version看是否正确显示grunt-cli版本

需要你在控制台进入到网站或系统的具体目录下。这里我们进入 D:\grunt_test 目录下。然后输入以下命令。

npm install grunt --save-dev

## 使用uglify插件（压缩javascript代码）

npm install grunt-contrib-uglify --save-dev

## 安装Bower
npm install bower -g


bower install angularjs --save
bower insall jquery --save

bower init
会提示你输入一些基本信息，根据提示按回车或者空格即可，然后会生成一个bower.json文件

方法一：假如你的git安装目录是”C:\Program Files (x86)\Git”，在path中( 系统属性中)加入git的bin和cmd目录，如C:\Program Files (x86)\Git\bin;C:\Program Files (x86)\Git\cmd


grunt-contrib-less
grunt-autoprefixer
clean:删除临时文件
grunt-contrib-jshint（js语法检查）、grunt-contrib-concat（js合并）、grunt-contrib-uglify（采用UglifyJS压缩js）、grunt-contrib-cssmin（Css压缩合并）、grunt-htmlhint（html语法验查），以上都是常用的插件。