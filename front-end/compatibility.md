浏览器兼容性：

对待兼容性（以 IE 8 为例）：

* 统计你的网站有多少用户在用 IE 8（不是整个浏览器市场）
* IE 8 上的体验没必要做到跟 Chrome 一样。

如何可能的话，统计一下这些用户对公司有没有贡献（钱），没有贡献直接让他们升级。3. 当 IE 8 用户低于5%，直接提示不支持。













## 其他
 
如何查看各浏览器的市场份额：
 
【[百度统计官方网站](http://tongji.baidu.com/)】->【流量研究院】->【浏览器市场份额】

2017-09-29：

* Chrome：43.37%
* IE 8：9.62%
* IE 9：9.44%
* ...
 
也有其他方式，自行百度。

## IE 8 兼容性

透明背景：

```
filter:progid:DXImageTransform.Microsoft.gradient(startColorstr=#7f000000,endColorstr=#7f000000); // IE 8
```

HTML5 标签：

```
<!--[if lt IE 9]>
    <script src="http://apps.bdimg.com/libs/html5shiv/3.7/html5shiv.min.js"></script>
<![endif]-->
```

百度网盘下载：https://pan.baidu.com/s/1miDqbTQ

video：

```
<script src="http://html5media.googlecode.com/svn/trunk/src/html5media.min.js"></script>
```

低版本浏览器上采用 flowplay。



Chrome 上用原生 API，IE 8 上用 PolyfillChrome

## TODO

* video标签支持的视频格式
* audio
* ckplayer
* video.js

测试视频下载
http://www.runoob.com/try/try.php?filename=tryhtml_video_html5_4