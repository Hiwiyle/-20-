# BeautifulSoup模块学习笔记
#### 导入模块
- from bs4 import BeautifulSoup
### 实例化对象
- soup = BeautifulSoup（文件名， ‘lxml’）
- soup = BeautifulSoup（从网页中获取到的源代码， ‘lxml'）
   - ‘lxml’：是指定解释器为lxml
   - 第二个的网页源代码要记得用.text()的方法
### 定位内容 （都是对已经实例化过的对象使用的方法）
#### 通过标签名定位
- **对实例化对象使用.标签的方法**
   - soup.p     *通过标签名地位第一个p标签*
#### 通过标签属性定位 【实例方法.find() & .find_all()】
- **传入实参（class_='标签属性'）**
   - soup.find(class_='first')    *返回class属性值为first的第一个标签*
   - soup.find_all(class_='first')    *返回class属性值为first的所有标签的列表*
#### 通过标签名+标签属性定位 【实例方法.find() & .find_all()】
- **传入实参（'标签名', class_='标签属性'）**
   - soup.find('div', class_='first')    *返回标签名为div和其属性为first的第一个标签*
   - soup.find_all('div', class_='first')    *返回标签名为div和其属性值为first的所有标签的列表*
#### 通过选择器定位 【实例方法.select()】
1. id选择器 【传入实参('#id值')】
   - '#'表示id选择器
   - soup.select('#first')    *返回所有符合id为first的标签列表*
2. class选择器 【传入实参('.class值')】
   - '.'表示class选择器
   - soup.select('.first')    *返回所有符合class为first的标签列表*
3. 标签选择器 【传入实参('标签名')】
   - 不需要在前面加入任何符号
   - soup.select('li')    *返回所有符合标签名为li的标签列表*
4. 层级选择器 【在层级之间用>符号隔开】
   - soup.select('div>ul>#first')    *选中所有div标签下ul标签中id属性值为first的所有标签列表*
   - soup.select('div>ul>li')    *选中所有div标签下所有ul标签中的所有li标签*
   - soup.select('div li')    *选中div标签包含的所有li标签*
### 从标签中提取文本内容和属性值
1. 从标签中提取文本内容
   - soup.select('.first')[1].string    *string属性返回的是指定标签的直系文本，即直接存在于该标签中的文本*
   - soup.select('.first')[1].text    *text属性返回的是指定标签下的所有文本*
2. 从标签中提取属性
   - soup.find(class_='first')['属性名']
      - soup.find(class_='first')['class']    *提取该标签下的class属性*