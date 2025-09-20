# PowerMockito 使用

参考文档: https://www.jianshu.com/p/6631bd826677

## PowerMockito 原理简单介绍

powermock 有两个重要的依赖：javassist 和 objenesis，javassist 是一个修改 java 字节码的工具包，objenesis 是一个绕过构造方法来实例化一个对象的工具包。由此看来，PowerMock 的本质是通过修改字节码来实现对静态和 final 等方法的 mock 的。

## 普通 Mock：Mock 参数传递的对象

**测试目标代码：**

```java
public class CommonExample {
    public boolean callArgumentInstance(File file) {
        return file.exists();
    }
}
```

**测试用例代码：**

```java
public class CommonExampleTest {
    @Test
    public void testCallArgumentInstance() {
        File file = PowerMockito.mock(File.class);
        CommonExample commonExample = new CommonExample();
        PowerMockito.when(file.exists()).thenReturn(true);
        Assert.assertTrue(commonExample.callArgumentInstance(file));
    }
}
```

普通 Mock 不需要加@RunWith 和@PrepareForTest 注解，在这种情况下，使用 Mockito 也是可以实现的。上述步骤如下：

1. 通过`PowerMockito.mock(File.class)`创建出一个 mock 对象；
2. 然后再通过`PowerMockito.when(file.exists()).thenReturn(true);`来指定这个 mock 对象具体的行为；
3. 再将 mock 对象作为参数传递个测试方法，执行测试方法。

## Mock 方法内部 new 出来的对象

**测试目标代码：**

```java
public class CommonExample {
    public boolean callArgumentInstance(String path) {
        File file = new File(path);
        return file.exists();
    }
}
```

**测试用例代码：**

```java
public class CommonExampleTest extends BasePowerMockTestCase {

    @Test
    @PrepareForTest(CommonExample.class)
    public void callCallArgumentInstance2() throws Exception {
        File file = PowerMockito.mock(File.class);
        CommonExample commonExample = new CommonExample();
        PowerMockito.whenNew(File.class).withArguments("aaa").thenReturn(file);
        PowerMockito.when(file.exists()).thenReturn(true);
        Assert.assertTrue(commonExample.callArgumentInstance("aaa"));
        File newFile = Mockito.mock(File.class);
        newFile.exists();
        Mockito.verify(newFile).exists();
    }
}
```

当使用`PowerMockito.whenNew().thenReturn()`方法时，必须加上注解`@PrepareForTest`和`@RunWith`，注解@PrepareForTest 里写的类是需要 mock 的 new 对象代码所在的类。需要 mock 的对象是在方法内部 new 出来的，这是一种比较常见的 mock 方式。 步骤（已经讲过的步骤省略）：

1. 通过`PowerMockito.whenNew(File.class).withArguments("aaa").thenReturn(file);`来指定当以参数为`"aaa"`创建 File 对象的时候，返回已经 mock 的 File 对象。
2. 在测试方法之上加注解`@PrepareForTest(CommonExample.class)`，注解里写的类是需要 mock 的 new 对象代码所在的类。
