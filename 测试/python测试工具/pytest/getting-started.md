---
title: 安装和入门
---

**英文原文链接**：https://docs.pytest.org/en/7.3.x/  
此翻译参考：
  * https://www.cnblogs.com/superhin/p/11677240.html
  * https://github.com/luizyao/pytest-chinese-doc

# 安装和入门
**Python支持版本**: Python 3.7+ or PyPy3  
**支持的平台**: Unix/Posix and Windows  
**PyPI包名**: [pytest](https://pypi.org/project/pytest/)   
**依赖项**: py,colorama (Windows)  
**PDF文档**: [download latest](https://buildmedia.readthedocs.org/media/pdf/pytest/latest/pytest.pdf)

`pytest`是一个使创建简单及可扩展性测试用例变得非常方便的框架。测试用例清晰、易读而无需大量的繁琐代码。只需要几分钟的时间，就可以对你的应用开始一个简单的单元测试或者复杂的功能测试。

## 安装`pytest`
在命令行执行以下命令：
```bash
pip install -U pytest
```

检查版本：
```bash
$ pytest --version
pytest 7.3.1
```

## 创建你的第一个测试用例
创建一个名为`test_sample.py`文件，包含一个被测函数和一个测试函数：

```python title="src/chapter-1/test_sample.py"
def func(x):
    return x + 1

def test_answer():
    assert func(3) == 5
```

现在开始执行这个测试用例：

```python
$ pytest src/chapter-1/test_sample.py
=========================== test session starts ============================
platform linux -- Python 3.x.y, pytest-7.x.y, pluggy-1.x.y
rootdir: /home/sweet/project
collected 1 item

test_sample.py F                                                     [100%]
================================= FAILURES =================================
_______________________________ test_answer ________________________________
    def test_answer():
>       assert inc(3) == 5
E       assert 4 == 5
E        +  where 4 = inc(3)

test_sample.py:6: AssertionError
========================= short test summary info ==========================
FAILED test_sample.py::test_answer - assert 4 == 5
============================ 1 failed in 0.12s =============================
```

这个`[100%]`指运行所有测试用例的总体进度。运行完成后，因`func(3)`不返`5`，pytest会显示一个失败报告。

:::tip 提示
在上面的例子中，我们直接使用`assert`来验证测试用例中的预期结果，这是因为 pytest 提供了高级的断言自省功能，可以智能的为我们展示失败处的中间信息（`where 4 = func(3)`），因此我们就无需使用`assertEqual`、`assertNotEqual`之类的方法。
:::

## 执行多个测试用例
`pytest`会执行当前及其子文件夹中，所有命名符合`test_*.py`或者`*_test.py`规则的文件中的所有的测试用例。

## 触发一个指定异常的断言
使用`raises`可以验证某些代码是否抛出一个指定的异常：

```python title="src/chapter-1/test_sysexit.py"
import pytest

def f():
    raise SystemExit(1)

def test_mytest():
    with pytest.raises(SystemExit):
        f()
```

执行这个测试用例时，加上`-q/--quiet`选项可以查看精简版的测试结果：

```bash
$ pytest -q test_sysexit.py
.                                                                    [100%]
1 passed in 0.12s
```

## 在一个类中组织多个测试用例
pytest 可以让你很容易的创建一个测试类来包含多个测试用例：

```python title="src/chapter-1/test_class.py"
class TestClass:
    def test_one(self):
        x = "this"
        assert "h" in x

    def test_two(self):
        x = "hello"
        assert hasattr(x, "check")
```

我们无需让测试类继承自任何基类，但是要确保类名的前缀为`Test`，否则将忽略其中的测试用例。通过传入文件路径就可以执行这个测试类：

```python
$ pytest -q test_class.py
.F                                                                   [100%]
================================= FAILURES =================================
____________________________ TestClass.test_two ____________________________

self = <test_class.TestClass object at 0xdeadbeef0001>

    def test_two(self):
        x = "hello"
>       assert hasattr(x, "check")
E       AssertionError: assert False
E        +  where False = hasattr('hello', 'check')

test_class.py:8: AssertionError
========================= short test summary info ==========================
FAILED test_class.py::TestClass::test_two - AssertionError: assert False
1 failed, 1 passed in 0.12s
```

从输出的结果中我们可以看到：

- `test_one`测试成功，用`.`表示；`test_two`测试失败，用`F`表示；
- 并且我们清楚的看到`test_two`失败处的中间值的信息：`where False = hasattr('hello', 'check')`

:::tip 提示
测试类要符合特定的规则，pytest 才能发现它：

* 测试类的命名要符合`Test*`规则；
* 测试类中不能有`__init__()`方法，否则 pytest 无法采集到其中的测试用例；
:::

在类中组织多个测试用例的好处体现以下几个方面：

- 结构化测试的组织；
- 仅在指定的类中共享`fixture`；
- 应用在类上的`marker`将隐式的应用于其中所有的测试用例上；

需要注意的一点是，测试类中的每个用例都拥有该类的唯一实例。这是因为如果让所有测试用例共享同一个类实例，将不利于测试的隔离。

```python title="src/chapter-1/test_class_demo.py"
class TestClassDemoInstance:
    def test_one(self):
        assert 0

    def test_two(self):
        assert 0
```

```python
$ pytest -q src/chapter-1/test_class_demo.py
FF                                                                             [100%]
====================================== FAILURES ======================================
___________________________ TestClassDemoInstance.test_one ___________________________

self = <test_class_demo.TestClassDemoInstance object at 0x000001BE2B380640>>

    def test_one(self):
>       assert 0
E       assert 0

src/chapter-1/test_class_demo.py:3: AssertionError
___________________________ TestClassDemoInstance.test_two ___________________________

self = <test_class_demo.TestClassDemoInstance object at 0x000001BE2B380760>>

    def test_two(self):
>       assert 0
E       assert 0

src/chapter-1/test_class_demo.py:6: AssertionError
============================== short test summary info ===============================
FAILED src/chapter-1/test_class_demo.py::TestClassDemoInstance::test_one - assert 0
FAILED src/chapter-1/test_class_demo.py::TestClassDemoInstance::test_two - assert 0
2 failed in 0.05s
```

可以看到，这个例子中的两个测试用例拥有不同的类实例：`0x000001BE2B380640`和`0x000001BE2B380760>`。

## 申请一个唯一的临时目录
pytest 提供一些内置的`fixtures`，用于请求一些系统的资源。例如，一个唯一的临时目录：

```python title="src/chapter-1/test_tmp_path.py"
def test_needsfiles(tmp_path):
    print(tmpdir)
    assert 0
```

在这个例子中，在形参的位子列出`tmp_path fixture`，`pytest` 会在每个用例执行之前创建一个唯一的临时目录。

现在，我们来执行这个测试用例：

```python
$ pytest -q test_tmp_path.py
F                                                                    [100%]
================================= FAILURES =================================
_____________________________ test_needsfiles ______________________________

tmp_path = PosixPath('PYTEST_TMPDIR/test_needsfiles0')

    def test_needsfiles(tmp_path):
        print(tmp_path)
>       assert 0
E       assert 0

test_tmp_path.py:3: AssertionError
--------------------------- Captured stdout call ---------------------------
PYTEST_TMPDIR/test_needsfiles0
========================= short test summary info ==========================
FAILED test_tmp_path.py::test_needsfiles - assert 0
1 failed in 0.12s
```

有关TMPDIR处理的更多信息，请访问[Temporary directories and files](https://docs.pytest.org/en/7.3.x/how-to/tmp_path.html#tmp-path-handling)。

可以使用如下命令查看所有可用的 fixtures，如果想同时查看以`_`开头的 fixtures，需要添加`-v`选项：

```bash
$ pytest -v --fixtures # shows builtin and custom fixtures
```
