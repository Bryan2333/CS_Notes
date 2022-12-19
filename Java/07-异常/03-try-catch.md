# try-catch

## 基本介绍

-   Java提供try和catch块来处理[[02异常处理|异常]]。try块用于包含可能出错的代码，catch块则用于处理try块中出现的异常。
-   程序员可以根据实际情况，在一个代码中写多个try-catch

## 基本语法

```Java
try {
    //可疑代码
    //将异常生成对象传给catch块
} catch (异常) {
    //对异常的处理
}
```

## 使用细节

1.   如果发生了异常，则异常后面的代码块不会执行，直接进入catch块
2.   如果没有异常发生，则按顺序执行try块中的代码，不会进入catch块
3.   如果不管有没有异常发生，都希望执行某段代码块，则可以使用finally块
4.   可以有多个catch捕获不同的异常，进行区别处理。但要求**父类异常在后，子类异常在前**。如果发生了异常，只会匹配一个catch
5.   可以try-finally配合使用，这种用法相当于没有捕获异常，因此程序会在执行finally代码块用退出

### 示例

```Java
public class TryCatch01 {
    public static void f1() {
       	try {
            int num1 = 10;
            int num2 = 0;
            System.out.printf("%d / %d = %d", num1, num2, num1/num2); 
            //上面的代码出现异常，下面的代码不会执行，直接进入catch块
            System.out.println("num1 = %d, num2 = %d", num1, num2); 
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
    }
    
    public static void f2() {
        //该段代码不会发生异常，则按顺序进行，不会进入catch块
        try {
            int num1 = 10;
            int num2 = 2;
            System.out.printf("%d / %d = %d", num1, num2, num1/num2); 
            System.out.println("num1 = %d, num2 = %d", num1, num2); 
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
    }
    
    public static void f3() {
        try {
            Person p1 = new Person();
            p1 = null;
            System.out.println(p1.getName());
            
            int num1 = 10;
            int num2 = 0;
            int result = num1 / num2;
        } catch (NullPointerException e) { //以有多个catch捕获不同的异常，进行区别处理
            System.out.println(e.getMessage());
        } catch (ArithmeticException e) {
            System.out.println(e.getMessage());
        } catch (Exception e) { //父类在最后
            System.out.println(e.getMessage());
        }
    }
}

class Person {
    private String name = "Jack";
    
    public getName() {
        return name;
    }
}
```

