# main方法

## 介绍

-   形式： `public static void main(String[] args) { } `
    -   Java虚拟机调用类的main方法，所以main方法必须由 `public` 来修饰
    -   Java虚拟机调用类的main方法时不需要创建对象，所以main方法必须是 `static`
    -   该方法接收String类型的数组参数，该数组保存执行时传递给所运行的类的参数

## 示例

-   示例代码

```Java
public class Main {
    public static void main(String[] args) {
        if (args != null) {
            for (int i = 0; i < args.length; i++) {
                System.out.printf("第%d个参数 = %s", (i + 1), args[i]);
            }
        }
    }
}
```

-   运行结果

![mainMethodDemo.png](https://s2.loli.net/2022/12/19/WcjrSGRChw8JUbv.png)