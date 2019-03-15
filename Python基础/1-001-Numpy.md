# Numpy基本介绍

## 加载numpy
```python3
import numpy as np
```

## 创建矩阵
1. 普通创建
    ```python3
    array = np.array([[1, 2, 3], [2, 3, 4]])
    ```
2. 带类型创建
   ```python3
   # 创建整形矩阵
   array = np.array([1, 2, 3], dtype=np.int)
   # 查看矩阵数据类型
   array.dtype
   ```
3. 其他数据类型
   ```python3
   int32
   int64
   float16
   float32
   float64
   ```
4. 创建空矩阵
   ```python3
   # 创建一个2*3的空矩阵
   array = np.empty( shape=(2,3) )
   ```
5. 创建赋值矩阵
   ```python3
   # 创建一个2*3的零矩阵
   array = np.zeros( shape=(2, 3) )
   # 创建一个2*3的一矩阵
   array = np.ones( shape=(2,3) )
   ```
6. 创建随机矩阵
   ```python3
   # 矩阵中的每一个元素均为0~1的浮点型数字
   array = np.random.random( (3,4) )
   ```
## 向量创建
1. 创建有序向量
   ```python3
   array = np.arange(1, 10)
   ```
2. 生成等长线段向量
   ```python3
   array = np.linspace(0, 15, 5)
   # output:
   # >> array([ 0.  ,  3.75,  7.5 , 11.25, 15.  ]) 
   ```


## array常用成员
1. 获取矩阵宽度
   ```python3
   ayyar.ndim
   ```
2. 获取矩阵形状(高, 宽)
   ```python3
   ayyar.shape
   ```
3. 获取矩阵大小
   ```python3
   ayyar.size
   ```

## array常用方法
1. 重塑矩阵形状
   ```python3
   array = np.arange(12)
   re = array.reshape( (3. 4) )
   ```
   注意，reshape()后的size必须与原矩阵size相同，否则会抛出`ValueError`异常
2. 矩阵求和
   ```python3
   # 整个矩阵的和
   np.sum(array)
   # axis = 0 -> 按列
   # axis = 1 -> 按行
   # axis参数在max/min等方法中也适用
   np.sum(array, axis = 1)
   ```
3. 求矩阵中的最小
   ```python3
   np.min(array)
   ```
4. 求矩阵中的最大
   ```python3
   np.max(array)
   ```
5. 获取最小值、最大值的的索引
   ```python3
   array = np.arange(1, 13)
   array = array.reshape( (3, 4) )
   # 获取最小值索引
   min_p = np.argmin(array)
   # 获取最大值索引
   max_p = np.argmax(array)
   ```
   获取的最大最小值并非其在矩阵中的位置,而是其一维索引位置.
6. 计算矩阵均值
   ```python3
   # 类方法
   np.mean(array)
   np.average(array)
   # 对象方法
   array.mean()
   ```
7. 获取矩阵中位数
   ```python3
   np.median(array)
   ```
8. 获取累计向量
   ```python3
   np.cumsun(array)
   ```
   该方法仅能获取一维向量
9. 计算矩阵差
    ```python3
    np.diff(array)
    ```
    该方法会改变矩阵的形状.例如:输入3*4的矩阵,只会输出3*3的矩阵.
10. 获取非零值
    ```python3
    np.nonzero(array)
    ```
    该方法分别输出非0值的行数与列数,输出到两个矩阵中.
11. 排序
    ```python3
    # 按行升序
    array.sort()
    # 按列升序
    array.sort(axis=0)
    ```
12. 边界约束(截取)
    ```python3
    # 将矩阵中小于0的元素约束成0;大于255的元素约束成255
    np.clip(array, 0, 255)
    ```
    该方法运用在数据约束中,例如对于图像数据,所有的数值均应该在0~255之间.对于不合规的数据,我们能够使用该方法进行数据的约束.
13. 展开矩阵为向量
    ```python3
    array = np.array([[1, 2, 3], [2, 3, 4]])
    print(array.flatten())
    # output:
    # [1, 2, 3, 2, 3, 4]
    ```


---
# Numpy运算

## 元素运算
1. 加法、减法运算
   ```python3
   a = np.array([1, 2, 3])
   b = np.array([2, 1, 4])
   # 两个矩阵中对应元素减法运算
   sub = a - b
   # 两个矩阵中对应元素加法运算
   add = a + b
   ```
2. 乘法、除法运算
   ```python3
   a = np.array([1,2,3,4])
   b = np.array([2,2,2,2])
   # 对应元素乘法运算
   mul = a * b
   # 对应元素除法运算
   div = a / bv
   ```
3. 简单函数运算
   ```python3
   a = np.array([1, 2, 3])
   # 对每个元素进行sin运算
   # 类似的,有cos,tan等运算
   sin = np.sin(a)
   ```
4. 比较运算符
   ```python3
   a = np.array([1, 2, 3, 4, 5, 6, 7])
   # 判断比4小的元素
   a<4
   # output: array([ True,  True,  True, False, False, False, False])
   # 类似的,有<, <=, >, >=, ==等运算
   ```

## 矩阵运算
1. 矩阵点乘
   ```python3
   a = np.array( [[1, 1], 
                  [0, 1]] )
   b = np.array( [[1, 2], 
                  [3, 4]] )
   dmul = np.dot(a, b)
   # output:
            array([[4, 6],
                   [3, 4]])
   # 同样,a·b运算有等价写法
   dmul2 = a.dot(b)
   ```
2. 矩阵转置
   ```python3
   np.transpose(array)
   # 有等价写法
   array.T
   ```

## 矩阵索引
1. 常规索引方法
   ```python3
   array[0]
   array[0][1]
   ```
   与python类似,使用中括号[]直接进行索引
2. 等价索引方法
   ```python3
   array[0][1]
   # or 
   array[0, 1]
   ```
3. 矩阵分片
   ```python3
   # 与python中的list分片类似,采用:语法
   # 冒号左侧为闭,右侧为开
   array[1:3]
   array[1][1:3]
   array[1, 1:3]
   ```
4. 矩阵遍历
   ```python3
   # 按行遍历
   for row in array:
        print(row)
   # 按列便利
   # 把矩阵转置后遍历行
   for col in array.T:
        print(col)
   ```
5. 元素遍历
   ```python3
   # 先将矩阵展开,然后再遍历
   # array.flat 返回一个迭代器
   for item in array.flat:
        print(item)
   ```
6. 矩阵合并
   ```python3
   # 垂直合并
   # vertical stack
   np.vstack( (array1, ayyar2) )
   # 水平合并
   # horizontal stack
   np.hstack( (array1, array2) )
   # 指定维度合并
   np.concatenate( (array1, array2), axis=1 )
   ```
7. 向量转置
   <br>特别注意,对于一维向量而言,array.T并不会转置矩阵,因为其本质上仅有一个维度;而array.T操作实际上为reshape操作,单维度不能发生变化.
   <br>我们需要对向量进行升维操作后,才能进行转置操作
   ```python3
   array = np.array([1,2,3,4])
   # np.newaxis: 创建新维度
   print(array[:, np.newaxis])
   # output:
   """
   array([  [1],
            [2],
            [3],
            [4] ] )
   """
   # 更好的,我们能够矩阵的shape参数进行赋值
   arrap.shape = (4, 1)
   ```

## 矩阵分割
1. 等距分割
   ```python3
   # 将矩阵array横向等距分成2块
   np.split(array, 2, axis=1)
   # 垂直分割
   # 垂直分割成等距两块
   np.vsplit(array, 2)
   # 水平分割
   # 水平分割成等距两块
   np.hsplit(array, 2)
   ```
   注意:使用此方法时,若不能等距分割,则会抛出一个`ValueError`异常!
2. 不等距分割
   ```python3
   # 将矩阵array横向分割成3块,若不能等距分割,则除第一块外其余块等距.
   np.array_split(array, 3, axis=1)
   ```
   注意:使用此方法分割后的结果首块最大!

## 矩阵的赋值
1. '='号赋值
   <br>传递引用,即仅传递了对象指针,赋值后id相同
2. copy方法
   <br>深度拷贝,赋值后id不同