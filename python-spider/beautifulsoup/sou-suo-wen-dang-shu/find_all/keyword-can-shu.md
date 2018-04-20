# keyword参数

如果一个指定名字的参数不是搜索内置的参数名,搜索时会把该参数当作指定名字tag的属性来搜索,如果包含一个名字为`id`的参数,Beautiful Soup会搜索每个tag的”id”属性.

```text
soup.find_all(id='link2')
# [<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>]
```

如果传入`href`参数,Beautiful Soup会搜索每个tag的”href”属性:

```text
soup.find_all(href=re.compile("elsie"))
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>]
```

搜索指定名字的属性时可以使用的参数值包括[字符串](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id30),[正则表达式](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id31),[列表](http://beautifulsoup.readthedocs.io/zh_CN/latest/#id32),[True](http://beautifulsoup.readthedocs.io/zh_CN/latest/#true).

下面的例子在文档树中查找所有包含`id`属性的tag,无论`id`的值是什么:

```text
soup.find_all(id=True)
# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
```

使用多个指定名字的参数可以同时过滤tag的多个属性:

```text
soup.find_all(href=re.compile("elsie"), id='link1')
# [<a class="sister" href="http://example.com/elsie" id="link1">three</a>]
```

有些tag属性在搜索不能使用,比如HTML5中的 data-\* 属性:

```text
data_soup = BeautifulSoup('<div data-foo="value">foo!</div>')
data_soup.find_all(data-foo="value")
# SyntaxError: keyword can't be an expression
```

但是可以通过`find_all()`方法的`attrs`参数定义一个字典参数来搜索包含特殊属性的tag:

```text
data_soup.find_all(attrs={"data-foo": "value"})
# [<div data-foo="value">foo!</div>]
```

