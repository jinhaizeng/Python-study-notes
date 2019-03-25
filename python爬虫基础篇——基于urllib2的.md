# 1.爬虫基本框架
![爬虫简单框架](https://github.com/jinhaizeng/Python-study-notes/blob/master/%E5%9B%BE%E5%BA%8A/%E7%AE%80%E5%8D%95%E7%88%AC%E8%99%AB%E6%9E%B6%E6%9E%84.PNG?raw=true)
![爬虫简答框架——运行流程](https://raw.githubusercontent.com/jinhaizeng/Python-study-notes/master/%E5%9B%BE%E5%BA%8A/%E7%AE%80%E5%8D%95%E7%88%AC%E8%99%AB%E6%9E%B6%E6%9E%84-%E8%BF%90%E8%A1%8C%E6%B5%81%E7%A8%8B.PNG)
# 2.URL管理器
URL管理器：管理待抓取URL集合和已抓取URL集合
* 目的：防止重复抓取、防止循环抓取
* 需要实现的功能：
    * 添加新URL到待爬取集合中
    * 判断待添加URL是否在容器中
    * 判断待爬取URL
    * 判断是否还有待爬取URL
    * 将URL从待爬取移动到已爬取
* ![实现方式](https://github.com/jinhaizeng/Python-study-notes/blob/master/%E5%9B%BE%E5%BA%8A/URL%E5%AE%9E%E7%8E%B0%E6%96%B9%E5%BC%8F.PNG?raw=true)

# 3.网页下载器
## 3.1网页下载器简介
网页下载器：将互联网上URL对应的网页下载到本地的工具  
![网页下载器](https://github.com/jinhaizeng/Python-study-notes/blob/master/%E5%9B%BE%E5%BA%8A/%E7%BD%91%E9%A1%B5%E4%B8%8B%E8%BD%BD%E5%99%A8.PNG?raw=true)  
python有哪几种网页下载器
* urllib2——python官方基础模块
* requests——第三方包更强大
## 3.2urllib2下载网页的方法
1. 最简洁方法
示例代码
```python
import urllib2
# 直接请求
response = urllib2.urlopen('http://www.baidu.com')

# 获取状态码，如果是200表示获取成功
print response.getcode()

# 读取内容
cont = response.read()
```
2. 添加data、http header(这种方法还没有搞清楚)
![第二种方法](https://github.com/jinhaizeng/Python-study-notes/blob/master/%E5%9B%BE%E5%BA%8A/urllib2%E7%AC%AC%E4%BA%8C%E7%A7%8D%E4%B8%8B%E8%BD%BD%E7%BD%91%E9%A1%B5%E7%9A%84%E6%96%B9%E6%B3%95.PNG?raw=true)  
示例代码
```python
import urllib2
# 创建Request对象
request = urllib2.Request(url)

# 添加数据
request.add_data('a','1')
# 添加http的header
request.add_header('User-Agent','Mozilla/5.0')

# 发送请求获取结果
response = urllib2.urlopen(request)
```
3. 添加特殊情景的处理器
![添加特殊情景的处理器](https://github.com/jinhaizeng/Python-study-notes/blob/master/%E5%9B%BE%E5%BA%8A/urllib2%E7%AC%AC%E4%B8%89%E7%A7%8D%E4%B8%8B%E8%BD%BD%E7%BD%91%E9%A1%B5%E7%9A%84%E6%96%B9%E6%B3%95.PNG?raw=true)  
示例代码
```python
import urllib2,cookielib

# 创建cookie容器
cj = cookielib.CookieJar()

# 创建1个opener
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))

# 给urllib2安装opener
urllib2.install_opener(opener)

# 使用带有cookie的urllib2访问网页
response = urllib2.urlopen("http://www.baidu.com/")
```