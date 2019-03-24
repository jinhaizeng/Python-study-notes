# 1.爬虫基本框架
![爬虫简单框架](https://github.com/jinhaizeng/Python-study-notes/blob/master/%E5%9B%BE%E5%BA%8A/%E7%AE%80%E5%8D%95%E7%88%AC%E8%99%AB%E6%9E%B6%E6%9E%84.PNG?raw=true)
![爬虫简答框架——运行流程](https://raw.githubusercontent.com/jinhaizeng/Python-study-notes/master/%E5%9B%BE%E5%BA%8A/%E7%AE%80%E5%8D%95%E7%88%AC%E8%99%AB%E6%9E%B6%E6%9E%84-%E8%BF%90%E8%A1%8C%E6%B5%81%E7%A8%8B.PNG)
# 2.URL管理器
* URL管理器：管理待抓取URL集合和已抓取URL集合
    * 目的：防止重复抓取、防止循环抓取
    * 需要实现的功能：
        * 添加新URL到待爬取集合中
        * 判断待添加URL是否在容器中
        * 判断待爬取URL
        * 判断是否还有待爬取URL
        * 将URL从待爬取移动到已爬取
    * ![实现方式](https://github.com/jinhaizeng/Python-study-notes/blob/master/%E5%9B%BE%E5%BA%8A/URL%E5%AE%9E%E7%8E%B0%E6%96%B9%E5%BC%8F.PNG?raw=true)