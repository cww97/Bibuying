﻿# Bibuying

we are [here](https://github.com/BibuyingTeam/Bibuying.git)

由于彭先生起了“十度”这个名字

我们顺势起了个“必不应”，大家都是假的搜索引擎

## 要求

第一次小组项目作业：
Lucene倒排检索，给定一个不少于10k条的文本数据集，实现创建索引和检索功能。
加分项：中文语料、检索界面web化， 或借助solr，elastic等工具。
Deadline：4月15日。

## 项目环境

python 3.6 (Anaconda, windows 64)
pycharm

## 数据来源

从网易云爬歌手的热门50首歌

分类分别为

- 华语男歌手
- 华语女歌手
- 华语组合/乐队

每个分类里有100个热门歌手，每个歌手50首歌

`3 * 100 * 50 = 15000 首歌`

数据量应该符合要求的

定义`get_soup()`爬取html：
```python
def get_soup(web_url):
	print(web_url)
	req = urllib.request.Request(url=web_url, headers=headers)
	# print(req)
	web_page = urllib.request.urlopen(req)
	data = web_page.read()
	soup = BeautifulSoup(data, 'lxml')
	f.write(soup.prettify())
	return soup
```

### 爬取歌手id

以华语男歌手为例，url：`http://music.163.com/discover/artist/cat?id=1001`
内有标签`<a class="nm nm-icn f-thide s-fc0" href=" /artist?id=3681" title="李志的音乐">`

于是有了下面两行
```python
ids = soup.find_all('a', attrs={"class": "nm nm-icn f-thide s-fc0"})
pattern = re.compile(r'id=\d+')
```
找到所有标签然后用正则表达式得到id

结果存在`artist_id.txt`中，如下：

![artist_id](doc/pic/artist_id.png)

### 根据id获取歌单

先睡觉= =

// 待续

——by cww

## 数据索引

由于前面使用的py进行操作，这里方便起见统一使用了`elastic`的python接口`elasticsearch`.



// add here

——by xhy

## 检索界面

核心功能两个页面，搜索结果目录页和details页，有心情再搞个搜索主页

// add here

——by sjj

## 后记

感谢感谢感谢balabala

## 参考文献

[BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/index.zh.html)

[python爬取网易云歌词](https://www.cnblogs.com/Beyond-Ricky/p/6757954.html)

[ElasticSearch py](https://pypi.python.org/pypi/elasticsearch/2.2.0)

[django教程 | 菜鸟教程](http://www.runoob.com/django/django-tutorial.html)