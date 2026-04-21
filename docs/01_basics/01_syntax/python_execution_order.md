# Python代码执行顺序：函数为什么不会立即执行？

## 1. 问题描述

在阅读代码时发现：

```python
def test():
    print("hello")

print("start")

执行结果：

start

为什么 test() 没有执行？

2. 复现代码
def test():
    print("hello")

print("start")
3. 原因分析

Python执行分为两个阶段：

① 解析阶段（Definition Phase）
创建函数对象
绑定函数名
不执行函数体
② 运行阶段（Execution Phase）
从上到下执行代码
只有遇到函数调用才执行函数体
4. 解决方案
def test():
    print("hello")

print("start")
test()
5. 易错点
def test():
    print(x)

x = 10
test()

👉 可以正常执行（因为执行时 x 已定义）

6. 延伸（高级理解）
类定义会立即执行（类体）
装饰器在定义时执行
Python是解释执行但有“编译阶段（字节码）”