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
   div = a / b
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
2. TODO
