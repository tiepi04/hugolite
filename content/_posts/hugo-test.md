---
title: Hugo Test
published: 2025-07-13T11:50:37+08:00
summary: "test"
cover:
  image: "https://rba.kanostar.top/landscape"
tags: [语言, 博客]
categories: '语言'
draft: false 
lang: ''
---
# 标题
# H1
## H2
### H3
#### H4
##### H5
###### H6


H1到H6正常

# 字

## 删除线
~~删除线~~
``` bash
~~删除线~~
```

## 插入字

hugo好像打不出插入字

## 粗体
1. **粗体1**
``` bash
**粗体1**
```
2. __粗体2__
``` bash
__粗体2__
```

## 斜体
1. *斜体1*
``` bash
*斜体1*
```
2. _斜体2_
``` bash
_斜体2_
```

## 粗体和斜体

***又粗又斜***

``` bash
***又粗又斜***
```

## 列表

无序列表使用 -、+ 或 * 表示，有序列表使用数字加点表示。

复制代码
``` bash
- 无序列表项 1
- 无序列表项 2
  - 嵌套无序列表项

1. 有序列表项 1
2. 有序列表项 2
   1. 嵌套有序列表项
```
## 链接和图片

* 链接使用格式

[这是一个链接](https://markdown.com.cn)

也可以直接表示链接

<https://markdown.com.cn>

* 图片使用格式。
`![图片alt](图片链接 "图片title")`
![这是一个图片](https://markdown.com.cn/assets/img/shiprock.c3b9a023.jpg "你儿豁")
*这个图片上有字*

邮箱使用格式
<fake@example.com>

``` bash
[这是一个链接](https://markdown.com.cn)
<https://markdown.com.cn>

![这是一个图片](https://markdown.com.cn/assets/img/shiprock.c3b9a023.jpg "图片title"")

<fake@example.com>
```

### 链接图片
[![沙漠中的岩石图片](https://markdown.com.cn/assets/img/shiprock.c3b9a023.jpg "点了就是刷新这个界面")](https://blog.tiepi.eu.org/_posts/hugo-test/)
*你点一下试试*

## 引用

使用 > 表示引用。
当然，也可以嵌套使用
> 这是一个引用段落。
>> 这是一个嵌套引用段落。
``` bash
> 这是一个引用段落。
>> 这是一个嵌套引用段落。
```

## 代码块
1. 用一个反引号`表示的
我更喜欢用来表示`强调`

行内代码使用反引号 ` 包围，多行代码块使用三个反引号 包围。

``` bash
这是 `行内代码` 示例。
```

2. 用三个反引号`表示的

## 分段
使用三个或更多的 -、* 或 _ 表示分割线。

1. 用`-`分段
---
2. 用`_`分段
___
3. 用`*`分段
***

### 分开式的链接

应该会很有用

[hobbit-hole][1]

[hobbit-hole][2]

[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle
[2]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle

``` bash
[hobbit-hole][1]

[hobbit-hole][2]

[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle
[2]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle
```

# 转义字符
要显示原本用于格式化 Markdown 文档的字符，请在字符前面添加反斜杠字符 \ 
