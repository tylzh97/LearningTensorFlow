# Pandas基本介绍

## pandas介绍

## pandas安装
- pip安装
  ```bash
  >> sudo pip install pandas
  ```

## 加载pandas
```python3
import pandas as pd
```

## 初始化数据
1. 创建串
   ```python3
   s = pd.Series( [1, 2, 3, 4, 5] )
   ```
2. 创建时间串
   ```python3
   dates = pd.date_range('20190307', periods=7)
   ```
3. 创建数据帧
   ```python3
   # index  表示行名称
   # columns表示列名称
   df = pd.DataFrame([[1,2], [3, 4]], index=['a', 'b'], columns=['X', 'Y'])
   print(df)
   """ output:
       X  Y
    a  1  2
    b  3  4
   """
   ```
   若在初始化时不带index与columns选项,则默认为自然数标号
4. 通过Python字典,创建数据帧
   ```python3
   # 要求字典中的value均为标量,或等维向量
   dic = {'a': [1, 2, 3, 4], 'b': [5, 6, 7, 8]}
   df = pd.DataFrame(dic)
   print(df)
   """ output:
       a  b
    0  1  5
    1  2  6
    2  3  7
    3  4  8
   """
   # 或字典中的value仅包含标量,则需要指定index名称
   dic = {1:'a', 2:'b', 3:'c'}
   df = pd.DataFrame(dic, index=[1])
   """ output:
       1  2  3
    1  a  b  c
   """
   ```
   若字典中均为标量且没有传入index关键字,则会抛出`ValueError: If using all scalar values, you must pass an index`异常

## pandas对象常用属性
1. 获取数据帧每列对象属性
   ```python3
   df.dtypes
   ```
2. 获取数据帧的每行的行号与列号
   ```python3
   # 获取行号
   df.index
   # 获取列号
   df.columns
   ```
3. 获取数据帧的值
   ```python3
   # 按行获取数据,输出numpy.ndarray类型数据
   df.values
   ```
4. 获取数据帧的统计学情况
   ```python3
   # 总和/均值/标准差/最小值/最大值
   df.describe()
   """ output:
            a         b
    count  4.0  4.000000
    mean   1.0  6.500000
    std    0.0  1.290994
    min    1.0  5.000000
    25%    1.0  5.750000
    50%    1.0  6.500000
    75%    1.0  7.250000
    max    1.0  8.000000
   """
   ```