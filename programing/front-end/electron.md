# electron

electron

https://electron.atom.io/

# Clone the Quick Start repository
$ git clone https://github.com/electron/electron-quick-start

# Go into the repository
$ cd electron-quick-start

# Install the dependencies and run
$ npm install && npm start

npm install --save-dev electron-packager

"scripts": {
  "start": "electron .",
  "packager": "electron-packager ./app HelloWorld --all --out ./OutApp --version 1.4.0 --overwrite --icon=./app/img/icon/icon.ico"
  },

npm run packager

### electron-vue

# 安装 vue-cli 和 脚手架样板代码
npm install -g vue-cli
vue init simulatedgreg/electron-vue my-project

# 安装依赖并运行你的程序
cd my-project
yarn # 或者 npm install
yarn run dev # 或者 npm run dev

GitHub
https://github.com/SimulatedGREG/electron-vue
中文文档
https://simulatedgreg.gitbooks.io/electron-vue/content/cn/
