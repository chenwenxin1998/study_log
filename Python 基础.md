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

