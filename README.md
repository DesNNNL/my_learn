# my_learn

学习python上走过的路
其实回头看看还好，不算太难，毕竟还没学到深层次的东西





关于里面的.py文件





#爬虫类：

    
txtdownload：是下载https://www.ybdu.com/ 网址中的小说的脚本,面向过程，单线（进）程，需要手动输入目标书籍的目录网址
    
newtxtdownload：同上，两者不同的是对requests请求返回的数据的处理方式不同，两者差距不大
    
bs4_txt：同上，但是这个脚本是用BeautifulSoup方法处理的数据内容，简单。最开始的想法是做成一个面向对象的脚本的，可发现这种小型脚本做成面向对象的话，工作效率反而会下降很多（反正我对代码的重复调用的需要又不高）。然后就做成了现在这样的半对象半过程的样子。
                   
题外插一句：BeautifulSoup是真的好用，xpath是真的很蠢（遇到br/就傻逼了）
 
    
movie：是对http://www.msj1.com/ 整站数据的爬取，但是我比较懒，只爬到了每一部剧的网址，其实根据上面爬取小说的方法，完全可以做到将网站内部所有的剧的海报和每一集的下载地址都爬下来。感兴趣的话可以试一下。
 
    
    
meizitu：其实是中了那些网站教学的毒，他们要用美女妹子的照片来吸引学生，我于是也跟着去爬取了网站的一些图片，我只是把首页上所有页码中的图片集里所有图片爬下来，要爬取整站的话，应该从首页的分类里面爬，就像我爬取movie里的信息一样。这个文件的目标网址是http://www.mzitu.com/ ，注意headers里面的Referer的网址就是主页，不然爬取的图片会是一张劝你不要盗取链接的图片
    
	
jingmiblog：是静觅爬虫的教程（基于2.7版本的），把他们写成html下载下来，我本来想把html整合成pdf的，结果电脑安装pdfkit库的时候报错，我也不想去弄了，于是就这样吧
    
    
maoyantop：就是静觅爬虫教程（基于3.x版本的），我拿来试了一下手，还好。  
    
    
sina：新浪的电脑端特别难爬取，我试了一下，爬了一点然后放弃。这个文件是爬取的新浪手机端的内容，具体是将一个博主的最新的粉丝爬取下来，大概有4700个左右，但是我做了筛选，只打印出妹子的基本信息（哈哈哈），所以只能看到一点。这个文件我已经确定了爬取的博主是 super也好君 （ https://m.weibo.cn/api/container/getIndex?containerid=231051_-_fans_-_3053244325&featurecode=10000326&type=uid&value=3053244325&since_id= ) , 其他人的链接只有自己找咯（建议去找什么美妆博主，妹子说不定很多哟）。
   
   
    

#以上的内容合理观看顺序应该是 maoyantop、txtdownload、newtxtdownload、meizitu、movie、jingmiblog、bs4_txt、sina
   
    


至于tencent和test_spider是基于scrapy框架搭建的脚本，tencent是下载的tencent的社会招聘的信息，test_spider是上面所提到的txt下载器，在说一次，xpath方法真的难用，而且注意yield和return有的地方可以替换，有的地方不能替换。最重要的是不要在pipilines里面对一个文件做一些文件读写的事，他们是异步，也就是说你读写的顺序是随机的（我下载小说的章节就是不规律的，难受）
