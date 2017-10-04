


* 今日头条新闻文章采集爬虫
      选择爬取今日头条文章的方式   要爬取的频道名称   要爬取的文章关键字
      
中国旅游景点大全数据[含经纬度] 
http://www.shenjianshou.cn/index.php?r=market/product&product_id=500125


反爬虫

scrapy startproject doubanbook





遇到的问题：403

解决：添加用户代理

问题：Filtered offsite request to 'movie.douban.com'

解决：

官方对这个的解释，是你要request的地址和allow_domain里面的冲突，从而被过滤掉。可以停用过滤功能。

yield Request(url, callback=self.parse_item, dont_filter=True)