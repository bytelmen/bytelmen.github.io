---
layout: post
title:  "python中的sort和sorted"
date:   2016-04-07 23:11:09 +0800
categories: python
---
sorted 和sort是python内置的函数,但是sort是列表的函数，而sorted直接对容器进行操作，返回一个新的容器，容器可以是list，tuple，可迭代对象等。
a.sort()排序后会改变a。而sorted(a)会返回一个排序后的容器，a并不变化。

实际测试sorted比sort速度快。

#### 返回下标index
numpy 中有个函数argsort()可以返回排序后的下标。对于列表`s=[2, 3, 1, 4, 5]`,`numpy.argsort(s)`的返回值是array([2, 0, 1, 3, 4]),这个表示排序的列表[1, 2, 3, 4, 5]中元素对应于s中的下标为[2, 0, 1, 3, 4]。使用lettcode刷题时，不能导入包。所以只能用其他方式来实现这个功能。sorted就可以实现。`sorted(range(len(s)), key=lambda k: s[k])`的返回值就是[2, 0, 1, 3, 4]。

用help(sorted)查看帮助得到：
```sorted(iterable, key=None, reverse=False) --> new sorted list```

第一个参数是可迭代对象，第二个参数是用来比较的关键字。sorted函数是返回iterable按照key参数制定的关键字排序后的新的列表。`sorted(range(len(s)), key=lambda k: s[k])`则是返回range(lens)按照关键字s[k]排序后的结果。（k是从第一个参数range(lens)中取元素）
