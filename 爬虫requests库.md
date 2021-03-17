# 爬虫requests库

[TOC]

## 01requests模块发送带headers的请求和带参数的请求

### 发送简单的请求

![image-20210226192713485](%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210226192713485.png)

判断请求是否成功

```Python
assert response.status_code == 200
//报错就会AssertionError
```

```python
response =request.get(url)

//常用方法

response.text
response.content

response.status_code

response.request.url
response.url

response.request.headers
response.headers——————————//响应头

response.content.decode()查看响应的内容
```

![image-20210227024735977](%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210227024735977.png)

> response.request.url
>
> response.url
>
> 响应和请求的url地址一样吗
>
> 往往不一样，重定向之后就会不一样

请求头——蓝色那个是程序

user-agent（requests模块默认的user-agent）并不是正规的浏览器，是一种程序，对方服务器看出来了是爬虫，那就返回的少

因此，要发送带header请求

#### 发送带header请求

**来模仿浏览器，欺骗服务器，获取和浏览器一致的内容**

header的形式：字典

```
headers={"User-Agent":"Mozilla/5.0(Windows NT10.0;Win64; x64)AppleWebkit/537.36(KHTML, like Gecko)Chrome/54.0.2840.99 Safari/537.36"}
```

用法： requests.get(url,headers=heaeders)

![image-20210227025502426](%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210227025502426.png)

> 源码里面的空白就是/n/t/n/t......
>
> 不代表没有内容

为什么headers传给headers呢？（到时讲）

#### 发送带参数的请求

![image-20210227025839938](%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210227025839938.png)

参数的形式：字典

```
kw={'wd':'长城'}
```

用法： requests.get(url,params=kw)

添加params参数，接受字典格式的内容

——>  就不用wd=.....那段了

那url不带那段，要不要加上？呢

```
p={'wd':'长城'}
```

用法： requests.get(url_temp,headers=heaeders,params=p)

> 为什么headers传给headers呢？
>
> 因为后续会在get里面放很多很多参数，headers是字典，params也是，request这个模块，p传给headers还是params，所以一定要给别人看 到底谁传给谁，很多时候不能，按照定义的顺序来，因为不一定先是headers，所以还是headers传给headers吧

<img src="%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210228021307807.png" alt="image-20210228021307807" style="zoom:50%;" />

在线解码工具：解码

有百分号——**url编码**的内容

> 拼接到了一起
>
> 如果没有问号![image-20210228021528565](%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210228021528565.png)
>
> 结果一样，不影响

**.fomat——调用这个方法，放入任何想放的东西**

![image-20210228021808698](%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210228021808698.png)

```python
"我{}喜欢你".format(1)
'我1喜欢你'

"我{}喜欢你".format(a)
'我a喜欢你'

"我{}喜欢你".format([1,2,3])
'我[1,2,3]喜欢你'

"我{}喜欢你".format({"a":2})
"我{'a':2}喜欢你"

"我{}喜{}欢{}你".format({"a":2},2,3)
"我{'a':2}喜2欢3你"
```

字符串格式化的另一种方式——format

![image-20210228022342408](%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210228022342408.png)

<img src="%E7%88%AC%E8%99%ABrequests%E5%BA%93.assets/image-20210228022603286.png" alt="image-20210228022603286" style="zoom:50%;" />

找规律

## 02贴吧爬虫



## 03requests模块发送posts请求



## 04requests模块使用代理



## 05requests模拟登陆的三种方式



## 06requests模块发送请求和获取网页的字符串



## 07requests保存图片





#### 6-1-5 Fiddle的使用



### 6-2 数据提取方法



### 6-3 动态网页数据的提取



### 6-4 scrapy

