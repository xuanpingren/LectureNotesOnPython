列表
---

语言的内置（built-in）类型。注意与String类比，index也是从0开始， in操作符， 求长度，获得字串，遍历操作类似。

``
[]
[10, 20, 30, 40]
['crunchy frog', 'ram bladder', 'lark vomit']
``

列表中的元素不需要是同一类型的

['spam', 2.0, 5, [10, 20]] 

列表[10,20]在另外一个列表中，这叫嵌套列表。

['spam', 1, ['Brie', 'Roquefort', 'Pol le Veq'], [1, 2, 3]]，长度是多少？


列表是 Mutable类型。值可以在原地变。（注意与String的区别）。

IndexError

遍历

for cheese in cheeses:
    print(cheese)


for i in range(len(numbers)):
    numbers[i] = numbers[i] * 2

for x in []:
    print('This never happens.')

讨论软件工程认证数据输入问题。


+操作符用来连接， *操作符用来重复

列表的方法

append

extend

sort

t = ['d', 'c', 'e', 'b', 'a']
t.sort() # 文t.sort()返回什么值？
t

sum  - reduce方法，把几个值变成一个值

map方法，把几个值变成另外几个值

def f(x):
    return 2*x

list(map(f, [1,2]]))



filter方法，从几个值中选择符合条件的几个值

def f(x):
    if x % 2 == 0:
        return True
    return False

list(filter(f, [1,2,3,4]))

pop

t = ['a', 'b', 'c']
x = t.pop(1) # pop可不带参数，不带参数返回哪个值？

t = ['a', 'b', 'c']
del t[1]

t = ['a', 'b', 'c', 'd', 'e', 'f']
del t[1:5]


t = ['a', 'b', 'c']
t.remove('b')


list_of_characters = list('spam')
list_of_words = 'spam should be filtered'.split()
list_of_words = 'spam-should-be-filtered'.split('-')


join方法

','.join(['1','2','3'])


a = 'banana'
b = 'banana'
a is b # a与b是不是指向同一个值
a == b


a = [1, 2, 3]
b = [1, 2, 3]
a is b # not identical, a and b are not the same object 
a == b # equivalent     though they have the same values


别名（Aliasing）

a = [1, 2, 3]
b = a
b is a 

把变量名与对象联系起来叫做reference。
a与b是指向[1,2,3]的两个references。
因为[1,2,3]是mutable的，所以使用a对[1,2,3]做改变同样影响到b对应的值。
error-prone（易错）

列表作为参数
-----------

def delete_head(t):
    del t[0]

letters = ['a', 'b', 'c']
delete_head(letters) # letters and t points to the same list object.
letters


注意区别append与+操作符
---------------------

t1 = [1, 2]
t2 = t1.append(3)
t1
[1, 2, 3]
t2


t3 = t1 + [4]
t3
[1, 2, 3, 4]
t1
[1, 2, 3]



区别如下两个函数
def bad_delete_head(t):
    t = t[1:] # WRONG!

def tail(t):
    return t[1:]



---------------------------------
字典（Dictionary）

Mutable

超级有用

d = {} or d = dict()


d = {'hot':'热', 'cool':'凉', 'cold':'冷'}
d['warm'] = '温'
d['warm']
d['freezing'] # KeyError
len(d)

'warm' in d
'温' in d.values()

key
value
key-value pair (item)
item的顺序不可预测，不是按照创建时的顺序。

练习：给定一个字符串，数出每个字母出现的频率。


参考
------

- Think Python 2e – Green Tea Press.  http://greenteapress.com/thinkpython2/thinkpython2.pdf.  
