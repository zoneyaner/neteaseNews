## neteasenews
>毕业设计课题:网页文本自动化采集系统

>日期: 2017.11.03-2018.05.25

>目标网站:  **http://news.163.com/**
---
> 基于**Requests**, **BeautifulSoup**,**selenium**库内的**webdriver**(chrome)以及**MongoDB**数据库技术的部署爬虫项目
1. **Requests**
    >向网站发送一般请求
2. **BeautifulSoup**
    >对网站返回的文本或者二进制内容进行解析,并利用方法有条件采集
3. **selenium**
    >对于JS渲染或者动态加载的网页获取源代码,应用与特殊的请求环境
4. **chrome**
    >版本信息:Version 65.0.3325.181 (Official Build) (64-bit),可采用无界面模式,具体可见于**config.py**文件
5. **MongoDB**
    >与python爬虫相得益彰的数据库.需要引用python的**pymongo**库
---
### 摘要:
>>该爬虫运行在网易新闻上,主要是针对首页,排行,图片,国内,国际,社会,数读,军事,航空,无人机,新闻学院,政务,公益,媒体等标签页进行逐步爬取,因为新闻的时效性,需要时刻更新,所以在此基础上进行流程部署,并将最终爬取内容存入数据库中,这里采用的数据库是**Mongodb**.
---
### 文件说明:
1. **news.py**
    > 爬虫流程部署,定义唯一__main__方法
2. **config.py**
    > 爬虫配置文件,关于数据库以及其他常用字段设置
3. **datablogSpider.py**
    > 爬取标签:**数读**
4. **mainSpider**
    > 爬取**国内**,**国际**,**社会**,**军事**,**航空**,**无人机**标签,定义一些通用方法以及存储数据库的方法
5. **moreSpider**
    > 爬取**新闻学院**,**政务**,**公益**,**媒体**标签信息,大多数采用以上定义的通用方法.
6. \__init__.py
    > 空文件,作用将该文件夹下的.py文件作为一个包.解决文件导入问题
---
## 进度表:
---
爬虫技术,架构布设,以及数据库表的设计,尝试爬取一些大量文本的网站csdn,搜狗新闻,微信等等

Time: 2018.03.05-

---
确定爬取网站:**http://news.163.com/**

Time:   2018.03.30
---
分析相同布局以及内容跳转相似的国内,国际,社会三个标签页,并编写第一个爬虫**mainSpider.py**

Time:   2018.03.30    

---
mainSpider增加details()方法,savedata()方法,并对请求方法进行了异常处理和添加处理js动态加载的能力,主要用到webdriver自动加载下拉脚本,获取完整内容

Time:   2018.04.01

---
修复了一些BUG,针对爬取过程出现异常情况进行处理(采用try-except捕捉),并且留意到数据库数据有重复的迹象

Time:   2018.04.02

---
分析军事,航空,无人机标签页与之前三个的相同之处和不同之处,主要体现在文章跳转的内容上,有纯文字,有图文,或者只有(图片+图片信息),因此对details()方法进行改进,对不同页面进行检测,最后处理.

Time:   2018.04.02      04:05:23

---
爬取数读标签,发现其下的所有url跳转内容有两种不同页面,一为之前标签的网易正文架构,二是数读平台,关键信息在不同的html标签里,所另开一个datablog.py文件专门爬取该标签

Time:   2018.04.03

---
修复了一些bug, 对提取信息的内容以什么方式存进数据库进行改进
Time:   2018.04.04

---
爬取排行榜标签

Time:    2018.04.05

---
尝试在mainSpider里多开几个进程,提高爬取效率成功,理解单参数pool.map()方法的迭代,和多参数itertools.startmap()方法的迭代,并且修改文件夹结构,更加符合框架.并且将之前的代码push to Github上.

Time:    2018.04.05     00:57:40

---
修复了各文件下库导入多余,并且在文件夹下添加\__init.py__文件,解决包导入路径bug

Time:    2018.04.06     02:55:15

---
爬取首页信息,无差别式的爬取,只针对新闻链接的正则匹配

Time:    2018.04.06     05:25:53

---
修改表的键的意思,改正一些名称,使其更加易懂

Time:   2018.04.06      08:45:20

---
爬取新闻学院,政务,公益,媒体,大致爬取过程较为之前简单,纯粹为正则表达式提取url,处理文本,存储数据库三步.

Time:   2018.04.07

---
各爬虫运行正常.

修复bug:正则表达式对原始字符串r和转移符之间导致的warning

Time:   2018.04.08      19:68:11

---