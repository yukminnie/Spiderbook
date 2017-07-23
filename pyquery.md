# Pyquery笔记



---

```
1.引入pyquery

from pyquery import PyQuery as pq

2.声明pyquery对象

doc = pq(html)
    doc = pq(rul=http://www.baidu.com")   ---url初始化
    doc = pq(filename='demo.html')        ---文件初始化

3.打印doc

print(doc('li'))
    print(doc('#container .list li'))     基本css选择器
    
4.子元素

items = doc('.list')
lis = items.find('li')   ---常用方法

lis = items.children()     

lis = items.children('.active')

5.父元素

items = doc('.list')
container = items.parent()  

parents = items.parents()  ---查找祖先节点

parent = items.parents('.wrap')  ---祖先节点的筛选

6.兄弟元素

li = doc('.list .item-0.active')  ---.item-0和.active属于并列关系
print(li.siblings())     ---上述筛选出元素的兄弟元素

print(li.siblings('.active'))  ---继续筛选

7.遍历元素

lis = doc('li').items()
    for li in lis:
        print(li)    ---返回的是一个生成器
        
8.获取信息

a = doc('.item-0.active a')

print(a)     
print(a.attr('href'))]   ---获取属性信息
print(a.attr.href)       ---同上

9.获取文本
a = doc('.item-0.active a')

print(a)
print(a.text())

10.获取html
li = doc('.item-0.active')

print(li)
print(li.html())   ---去除外层，不常用，可用于获取html文章

11.DOM

addClass  removeClass -------用于对Class原有属性进行快速操作
li = doc('.item-0.active')
print(li)

li.removeClass('active')
print(li)

li.addClass('active')
print(li)


attr，css   ------   用于对Class属性进行额外的添加操作
li = doc('.item-0.active')

li.attr('name','link')
li.css('font_size','14px')

remove --------  常用方法

<div class='wrap'>
    hello,world
    <p>This is paragraph.</p>
</div>

wrap = doc('wrap')
print(wrap.text())
wrap.find('p').remove()
print(wrap.text())

12.其他dom方法

http://pyquery.readthedocs.io/en/latest/api.html

13.伪类选择器

doc = pq(html)

li = doc('li:first-child')
li = doc('li:last-child')
li = doc('li:nth-child(s)')
li = doc('li:gt(2)')
li = doc('li:nth-child(2n)')
li = doc('li:contains(second)')

14.更多的css选择器
w3c

15.官方文档
http://pyquery.readthedocs.io/



```





