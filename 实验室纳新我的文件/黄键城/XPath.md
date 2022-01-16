# XPath表达式
- from lxml import etree
> 导入etree模块

## 实例化etree对象
1. 本地文档     【使用parse()函数进行实例化】
   - html = etree.parse('本地文档')

2. 网页源代码   【使用HTML()函数进行实例化】
   - html = etree.HTML('网页源代码')

## 用XPath表达式定位标签并提取数据  【用xpath()函数实现】
#### 定位标签
1. 标签名定位
   - 用‘/’和‘//’这两个符号进行标签的绝对路径的定位，并作为实参传入xpath()函数。
   > '/'为上下一层接一层的
   > '//'为上下隔多层标签

2. 索引定位
   - 在（1）的基础上如果同一层中有多个同名的标签节点，使用列表切片就能定位到所需的标签节点。

3. 属性定位
   - 在（1)的基础上再后面加上[@class='标签属性' ]。
   > print(html.xpath('//*[@class='title' ]))
   >> 其中实参里面的‘*’代表任何标签，也可以换成具体的标签名

4. 逻辑运算定位
   - 在（3）的基础上还不能定位到想要的标签就可以使用逻辑运算来定位
      - 使用“and”和“or”’进行标签属性的逻辑运算
      > html.xpath('//p[@class='title' and @name='color']')
      > html.xpath('//p[@class='title' or @name='color']')

#### 提取文本内容和属性值
   - 在实参后面添加“/text()”来提取该节点的直系文本内容
   - 在实参后面添加“//text()”来提取该节点下的所有文本内容
   - 在实参后面添加“/@属性名”来提取该节点的指定属性值
   > html.xpath('//*[@class='title' ]/text()')
   > html.xpath('//*[@class='title' ]//text()')
   > html.xpath('//*[@class='title' ]/@id')

## 快速获取标签节点的XPath表达式
   - 在网页中打开开发者工具，点击Elements查看网页源代码；找到要找的标签点击鼠标右键的Copy XPath选项即可获取到标签节点的XPath表达式