# Robots协议

Robots协议（Robots Exclusion Protocol，网络爬虫排除标准）
 
## 什么是robots.txt？
 
一个搜索引擎抓取你的网站，做的第一件事就是看看你的网站根目录下有没有robots.txt这个文件，如果有则按照上面的规则抓取你的网站，没有的话则是默认可以抓取你的网站上面的所有内容。说白了就是一个文件，告诉搜索引擎网站的哪些内容不可以抓取。
 
 
## 作用
 
既然这个文件可以告诉搜索引擎哪里不可以抓取，那么就可以利用这点来优化网站。
 
1.屏蔽站内死链（404页面）、重复链接（内容重复的页面）、无关链接（跟主题无关的页面，比如广告页面等等）。
 
2.防止搜索引擎抓取重复内容。网站上存在不同url相同内容的话，容易被搜索引擎认为是作弊行为，从而被降权。应当把重复的url屏蔽掉。
 
3.可以把网站地图的链接放在这个文件里面，方便搜索蜘蛛抓取网页。
 
4.屏蔽网站上涉及隐私的内容。
 
5.做外链的时候有用。前几天在百度搜藏放了几个网址，今天看了那个网站的robots.txt，才知道前几天的辛苦白费了！
 
6.防止假的友情链接。有些网站把友情链接页面写入这个文件，然后骗取别人跟他交换友情链接。别人傻乎乎的，还以为占到便宜了。
 
 
## 基本语法
User-agent: *  ------------------*代表所有的搜索引擎
 
User-agent: Baiduspider -----百度搜索引擎
 
User-agent: Googlebot -------谷歌搜索引擎
 
User-agent: Sosospider -------搜搜搜索引擎
 
Allow:XXX---------------------允许访问以XXX开头的文件或目录
 
Disallow:XXX-----------------禁止搜索引擎访问以XXX开头文件或目录
 
*--------------------------------匹配任意长度的字符串（长度可为0）
 
$--------------------------------结束符
 
\#--------------------------------注释
 
Sitemap------------------------站点地图
 

## 案例分析
 
1.允许所有搜索引擎访问所有页面
 
User-agent: *
 
Allow:/
 
 
2.禁止百度抓取所有页面
 
User-agent: Baiduspider
 
Disallow: /
 
 
3.禁止谷歌抓取网站private_html文件夹里面除了about.html外的所有文件
 
User-agent: Googlebot
 
Allow:/private_html/about.html
 
Disallow: /private_html/
 
 
4.禁止所有搜索引擎抓取包含问号 (?) 的网址
 
User-agent: *
 
Disallow: /*?*
 
 
5.禁止搜索引擎抓取.asp结尾的网址
 
User-agent: *
 
Disallow: /*.asp$
 
 
6.只允许百度搜索引擎访问，其他搜索引擎全部禁止
 
User-agent: BaiduSpider
 
Allow: /
 
User-agent: *
 
Disallow: /
 
 
7.设置站点地图
 
Sitemap: http://www.chenjianhang.com/sitemap.xml
 
 
 
## 注意事项
 
* robots.txt必须放在网站根目录下，文件名必须全部小写。
* robots.txt文件内容为空时，效果与没有该文件一样，都是默认可以抓取网站所有页面。
* Disallow:后面接着的内容为空时，作用和Allow: /一样。
* 注意Disallow: /test和Disallow: /test/是有区别的，Disallow: /test禁止抓取/test、/testabc.html、/test/abc目录，而Disallow: /abc/是禁止抓取/test/abc目录，但却允许抓取/test和/testabc.html
* 如果上传了robots文件，但你对robots协议的语法不熟悉，不能确定该文件是否写错，请务必使用检测工具检测一下是否写错。如果写错，会造成你的网站无法正常被百度收录。我常用的工具是百度站长工具：http://zhanzhang.baidu.com/robots。使用方法：点击规则校验->输入网址->提取->输入要校验的网址或路径(这些路径就是希望被百度收录的不同位置的路径)->点击校验->如果结果都是允许抓取，说明robots.txt文件正确。当然百度站长等站长工具上都有自动生成robots.txt的工具，菜鸟可以去用，免得出错。
* robots协议是一个"君子协议"。网站上的隐私内容不要放在公开目录上，更不能写到robots.txt上，写在上面不是明摆着告诉别人你的网站的隐私数据放在哪里吗，遇到居心不良的人，后果不堪设想。
* 注意robots协议是大小写敏感的，url中的大小写是严格区别的。还有像Sitemap和Allow等不要写成小写了：sitemap、allow。
 
 
 