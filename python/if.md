####[If not](https://www.cnblogs.com/chenya/p/4218761.html)
代码中经常会有变量是否为None的判断，有三种主要的写法：

1. 第一种是`if x is None`；
2. 第二种是 `if not x：`；
3. 第三种是`if not x is None`（这句这样理解更清晰`if not (x is None)`） 。

`if x is not None`是最好的写法，清晰，不会出现错误，以后坚持使用这种写法。

使用if not x这种写法的前提是：必须清楚x等于None,  False, 空字符串"", 0, 空列表[], 空字典{}, 空元组()时对你的判断没有影响才行。




 