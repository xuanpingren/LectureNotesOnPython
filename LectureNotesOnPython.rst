=======================
Lecture Notes on Python
=======================

:Authors:
   蓝珲 (lanhui AT zjnu.edu.cn)

:Version: 0.1 of 2019/03/30

	  
非学究写书，无空洞行文。Python语法简洁，库函数全面强大，编程速度快，运行速度也不慢。

.. contents:: 内容目录


Python的发音纠正
------------------------------

国人普遍把th发作s。 Not quite correct。

\ ˈpī-ˌthän , -thən\  pronounciation_

.. _pronounciation: https://cn.bing.com/search?q=define%20python&tf=U2VydmljZT1EaWN0aW9uYXJ5QW5zd2VyVjIgU2NlbmFyaW89RGVmaW5pdGlvblNjZW5hcmlvIFBvc2l0aW9uPU5PUCBSYW5raW5nRGF0YT1UcnVlIEZvcmNlUGxhY2U9RmFsc2UgUGFpcnM9RGljdGlvbmFyeVdvcmQ6cHl0aG9uO3NjbjpEZWZpbml0aW9uU2NlbmFyaW87cDpRQVM7IHw%3d&hs=hyRBF0mYq9hrfQUq66DIZnFVta1ZGRfBiBks25oUguk%3d



Python源流
------------------------------

Python之父Guido van Rossum，荷兰人，1956年生，1982年阿姆斯特丹大学获得
数学与计算机科学硕士学位。有过ABC语言的工作经验。1989年设计了Python语
言。

Python语法简洁，有大而全而有用的标准库。

自然（natural）语言。特点：歧义，重复。“The penny dropped。” “不要。”

正式（formal）语言。特点：只管字面意思。

计算机组成概要：CPU，总线，内存，硬盘。

Bit, byte, KB, MB, GB, TB换算。

变量的命名。如，层叠策略，用CDCL还是TiledStrategy?

教务管理系统，http://10.1.70.164/jwglxt?

习语言、易语言等目前非主流语言。

最简单的类定义:


    class A:
        pass


以上面的类为蓝本，创建一个实例：a = A()。 虽然这个a什么也做不了。

Python文件命令行执行。 python a.py。

函数头的三要素：def，函数名，参数列表:


    | def add_number(a, b):
    |     return a + b
    
    | def add_lst(a, b):
    |     if len(a) != len(b):
    |         return 'ERROR: a and b not in equal length.'
    |     n = len(a)
    |     result = []
    |     for i in range(n):
    |         result.append(a[i] + b[i])
    |     return result
    |
    | print( add_lst([1,2,3],[-1,-2,-3]) )




Python的关键词
--------------------------------


| def pass
| from import
| False True
| in
| None
| class 
| return
| while for
| continue break 
| and or not
| if else elif
| try except finally raise
| lambda nonlocal 
| del global with
| yield assert   
| as is


关键词被语言留用（reserved），无法作变量名。


值的类型
-------------------------

所有的值都是对象。a = 5, help(a)  a.bit_length()

数字。1， 1.，1.1， .1, 1e1, 1e-1, 1E1, 1E-1

字符串（string）。'hello', 100 * 'hello', 'hello' * 100, 'Weight is %4.2f kg' % (70.2)
       f = open('a.html')
       s = f.read()
       f.close()

列表（list）。['a', 'b', 'c', 'd']
     ['bob', 170, 'john', '180']
     [1, 2, 3, 4]
     range(10) 返回一个range对象。可以用list函数把这个对象变成列表。
     等价的是range(0, 10, 1)，从0开始，步进1，不包括10。
     A list of list
     A list of tuples
     A list of objects

元组（tuple），字典（dict）。



变量（Variable）
------------------------------------

是一个名字（name），是指向一个值（value）的名字。

值存放在内存（memory）中的某个地址。

尽量选有意义的简短的名字。比如，代表个数用n，代表索引用i，j，k。

关键词不能用作变量名。


值存放在内存某处。值会记录指向它的变量个数。

为节省空间，如果几个变量的值相同，那么这些变量有时会指向这个值（而不是为每个变量单独分配内存空间单独存放该值）。

这叫做interning技术。但并非总是如此。


| a = 10
| b = 10
| c = 10
| id(a), id(b), id(c)
| (8791229060416, 8791229060416, 8791229060416)


值10存在地址8791229060416，所有a，b，c三个变量都指向（point to）这个地址。



| x = 257
| y = 257
| id(x), id(y)
| (46487024, 46487952)


以上虽然变量x与y的值都是一样，可是这两个值存放在不同的内存地址。


| s1 = 'hello'
| s2 = 'hello'
| id(s1), id(s2)
| s1 == s2
| s1 is s2

| s1 = 'h' * 100
| s2 = 'h' * 100
| id(s1), id(s2)

| s3 = 'hello, world!'
| s4 = 'hello, world!'
| id(s3), id(s4)
| (46703536, 46705136)



| class A:
|    pass

| a = A()
| b = A()
| a
| <__main__.A object at 0x0000000002CD92E8>
| b
| <__main__.A object at 0x0000000002CD9240>



| x = [1,2,3]
| id(x)
| 46869512
| y = x
| id(y)
| 46869512
| x.append(4)
| x
| [1, 2, 3, 4]
| y
| [1, 2, 3, 4]

| x = []
| id(x)
| 46869640


| x = [1,2,3,4]
| y = [1,2,3,4]
| id(x)
| 46869768
| id(y)
| 46868808


一个没有名字与之对应的值将会被清出内存。

参考资料：

- http://foobarnbaz.com/2012/07/08/understanding-python-variables/
- https://stackoverflow.com/questions/19721002/is-a-variable-the-name-the-value-or-the-memory-location



可变（mutable）类型与不可变类型
----------------------------------------------------------

字符串是不可变的（immutable）类型，不能在原内存地址改变。

a = 'hello'  不可以原地修改a[0] = 'H'。需要修改a的值时，需要对a进行重新赋值a = 'Hello'。

列表是可变（mutable）类型，能在原内存地址改变。

a = [1, 2]   可以原地修改a[0] = 2

参考资料：

- https://stackoverflow.com/questions/8056130/immutable-vs-mutable-types



表达式（expression）：值，变量或操作符的组合。

    | 17
    | n + 2

语句（statement）：能够制造一个变量或者显示信息的代码。

    | n = 17
    | print(n)




数与格式化显示
-------------------------

    | x = 3.1415926
    
    | print('%4.0f' % (x))
    | print('%4.1f' % (x))
    | print('%4.2f' % (x))
    | print('%4.3f' % (x))
    | print('%4.4f' % (x))
    
    
    | print('%6.0f' % (x))
    | print('%6.1f' % (x))
    | print('%6.2f' % (x))
    | print('%6.3f' % (x))
    | print('%6.4f' % (x))
    
    
    | print('%.0f' % (x))
    | print('%.1f' % (x))
    | print('%.2f' % (x))
    | print('%.3f' % (x))
    | print('%.4f' % (x))
    | print('%.5f' % (x))
    | print('%.6f' % (x))
    | print('%.7f' % (x))
    | print('%.8f' % (x))
    | print('%.9f' % (x))
    | print('%.15f' % (x))
    | print('%.16f' % (x))
    | print('%.17f' % (x))
    | print('%.18f' % (x))
    
    | print('%4.f' % (x))
    | print('%5.f' % (x))
    | print('%6.f' % (x))
    | print('%7.f' % (x))
    | print('%8.f' % (x))
    
    | print('%f' % (x))
    


字符串（Strings）
------------------------------------------

由字符组成。

| fruit = 'banana!'
| first_letter = fruit[0]
| second_letter = fruit[1]

索引（index）从0开始，所以1代表第二个字符。只用整数。

负整数代表从字符串末尾开始。如fruit[-1]代表fruit字符串最后一个字符。

| i = 1
| fruit[i]
| fruit[i+1]

len()函数。返回字符串字符个数。len(fruit)。

| L = len(fruit)
| fruit[L-1]，最后一个字符。与fruit[-1]等价。


遍历（traverse）字符串。

    | fruit = 'banana'
    | for c in fruit:
    |     print(c)
    

反向遍历。

    | fruit = 'banana'
    | for i in range(len(fruit)-1,-1,-1):
    |     print(fruit[i])
    
    | fruit = 'banana'
    | for c in fruit[::-1]:  # [start,stop,step]
    |     print(c)
    
    
    | fruit = 'banana'
    | for c in ''.join(reversed(fruit)):
    |     print(c)
    

以上 ``# [start,stop,step]`` 代表注释（comment），注释以 ``#`` 号开头。
    


字符串相加（concatenation）
-------------------------------------------------------

输出Jack, Kack, Lack, Mack, Nack, Ouack, Pack, and Quack

| prefixes = 'JKLMNOPQ'
| suffix = 'ack'
| for c in prefixes:
|     if c == 'O' or c == 'Q':
|        print(c + 'u' + suffix)
|     else:
|         print(c + suffix)


子串（slice）
-------------------------------------------------------

s[n:m]，其中n或m可省略。
包括第n个字符，不包括第m个字符。（索引自0开始）

| s = 'Monty Python'
| s[0:5]
| s[6:12]
| s[:5]
| s[6:]
| s[:]

n一般小于m。如果n大于等于m，那么就返回空字符串。

空字符串的长度是0。

字符串是immutable的。不能改变已有的字符串。

| greeting = 'Hello, world!'
| greeting[0] = 'J'

| greeting = 'Hello, world!'
| new_greeting = 'J' + greeting[1:] 



搜索字符串
-----------------------------

| def find(word, c):
|     i = 0
|     while i < len(word):
|         if word[i] == c:
|             return i
|         i = i + 1
|     return -1

| print(find('banana', 'a'))

练习一：加第三个参数，设定从哪个字符开始搜起。

练习二：加第三个参数，设定从哪个方向开始搜起。

String对象有内置函数find。

数字符串中某个字符的个数。

练习：用上面三参数的find来做。


String类（对象）方法
------------------------------------------

| upper()
| lower()

方法调用：invocation/call

| word.find('na')
| word.find('na', 3)
| name.find('b', 1, 2)


in操作符
------------------------------------------

'a' in 'banana'
'seed' in 'banana'

练习：写出下面的函数，使得
in_both('apples', 'oranges')返回'aes'


字符串比较
-------------------------------------------

字典序（alphabetical order）。大写字母排在小写字母前。


字符串之间可以有以下对比操作:

| ==
| >, >=
| <, <=


练习：写is_reverse函数，使得is_reverse('god', 'dog')返回True。    

    

find_from函数的两种实现。如果能够找出错误，给1分奖励。

字符串是对象（object）。

对象的本质涵义 - data construct。

计算复杂度。

即兴定义函数，制造一个长度不小于4的密码。



列表
--------------------

语言的内置（built-in）类型。注意与String类比，index也是从0开始， in操作符， 求长度，获得字串，遍历操作类似。


    | [ ]
    | [10, 20, 30, 40]
    | ['crunchy frog', 'ram bladder', 'lark vomit']
    

列表中的元素不需要是同一类型的: ``['spam', 2.0, 5, [10, 20]]``

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

    
.. 讨论软件工程认证数据输入问题。


``+`` 操作符用来连接， ``*`` 操作符用来重复。

列表的方法

    append
    
    extend
    
    sort
    
    t = ['d', 'c', 'e', 'b', 'a']

    t.sort() # 问t.sort()返回什么值？

    t
    
sum  - reduce方法，把几个值变成一个值

map方法，把几个值变成另外几个值

def f(x):
    return 2*x

list(map(f, [1,2]]))


filter方法，从几个值中选择符合条件的几个值。


    | def f(x):
    |     if x % 2 == 0:
    |         return True
    |     return False

    | list(filter(f, [1,2,3,4]))


pop

    | t = ['a', 'b', 'c']
    | x = t.pop(1) # pop可不带参数，不带参数返回哪个值？
    

del

    | t = ['a', 'b', 'c']
    | del t[1]
    
    | t = ['a', 'b', 'c', 'd', 'e', 'f']
    | del t[1:5]
    

remove

    | t = ['a', 'b', 'c']
    | t.remove('b')
    

split

    | list_of_characters = list('spam')
    | list_of_words = 'spam should be filtered'.split()
    | list_of_words = 'spam-should-be-filtered'.split('-')
    

join方法

    | ','.join(['1','2','3'])
    
    
    | a = 'banana'
    | b = 'banana'
    | a is b # a与b是不是指向同一个值
    | a == b
    
    
    | a = [1, 2, 3]
    | b = [1, 2, 3]
    | a is b # not identical, a and b are not the same object 
    | a == b # equivalent     though they have the same values
    

别名（Aliasing）

a = [1, 2, 3]
b = a
b is a 

把变量名与对象联系起来叫做reference。
a与b是指向[1,2,3]的两个references。
因为[1,2,3]是mutable的，所以使用a对[1,2,3]做改变同样影响到b对应的值。
error-prone（易错）



列表作为参数
---------------------------------------------

    | def delete_head(t):
    |     del t[0]
    
    | letters = ['a', 'b', 'c']
    | delete_head(letters) # letters and t points to the same list object.
    | letters
    

注意区别 ``append`` 与 ``+`` 操作符
----------------------------------------------

    | t1 = [1, 2]
    | t2 = t1.append(3)
    | t1
    | [1, 2, 3]
    | t2
    
    
    | t3 = t1 + [4]
    | t3
    | [1, 2, 3, 4]
    | t1
    | [1, 2, 3]
    


区别如下两个函数:

    def bad_delete_head(t):
        t = t[1:] # WRONG!
    
    def tail(t):
        return t[1:]
    

TDD - Test-driven Development
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

测试驱动开发。 My favourite。 刺激有挑战性。 帮助厘清需求。  帮助编写代码。

推荐使用pytest。如何安装？ 使用命令 ``pip install pytest``。

在 ``test_cases.py`` 写如下测试用例。然后在命令行运行： ``python -m pytest test_cases.py`` 。

.. code:: python

	  # Copyright (c) Hui Lan 2019

          import random
          import string
          
          def make_password(n):
              '''
              Return a string of length n consisting of a combination of
              letters, digits and special characters.  Note that each password
              must have at least one lower case letter, one upper case letter,
              one digit and one special charater.  Return an empty string if n
              is less than 4.
              '''
          
              if n < 4:
                  return ''
              
              password = random.choice(string.ascii_lowercase) + \
                  random.choice(string.ascii_uppercase) + \
                  random.choice(string.digits) + \
                  random.choice(string.punctuation) + \
                  ''.join([random.choice(string.ascii_letters + string.digits + string.punctuation) for i in range(n-4)])
          
              return ''.join(random.sample(password, n)) # shuffle password then return
          
          
          
          
          if __name__ == '__main__':
              for n in range(0,20):
                  pwd = make_password(n)
                  print(pwd)
            



计算复杂度
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

用Big O表述复杂度。O(n)， O(n^2), O(n^3)。



密码实验回顾。



字典（Dictionary）
---------------------------------

Mutable数据类型。

实际开发中超级有用。

    | d = {} or d = dict()
    
    | d = {'hot':'热', 'cool':'凉', 'cold':'冷'}
    | d['warm'] = '温'
    | d['warm']
    | d['freezing'] # KeyError
    | len(d)
    
    | 'warm' in d
    | '温' in d.values()
    
key

value

key-value pair (item)

item的顺序不可预测，不是按照创建时的顺序。


递增开发（Incremental Development）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

每次完成一小点。从易到难。


练习：给定一个字符串，数出每个字母出现的频率。

.. code:: python
	  
     def histogram(s):
         ''' Cannot pass any test cases. '''
         pass
    
     def histogram(s):
         ''' Can pass the test case in which s is an empty string. '''
         d = {}
         return d
    
     def histogram(s):
         ''' Can pass the test cases in which all characters in s are unique. '''
         d = {}
         for c in s:
             d[c] = 1
         return d
    
     def histogram(s):
         ''' Can pass all test cases. '''
         d = {}
         for c in s:
             if c not in d:
                 d[c] = 1
             else:
                 d[c] += 1
         return d
    
    
     h = histogram('good')
     print(h)
    

练习：给定一个字符串，数出每个单词出现的频率。

练习：给定一个新闻文本，数出每个单词出现的频率。考虑以下方面，（1）只考虑字典里有的单词。（2）单词周围如有标点符号，要先移除。

.. code:: python
	  
	  # Copyright (C) 2019 Hui Lan
          # The following line fixes SyntaxError: Non-UTF-8 code starting with ...
          # coding=utf8
          
          def file2lst(fname):
              ''' Return a list where each element is a word from fname. '''
              L = []
              f = open(fname)
              for line in f:
                  line = line.strip()
                  lst = line.split()
                  for x in lst:
                      L.append(x)
              f.close()
              return L
          
          
          def lst2dict(lst):
              ''' Return a dictionary given list lst.  Each key is an element in the lst.
              The value is always 1.'''
              d = {}
              for w in lst:
                  d[w] = 1 
              return d
          
          
          import string
          def remove_punctuation(s):
              p = ',.:’“”' + string.punctuation  
              t = ''
              for c in s:
                  if not c in p:
                      t += c
                  elif c == '’': # handle the case such as May’s
                      return t
              return t
          
          def word_frequency(fname, english_dictionary):
              ''' Return a dictionary where each key is a word both in the file fname and in 
              the dictionary english_dictionary, and the corresponding value is the frequency
              of that word.'''
              d = {}
              L = file2lst(fname)
              for x in L:
                  x = remove_punctuation(x.lower())
                  if x in english_dictionary:
                      if not x in d:
                          d[x] = 1
                      else:
                          d[x] += 1
              return d
          
          
          def sort_by_value(d):
              ''' Return a sorted list of tuples, each tuple containing a key and a value.
                  Note that the tuples are order in descending order of the value.'''
              import operator
              lst = sorted(d.items(), key=operator.itemgetter(1), reverse=True)    
              return lst
          
          
          if __name__ == '__main__':    
              ed = lst2dict(file2lst('words.txt')) # from http://greenteapress.com/thinkpython2/code/words.txt
              d = word_frequency('brexit-news.txt', ed)
              lst = sort_by_value(d)
              for x in lst:
                  print('%s (%d)' % (x[0], x[1]))
          
    

key与value互换
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

注意到在原来的字典中一个value可能对应多个key的值。比如 ``d = {'a':1, 'b':2, 'c':2}`` 中，2就对应两个key，'b'与'c'。


.. code:: python
	  
          def inverse_dictionary(d):
              d2 = {}
              for k in d:
                  v = d[k]
                  if not v in d2:
                      d2[v] = [k]
                  else:
                      d2[v].append(k)
              return d2
          
          
          
          d = {'a':1, 'b':2, 'c':2}
          d2 = inverse_dictionary(d)
          print(d2)
          

练习： 用 ``inverse_dictionary`` 对上面 ``d = word_frequency('brexit-news.txt', ed)`` 产生的 ``d`` 进行转化。然后按照单词出现频率从高到低把所有单词都显示出来。每行显示一个频率内的所有单词。


.. code:: python
	  
          d2 = inverse_dictionary(d)
          for k in sorted(d2.keys(), reverse=True):
              print('%d %s' % (k, ' '.join(d2[k])))
              

练习： 使用 ``setdefault`` 方法对上面的 ``inverse_dictionary`` 进行简化 （减少行数）。


.. code:: python



          def inverse_dictionary(d):
              d2 = {}
              for k in d:
                  v = d[k]
                  d2.setdefault(v, []).append(k)
          
              return d2
          



函数
------

函数 ``unique_words`` 与 ``unique_words2`` 哪个运行速度快？

.. code:: python

          def unique_words(lst):
              d = {}
              for x in lst:
                  d[x] = 1
              return sorted(d.keys())
          
          def unique_words2(lst):
              return sorted(list(set(lst)))
          
          
          N = 10000000
          print(unique_words(['hello', 'world', 'am', 'he'] * N))
          print(unique_words2(['hello', 'world', 'am', 'he'] * N))
          


局部变量
~~~~~~~~~~~~~~~~

在函数之内。函数执行结束，局部变量消失。


全局变量
~~~~~~~~~~~~~~~~

全局变量位于函数之外，模块之内。全局变量对所有模块内的函数可见（可读）。如果在函数内要对全局变量重新赋值，那么要先用 ``global`` 声明之 （declare）。


.. code:: python
	  
          verbose = True
          
          def example1():
              if verbose:
                  print('Running example1')
                  
          def example2():
              verbose = False  # a NEW local variable verbose
              if verbose:
                  print('Running example2')
                  
          def example3():
              global verbose # I am actually going to use the global variable verbose; don't create a local one.
              verbose = False
              if verbose:
                  print('Running example3')
          
          
          
          print(verbose)     
          example1()
          
          print(verbose) 
          example2()
          example1()
          
          print(verbose) 
          example3()
          example1()
          
          print(verbose) 
          


全局的列表与字典，如果只需改变其内容，而不是重新赋值，则不需要用 ``global`` 声明。


.. code:: python
	  
          record = {'s1':65, 's2':60}
          
          def add_score(student, score):
              record[student] = score
              
              
          print(record)
          add_score('s3', 75)
          print(record)


练习： 定义一个函数 ``empty_dict`` 清空字典 ``record``。 要求: 不能用 ``return`` 语句。 提示： 可以用 ``pop`` 方法， 或者直接给 ``record`` 赋值 ``{}`` 。


调用函数与传递参数
~~~~~~~~~~~~~~~~~~~~~~~~~

在使用函数前要先确定函数已经被定义。

区别 ``argument`` 与 ``parameter`` 。传过去的是 ``argument`` ， 函数头的参数列表是 ``parameter`` 。 ``argument`` 的值赋给 ``parameter`` ， ``parameter`` 是函数的局部变量。

``argument`` 与 ``parameter`` 的名字可以相同也可以不同。


.. code:: python
	  
          def reverse_string(s):
              t = ''
              for i in range(len(s)-1,-1,-1):
                  t += s[i]
              return t
          


          s = 'put'
          t = reverse_string(s)
          print(t)

以上 s 一个是全局变量一个是局部变量。

以上 t 一个是全局变量一个是局部变量。 




函数执行顺序 （flow of execution）
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

函数的定义不执行，被调用时才执行。

顺序执行。 当遇到函数调用时，跳转到函数，执行函数，函数返回后继续执行跳转地后一条语句。



参考
------

- Think Python 2e – Green Tea Press.  http://greenteapress.com/thinkpython2/thinkpython2.pdf.  


.. Make a html page from this file.  Issue the following command:
   pip install docutils && rst2html.py LectureNotesOnPython.rst LectureNotesOnPython.html
