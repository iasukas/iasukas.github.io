---
title: "Python inspect模块详解"
description:
author: iasukas
date: 2024-02-10 11:13:16 -0000
categories: [Python]
tags: [Python]
---

在本教程中，我们将学习Python的inspect模块及其功能。It模块用于检查代码中的对象。正如我们所知，Python作为一种面向对象的语言运行，我们的代码围绕这些对象运行，检查模块对于识别特定的模块或对象变得很有价值。事实证明，它对于检查特定的函数调用或跟踪特别有用，这反过来又有助于更顺利的调试过程。

inspect模块提供了一系列方法，可以分为两大类：用于确认令牌类型的方法和用于获取令牌源的方法。

## 验证令牌类型的方法

下面是验证令牌类型的方法-

isclass（）：如果对象是类，则此方法返回True值;否则，它返回False。当与getmembers（）函数结合使用时，它同时显示类及其类型。此方法用于检查活动类。

**举例来说─**

```
import inspect  
  
class MyClass:  
    pass  
def my_function():  
    pass  
  
result_class = inspect.isclass(MyClass)  
result_function = inspect.isclass(my_function)  
  
print("Is MyClass a class - ", result_class)  
print("Is my_function a class - ", result_function)  
```

**输出：**

```
Is MyClass a class - True
Is my_function a class -  False
```

在本例中，isclass（）方法用于检查MyClass和my_function对象是否为类。MyClass的结果为True（因为它是一个类），my_function的结果为False（因为它不是一个类）。

ismodule（）：如果提供的参数是一个已导入的模块，则此函数给出True响应。

**举例来说─**

```
import inspect  
import math  
result_math = inspect.ismodule(math)  
result_str = inspect.ismodule("hello")  
  
print("Is math a module - ", result_math)  
print("Is 'hello' a module - ", result_str)  
```

**输出：**

```
Is math a module - True
Is 'hello' a module - False
```

isfunction（）-如果提供的参数是内置函数名，则此方法返回True结果。

**举例来说─**

```
import inspect  
  
def my_function():  
    pass  
  
result_my_function = inspect.isfunction(my_function)  
result_print = inspect.isfunction(print)  
  
print("Is my_function a function - ", result_my_function)  
print("Is print a function - ", result_print)  
```

**输出：**

```
Is my_function a function - True
Is print a function - True
```

ismethod（）-此函数用于确定所提供的参数是否与方法的名称相对应。

**举例来说─**

```
import inspect  
class MyClass:  
    def my_method(self):  
        pass  
  
obj = MyClass()  
result_method = inspect.ismethod(obj.my_method)  
result_function = inspect.ismethod(my_function)  
  
print("Is my_method a method -", result_method)  
print("Is my_function a method - ", result_function)  
```

**输出：**

```
Is my_method a method -  True
Is my_function a method -  False
```

getclasstree（）`函数用于获取和检查类的层次结构。它提供了一个元组，其中包括类本身及其父类。当与返回父类的getmro（）函数配对时，它有助于理解类的层次结构。

**举例来说─**

```
import inspect  
  
class A:  
    pass  
  
class B(A):  
    pass  
  
class C(B):  
    pass  
  
class D(C):  
    pass  
  
tree = inspect.getclasstree([D, B], unique=True)  
print(tree)  
```

**输出：**

```
[(<class '__main__.D'>, (<class '__main__.C'>,)), (<class '__main__.B'>, (<class '__main__.A'>,))]
```

