# Python 基础

## 1.利用doctest进行单元测试

利用doctest可以将单元测试集成到注释中，单元测试可以保证测试单元的正确性，同时，利用doctest也可以方便团队更好的阅读代码，更加方便的理解函数的使用。

```python
def format_str_to_list(s):
    """
    format_str_to_list: segment s by ',' and return a list
    :Author:  chenwenxin
    :Create:  2021/2/22 12:48
    >>> format_str_to_list('a64e3bd874af11ebb79bd0abd5f3ef4d,a64e3bd874af11ebb79bd0abd5f3ef4d,a64e3bd874af11ebb79bd0abd5f3ef4d')
    ['a64e3bd874af11ebb79bd0abd5f3ef4d', 'a64e3bd874af11ebb79bd0abd5f3ef4d', 'a64e3bd874af11ebb79bd0abd5f3ef4d']
    """
    return s.split(",")

if __name__ == '__main__':
    import doctest
    print(doctest.testmod(verbose=False, report=False))

```



## 2.lambda函数

lambda函数，即匿名函数，使用起来十分简便，单行即可完成

```python
add = lambda x,y : x+y
print(add(1,2))
#输出 3

#等于
def add2(x, y)
	return x + y
print(add2(1,2))
#输出 3
```



## 3.map函数

**map()** 会根据提供的函数对指定序列做映射。

第一个参数 function 以参数序列中的每一个元素调用 function 函数，返回包含每次 function 函数返回值的新列表。

示例：

```python
def square(x):
    return x*x
res = map(square, [1, 2, 3])
#res  [1, 4, 9]
```

map函数也常和lambda函数连用

如以上代码可写成：

```python
res = map((lambda x:x*x),[1, 2, 3])
```

十分简洁。

## 4.yield

代码一

```python
def get_random_number_list():
    import random
    i = 0
    res = []
    while i<1000:
    	res.append(random.randint(0,1000))
     return res
```

get_random_number_list（）将会返回一个1000个int的list

假设有一web系统需要使用到上述的的函数，那么每有一次涉及到上述函数的时候，都会去开辟一块存放有1000个int数据的空间，如果请求很多，消耗的内存是十分惊人的，这时候我们使用yield关键字来实现上述函数：

```python
def get_random_number():
    import random
    i = 0
    while i<1000:
        a = random.randint(0,1000)
        yield a

```

通常，我们将带有yield关键字的函数称之为generator,这个函数并不会像之前的函数一样返回一个list,他的使用如下

```python
>>>res = def_get_random()
>>>res.next()
1
>>>res.next()
5
#
```



generator并不会返回函数的执行结果，实际上，他甚至都没有调用，当使用next()函数的时候，generator才开始执行，并且代码执行到第一个yield的时候停止，继续使用next（）函数，代码继续执行到下一个yield位置，可以理解为他的结果是动态生成的，这样就不用像get_random_number_list函数一样返回一个list而占用很多的内存。