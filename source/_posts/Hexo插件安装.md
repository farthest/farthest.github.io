title: Hexo插件安装
author: Winter
abbrlink: 33600
date: 2018-02-10 13:29:24
tags:
---
# Hexo插件安装及使用

## HEXO-addlink

>hexo-addlink是在hexo post页面中添加当前帖子链接的有用工具。

安装
npm install hexo-addlink --save  
用法首先_config.yml从您的hexo项目中添加配置。

addlink：
   before_text：hello ＃文字之前的帖子链接
  after_text：bye ＃文字帖子后的链接

运行hexo命令。

hexo clean && hexo g

## hexo-auto-excerpt

>HEXO-自动摘录
Hexo通过添加标签来支持摘录。您可以使用hexo-auto-excerpt插件自动执行此操作。

安装  
npm install --save hexo-auto-excerpt

## hexo-baidu-url-submit

您得注册百度站长工具，然后在工具->网页抓取->链接提交里找到你的密匙。

首先，在Hexo根目录下，安装本插件：
npm install hexo-baidu-url-submit --save

然后，同样在根目录下，把以下内容配置到_config.yml文件中:
```
baidu_url_submit:
  count: 1 ## 提交最新的一个链接
  host: www.hui-wang.info ## 在百度站长平台中注册的域名
  token: your_token ## 请注意这是您的秘钥， 所以请不要把博客源代码发布在公众仓库里!
  path: baidu_urls.txt ## 文本文档的地址， 新链接会保存在此文本文档里
```
其次，记得查看_config.ym文件中url的值， 必须包含是百度站长平台注册的域名（一般有www）， 比如:

```
# URL
url: http://www.hui-wang.info
root: /
permalink: :year/:month/:day/:title/
```
最后，加入新的
deployer:
```
deploy:
- type: s3 ## 这是我原来的deployer
  bucket: hui-wang.info
- type: baidu_url_submitter ## 这是新加的
```
执行hexo deploy的时候，新的连接就会被推送了。

实现原理
推送功能的实现，分为两部分：

新链接的产生， hexo generate 会产生一个文本文件，里面包含最新的链接  
新链接的提交， hexo deploy 会从上述文件中读取链接，提交至百度搜索引擎

# hexo-baidu-url-push
 >一个hexo插件，使用百度JS链路自动推送方法，提交链接到百度

npm install hexo-baidu-url-push --save
