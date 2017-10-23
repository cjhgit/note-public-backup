
## 支付

支付宝
微信支付
PayPal
银行卡
visa
第三方支持
第三方支持整合平台

从地域上来说，银联是中国的卡组织，VISA和万事达都是美国的卡组织。目前国内的银行卡按照打头数字的不同分别归属不同银行卡组织，以“4”字打头的银行卡属于VISA卡组织，以“5”字打头的属于万事达，以“62”、“60”、“9”打头的属于中国银联，而“62”、“60”打头的银联卡是符合国际标准的银联标准卡，可以在国外使用，这也是中国银联近年来的主打卡片。　　
　　
      从用途上看，如果只在国内消费，银联就是最好的选择，但如果经常需要到国外消费，一张VISA或万事达就必不可少了。近年来，为了迎合用户的需求，各大银行都推出了双币卡，也就是银联+VISA或银联+万事达，这样用户在国内消费就可以走银联渠道，到了国外就可以走VISA或万事达渠道。
 
　　那么VISA和万事达之间该如何选择呢？
 
　　其实，各个发卡组织的信用卡有各自的优势。VISA和万事达都是历史比较久的发卡组织，在全球都有较大的影响力。其中，VISA在美国、亚洲国家较为通行，而万事达在欧洲的影响力则更大一些。因而，去欧洲的话，带着万事达标识的信用卡可能更为方便，而在美国则可使用VISA信用卡。小伙伴们可以根据自己常去的境外国家进行选择。



http://lbsyun.baidu.com/index.php?title=uri/api/android
http://lbs.amap.com/api/javascript-api/guide/function/callapp

aFarkas/lazysizes

标注
http://www.mamicode.com/info-detail-1992580.html

首页交互
https://www.tencent.com/zh-cn/index.html

## 阿里云 RDC



canalifecare.com

### RDC 环境配置

下载路径：/root/deploy/jianan-front/package.tgz
解压目录：/usr/local/nginx-app/

Stop：echo "stop"

start：/root/deploy/jianan-front/deploy.sh
执行用户：root

注意要在机器上新建    target目录？


Access-Control-Allow-Credentials  true


## 前端项目构建步骤.txt

运行命令
npm  install
npm  run  build
输出物路径
target/

目标机器
120.24.226.112
部署路径
/root/deploy/coolkeke-front
部署命令
/root/deploy/coolkeke-front/deploy.sh---------------------对应E://coolkeke项目中deploy.sh-front

==========================================nginx配置===================================/etc/nginx/
https://router.vuejs.org/zh-cn/essentials/history-mode.html----location  /  {
    try_files  $uri  $uri/  /index.html;
}


项目流水线：

开始->构建->日常->预发->正式

流转到下一阶段配置：都不选

流水线名称：zktw-front
监听设置：自动触发
master 分支

构建：

任务名称：构建
代码库地址：superxiao1992/zktw-front.git
分支名称：master

日常：

任务名称：日常部署
包标签：default
应用：zktw-front
环境：日常环境

预发：

任务名称：预发部署
包标签：default
应用：zktw-front
环境：预发环境

正式：

任务名称：正式部署
包标签：default
应用：zktw-front
环境：正式环境


设计图有色差