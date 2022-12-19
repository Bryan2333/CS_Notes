# Class 类

## 基本介绍

-   Class 也是类，因此也继承自 Object 类
-   Class 类对象不能通过 `new` 创建，只能由 JVM 创建
-   某个类的 Class 类对象，在内存中只有一个，因为类只加载一次
-   每个类的实例都会记录自己是由哪个 Class 实例创建的
-   通过 Class 对象可以完整地得到一个类的完整结构，通过一系列 API
-   Class 类对象存放在堆中

## 常用方法

`getClass()` : 获得运行类型

`getPackage().getName()` : 获得全报名

`getConstructor().newInstance()` : 通过反射创建实例

`getField(String str)` : 通过反射获得属性

`field.set(obj, value)` : 通过反射给字段对象赋值

```java
String classPath = "com.bryan.Car";
// <?> 表示不确定的 Java 类型
Class<?> cls = Class.forName(classPath);
System.out.println(cls); // 输出哪个类的 Class 对象
// 得到包名
System.out.println(cls.getPackage().getName());
// 得到全类名
System.out.println(cls.getName());
// 通过 cls 创建实例对象
Car car = (Car) cls.getConstructor().newInstance();
System.out.println(car);
// 通过反射获得属性 band
Field brand = cls.getField("brand");
brand.set(car, "奔驰"); //通过反射给字段对象赋值
System.out.println(brand.get(car));
// 通过反射获得所有字段
System.out.println("=====所有的字段=====");
Field[] fields = cls.getFields();
for (Field field : fields) {
    System.out.println(field.getName());
}
```

## 获取 Class 类对象的方式

1.   已知一个类的全类名，并且该类在类路径下，则可以通过 Class 类的静态方法 `forName()` 获取，可能抛出 `NoSuchClassException` 。使用场景：多用于配置文件，读取全类名，加载类

     ```java
     //1. Class.forName(String str)
     public void firstMethod() throws Exception {
         String classPath = "com.bryan.Cat";
         Class<?> aClass = Class.forName(classPath);
         System.out.println(aClass);
     }
     ```

2.   已知具体类，可以通过 `类.class` 获取，该方式最为安全可靠，程序最高。应用场景：多用于参数传递，比如通过反射机制获得对于的构造器对象

     ```java
     //2. 类名.class 文件
     public void secondMethod() throws Exception {
         Class<Cat> catClass = Cat.class;
         Constructor<Cat> declaredConstructor = catClass.getDeclaredConstructor();
         Cat cat = declaredConstructor.newInstance();
         System.out.println(cat);
         System.out.println(catClass);
     }
     ```

3.   已知某个类的实例，调用该实例的 `getClass` 方法可以获取 Class 对象。应用场景：通过创建好的对象，获取 Class 对象

     ```java
     @Test
     //3. 对象.getClass 有对象实例时可以使用
     public void thirdMethod() {
         Cat cat = new Cat();
         Class<? extends Cat> aClass = cat.getClass();
         System.out.println(aClass);
     }
     ```

4.   通过类加载器 ClassLoader 获得类对象

     ```java
     //4. 通过类加载器 ClassLoader 获得类的 Class 对象
     public void fourthMethod() throws Exception {
         Cat cat = new Cat();
         // 先得到 cat 类的类加载器
         ClassLoader classLoader = cat.getClass().getClassLoader();
         // 在通过类加载器获得 Class 类对象
         Class<?> aClass = classLoader.loadClass("com.bryan.Cat");
         System.out.println(aClass);
     }
     ```

5.   基本数据类型可以通过 `基本数据类型.class` 获取类对象

     ```java
     //5. 基本数据类型可以通过 基本数据类型.class 获得 Class 对象
     public void fifthMethod() {
         Class<Integer> integerClass = int.class;
         Class<Boolean> booleanClass = boolean.class;
         System.out.println(booleanClass);
         System.out.println(integerClass);
     }
     ```

6.   基本数据类型对应的包装类可以通过 `类名.TYPE` 获取类对象

     ```java
     //6. 基本数据类型的包装类可以通过 类型.TYPE 获得 Class 对象
     public void sixthMethod() {
         Class<Integer> type = Integer.TYPE;
         Class<Character> type1 = Character.TYPE;
         System.out.println(type1);
         System.out.println(type);
     }
     ```

     ### 拥有 Class 对象的类
     
     ```Java
     Class<String> cls1 = String.class; // 外部类
     Class<Serializable> cls2 = Serializable.class; // 接口
     Class<Integer[]> cls3 = Integer[].class; // 数组
     Class<Double[][]> cls4 = Double[][].class; // 二维数组
     Class<Deprecated> cls5 = Deprecated.class; // 注解
     Class<Thread.State> cls6 = Thread.State.class; // 枚举
     Class<Long> cls7 = long.class; // 基本数据类型
     Class<Void> cls8 = void.class; // void
     Class<Class> cls9 = Class.class; // Class 类
     ```

