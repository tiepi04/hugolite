---
title: MarkDown的基本使用
published: 2023-11-24T22:33:57+08:00
summary: "折磨人的MarkDown"
cover:
  image: "https://api.likepoems.com/img/pc"
tags: [语言,博客]
categories: '语言'
draft: false 
lang: ''
---
这个页面主要用来测试功能
## 1.粗体
这个字体更粗<b>粗体</b>
``` bash
<b>粗体</b>
```
## 2.变颜色
<p style="color: #FF0000;">红色</p>
``` bash
<p style="color: #FF0000;">红色</p>
```
下面是搜集的颜色列表:

<img src="./hexo-2/colour.png" alt="颜色表" style="zoom:67%;" />

> 懂了格式后其它颜色同理

## 斜体
<i>斜体</i>
``` bash
<i>斜体</i>
```

## 删除体
<del>删除体</del>
``` bash
<del>删除体</del>
```

## 插入字
<ins>插入字</ins>
``` bash
<ins>插入字</ins>
```

## 上标字
<sup>上标字</sup>123
``` bash
<sup>上标字</sup>123
```

## 下标字
123<sub>下标字</sub>
``` bash
123<sub>下标字</sub>
```

## 强调字体
`redis` 是非常重要的。
``` bash
`redis` 是非常重要的。
```

## 标签

### 数字标签
1. 这是一个标签

2. 这是第二个标签
    数字 + . + 空格
    上面的标签用法是：
``` bash
1. 这是一个标签

2. 这是第二个标签
    数字 + . + 空格
```

### 符号标签
<li style="margin-left: 40px;font-size: 15px">123</li>
上面的使用这个实现的
``` bash
<li style="margin-left: 40px;font-size: 15px">123</li>
```
我们的 li 标签要放在一行中，不然，每一个 li 标签，会被添加
``` bash
<li style="margin-left: 40px;font-size: 15px">123</li><li style="margin-left: 40px;font-size: 15px">123</li><li style="margin-left: 40px;font-size: 15px">123</li>
```
如果不放在一行会出现

<li style="margin-left: 40px;font-size: 15px">123</li>
<li style="margin-left: 40px;font-size: 15px">123</li>
<li style="margin-left: 40px;font-size: 15px">123</li>

很难看

## 好看的排列

当我们只用 # 这个标签的时候，最好添加

``` bash
<br/>

# ***

<br/>
```
就会像这样
<br/>

# ***

<br/>

这样整体排列很好看。

## 图形标签
一个非常偶然的机会发现官方的图形标签。

- 1
    - 1
        - 1
            - 1
- 2
- 3

其上面的表示方式如下：
``` bash
1
    - 1
        - 1
            - 1
- 2
- 3
```

## 表格
|表格|属性|样式|
|---|---|---|
|一|二|三|
其代码如下：
``` bash
|表格|属性|样式|
|---|---|---|
|一|二|三|
```

假设有一个单元格的内容太多了，想要换行，可以
|表格|属性|样式|
|---|---|---|
|一|二|我们过了江，进了车站。我买票，他忙着照看行李。行李太多，得向脚夫11行些小费才可过去。<br/>他便又忙着和他们讲价钱。我那时真是聪明过分，总觉他说话不大漂亮，非自己插嘴不可，但他终于讲定了价钱；|
``` bash
|表格|属性|样式|
|---|---|---|
|一|二|我们过了江，进了车站。我买票，他忙着照看行李。行李太多，得向脚夫11行些小费才可过去。<br/>他便又忙着和他们讲价钱。我那时真是聪明过分，总觉他说话不大漂亮，非自己插嘴不可，但他终于讲定了价钱；|
```

但是如果想要合并单元格，就需要借助 html 元件了。
<table>
    <tr>
    	<td>最初价格</td>
        <td>买卖价格</td>
        <td>合约方向</td>
        <td>交割价格</td>
        <td>计算公式</td>
        <td>盈亏情况</td>
    </tr>
    <tr>
    	<td rowspan="4">1000U</td>
        <td rowspan="2">800U</td>
        <td rowspan="2">看空</td>
        <td>1200U</td>
        <td rowspan="2">合约张数 * 合约乘数 * （1/平仓价格 - 1/开仓价格）</td>
        <td>1 * 1 * (1/1200 - 1/800) =<br/> -(1/2400)BTC</td>
    </tr>
    <tr>
        <td>700U</td>
        <td>1 * 1 * (1/700 - 1/800) =<br/> 1/5600 BTC</td>
    </tr>
    <tr>
        <td rowspan="2">1200U</td>
        <td rowspan="2">看涨</td>
        <td>1400U</td>
        <td rowspan="2">合约张数 * 合约乘数 * （1/开仓价格 - 1/平仓价格）</td>
        <td>1 * 1 * (1/1200 - 1/1400) =<br/> 1/9800 BTC</td>
    </tr>
    <tr>
        <td>800U</td>
        <td>1 * 1 * (1/1400 - 1/1200) =<br/> -1/6400 BTC</td>
    </tr>
</table>

代码如下
``` bash
<table>
    <tr>
    	<td>最初价格</td>
        <td>买卖价格</td>
        <td>合约方向</td>
        <td>交割价格</td>
        <td>计算公式</td>
        <td>盈亏情况</td>
    </tr>
    <tr>
    	<td rowspan="4">1000U</td>
        <td rowspan="2">800U</td>
        <td rowspan="2">看空</td>
        <td>1200U</td>
        <td rowspan="2">合约张数 * 合约乘数 * （1/平仓价格 - 1/开仓价格）</td>
        <td>1 * 1 * (1/1200 - 1/800) =<br/> -(1/2400)BTC</td>
    </tr>
    <tr>
        <td>700U</td>
        <td>1 * 1 * (1/700 - 1/800) =<br/> 1/5600 BTC</td>
    </tr>
    <tr>
        <td rowspan="2">1200U</td>
        <td rowspan="2">看涨</td>
        <td>1400U</td>
        <td rowspan="2">合约张数 * 合约乘数 * （1/开仓价格 - 1/平仓价格）</td>
        <td>1 * 1 * (1/1200 - 1/1400) =<br/> 1/9800 BTC</td>
    </tr>
    <tr>
        <td>800U</td>
        <td>1 * 1 * (1/1400 - 1/1200) =<br/> -1/6400 BTC</td>
    </tr>
</table>
```

## 修改图片大小
``` bash
<div style="width: 50%;padding-left: 25%">

![](/images/software/5_0.jpg)

</div>
```
另外剧中的话使用 text-align:center; 不管用，需要使用上面的代码。

中间要有隔行，不然可能会出问题。

<div style="position: relative; width: 100%; height: 0; padding-bottom: 75%;"><iframe 
src="//player.bilibili.com/player.html?aid=39807850&cid=69927212&page=1" scrolling="no" border="0" 
frameborder="no" framespacing="0" allowfullscreen="true" style="position: absolute; width: 100%; 
height: 100%; left: 0; top: 0;"> </iframe></div>

## 图片并排插入
很简单，其实是表格+插入图片的语法，相比固定图片尺寸的写法，这个写起来比较方便。
``` bash
| ![xxx](\images\xxx.jpg) | ![xxx](\images\xxx.jpg) | ![xxx](\images\xxx.jpg) |
| --- | ---| --- |
```

## 添加多分类
categories 后面这样写就行了

分级分类
前一个的等级高
类别1>类别2>类别3
``` bash
categories: [类别1,类别2,类别3]
```

同级分类(可以包含分级分类)
``` bash
categories:
    - [Diary, PlayStation]
    - [Diary, Games]
    - [Life]
```
此时这篇文章同时包括三个分类： 
PlayStation 和 Games 分别都是父分类 Diary 的子分类
同时 Life 是一个没有子分类的分类。
<i>但在我的使用中它们混在一起了</i>

## 添加多个标签
标签没有分级
tags 后面直接这样写就行了
``` bash
tags: [标签1,标签2,标签3]
```

# 文章

## 引用文章

正常使用链接文章在[]()写/年/月/日/文章名
也就是写生成后的静态页面的地址。
这要是改以下年月日不就GG了。

所以可以使用相对链接来解决问题

``` bash
{% post_link 文章文件名（不要后缀） 文章标题（可选） %}
```

如：

``` bash
{% post_link Hello-World %}
{% post_link Hello-World 你好世界 %}
```

不理解的话实际操作一下就明白了。

## 博客内下载文件

用来本地下载
不在同一目录把文件的路径加到前面
```
<a href="" download="文件名">点击下载</a>
```

## 封面
添加两个东西即可
例如
``` bash
---
title: Hexo的建设及踩坑
top_img: http://up.36992.com/pic/e6/c5/51/e6c551e768092c8655292d89a4034a74.jpg
cover: http://up.36992.com/pic/e6/c5/51/e6c551e768092c8655292d89a4034a74.jpg
---
```

`top_img`是文章内顶部照片
`cover`是文章外文章预览照片
