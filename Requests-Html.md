## 推荐一个解析HTML的Python库--Requests-HTML

HTML Parsing for Humans, 这句话是库作者(kennethreitz)原话, 提现出了这个库的人性化, 话不多说, 来看几个例子吧. 
作者以Python官网做的例子, 在这里我用CSDN吧, 嘻嘻.
首先获取首页:

``` python
>>> from requests_html import session
>>> r = session.get('https://www.csdn.net')
```
获取所有连接:

``` python
 r.html.links
{'http://blog.csdn.net/sfM06sqVW55DFt1', '/nav/engineering', 'http://www.programmer.com.cn/',...}
# 由于这里连接较多 在这里仅仅粘贴一部分
```
获取所有绝对地址

``` python
 r.html.absolute_links
{'https://www.csdn.net/nav/iot', 'http://blog.csdn.net/sfM06sqVW55DFt1', ... ,}
```

使用JQuery选择器

``` python
>>> my_carousel = r.html.find('#myCarousel', first=True)
>>> print(my_carousel.text)
程序员们，你们再这样下去会没朋友的
从一份不合格的白皮书，了解蔡文胜辟谣美链背后的蹊跷
吉利花90亿美元成奔驰母公司最大股东，背后打的什么算盘？
一夜身价暴涨千倍，如何发布自己的ICO？
一个优秀的程序员是如何炼成的
Previous
Next
```
获取元素属性

```
>>> my_carousel.attrs
{'id': 'myCarousel', 'class': 'slide', 'data-ride': 'carousel'}
```
通过元素获取元素:

```
>>> my_carousel.find('a')
[<Element 'a' href='http://blog.csdn.net/csdnsevenn/article/details/79366722' target='_blank'>, ... ,] # 元素过多 不多展示了
```

将HTML转换为markdown:

``` python
>>> print(about.markdown)

* [About](/about/)

  * [Applications](/about/apps/)
  * [Quotes](/about/quotes/)
  * [Getting Started](/about/gettingstarted/)
  * [Help](/about/help/)
  * [Python Brochure](http://brochure.getpython.info/)
# 这里粘贴了作者的例子, CSDN上获取的没有这个例子清晰
```

支持xpath解析

```
>>> r.html.xpath('div')
[<Element 'div' class='read_num'>, <Element 'div' class='read_num'>,  ... ,] 
```
个人感觉这个库真的是很人性化, 并且源码并不多, 欢迎有兴趣的可以阅读一下, 小白一枚 让大神们见笑了.

[源码地址](https://github.com/kennethreitz/requests-html)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjU1ODYwODM1XX0=
-->