# final 关键字

-   final 中文意思：最后的、最终的

## 使用场景

-   当不希望类被[[03-继承#^3d8e44|继承]]时，可以用 `final` 修饰类
-   当不希望父类的某个方法被子类[[04-方法重写#^982662|重写]]时，可以用 `final` 修饰该方法
-   当不希望类的某个属性被修改时，可以用 `final` 修饰该属性
-   当不希望某个局部变量被修改时，可以用 `final` 修饰该变量

## 示例

不希望类被继承

```Java
finall class A {
    
}

// 下面代码会报错
// class B extends A {
    
}
```

-   不希望父类的某个方法被子类重写时

```Java
class A {
    public final void printInfo() {
        System.out.println("A.printInfo()");
    }
}

class B extends A {
    // 下面的代码会报错
    /*public void printInfo() {
        System.out.println("B.printInfo()");
    }*/
}
```

-   不希望类的某个属性被修改时

```Java
class A {
    public final int n1 = 100; //再次给n1赋值会报错
}
```

-   不希望某个局部变量被修改时

```Java
class Main {
    public void printNum() {
        final double num = 0.5;
       	// num = 0.1; //该段代码会导致编译报错
        System.out.println("num = " + num);
    }
}
```

## 使用细节

-   被 `final` 修饰的属性一般称为常量，一般用 `XX_XX` 来命名

-   `final` 修饰的**普通属性**在使用前必须赋予初始值，可以在如下位置进行赋值：

    1.   定义时
    2.   在构造器中
    3.   在代码块中

    -   示例：![ConstantVariable.png](https://s2.loli.net/2022/12/19/RmKj13xJBiSVFHg.png)

-    `final` 修饰的[[01-静态成员#^0a7c6e|静态属性]]，则只能在如下位置赋初始值：

		- 定义时
		- 静态代码块中

-   `final` 修饰的类不能被继承，但可以被实例化
-   类中 `final` 修饰的方法不能被重写，但可以被子类继承
-   `final` 和 `static` 往往搭配使用，效率更高，而且不会导致类加载
