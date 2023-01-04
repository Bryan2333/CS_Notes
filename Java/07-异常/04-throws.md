# throws

## 基本介绍

-   如果一个方法中的语句执行时可能产生某种异常异常，但不能确定如何处理这种异常，则该方法显示地声明抛出异常，而异常则**由该方法调用者负责处理**
-   在方法声明中用throws语句可以声明抛出异常的列表，异常类型可以是方法中产生的异常类型，也可以是它的父类

## 使用细节

1.   对于编译时异常，**程序中必须处理**，可以用throws或try-cache来处理异常
2.   对于运行时异常，程序如果没有显示处理，则默认的处理方式就是throws
3.   子类重写父类方法时，子类所抛出的异常类型要么和父类抛出的异常类型一致，要么是父类抛出的异常类型的子类
4.   如果在throws的过程中有方法用try-catch处理异常，就不需要再throws

## 示例

```Java
public class Main {
    public static void main(String[] args) {
        m3(); //不会报错，对于运行时异常，默认的处理方式就是throws
    }
    
  	// 对于编译时异常，程序中必须处理，这里将异常抛出
    public static void m1() throws FileNotFoundException {
        FileInputStream fis = new FileInputStream("D://test");
    }
    
    public static void m2() {
        //这里用try-catch处理编译时异常
        try {
            m1();
        } catch (Exception e) {}
    }
    
    public static void m3() throws ArithmeticException {
        int num = 10 / 0;
    }
}

class Base {
    public void method1() throws RuntimeException {}
    public void method2() throws RuntimeException {}
}

class Sub extends Base {
    //抛出异常类型和父类抛出的异常类型相同
    public void method1() throws RuntimeException {}
    //抛出异常类型为父类抛出的异常类型的子类
    public void method2() throws NullPointerException {}
}
```



