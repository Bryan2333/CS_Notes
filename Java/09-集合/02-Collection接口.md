# Collection接口

## 特点

`public interface Collection<E> extends Iterable<E>`

1.   实现Collection接口的子类可以存放多个元素，每个元素可以是Object
2.   Collection的实现类，有些可以存放重复的数据，有些则不可以
3.   Collection的实现类，有些是有序的，有些则是无序的
4.   Collection接口没有直接的实现类，都是通过他的子接口Set和List来实现的

## 常用方法

### add

添加单个元素

```Java
List list = new ArrayList();
list.add("Hello");
list.add(19);
list.add(true);
System.out.println("list = " + list); //输出list = [Hello, 19, true]
```

### del

可以通过指定对象来删除，也可以通过索引来删除

```Java
list.remove("Hello"); //等同于list.remove(0);
System.out.println("list = " + list); //输出list = [19, true]
```

### contains

查找集合中是否存在某个元素，返回布尔值

```Java
System.out.println(list.contains("Hello")); //输出false
```

### size

获取集合中元素的个数

```Java
System.out.println(list.size()); //输出2
```

### isEmpty

判断集合是否为空，返回布尔值

```java
System.out.println(list.isEmpty()); //输出false
```

### clear

清空集合

```Java
list.clear();
System.out.println("list = " + list); //输出list = []
```

### addAll

添加多个元素（参数为集合）

```Java
List list2 = new ArrayList();
list2.add("Thinking in Java");
list2.add("Core Java");
list.addAll(list2);
System.out.println("list = " + list); //输出list = [Thinking in Java, Core Java]
```

### containsAll

查找多个元素是否存在（参数为集合），返回布尔值

```Java
System.out.println(list.containsAll(list2)); //输出true
```

### removeAll

删除多个元素（参数为集合）

```Java
list.removeAll(list2);
list.add("Effective Java");
System.out.println("list = " + list); //输出list = [Effective Java]
```

## 遍历集合

### 迭代器

1.   Iterator对象又称迭代器，主要用于遍历Collection集合中的元素
2.   **所有实现了Collection接口的集合类都有一个iterator()方法**，用于返回一个实现了Iterator接口的对象，**即返回一个迭代器**
3.   Iterator仅用于遍历数组，对象本身不存放数据

#### 原理

迭代器有两个方法 `hashNext()` 和 `next()`

1.   `hashNext()`：用于判断是否还有下一个元素
2.   `next()`：指针下移，将下移后集合位置上的元素返回

#### 使用细节

1.   **调用next()方法之前必须调用hashNext()方法来检查是否还存在下一个元素，否则有可能会抛出NoSuchElementException异常**
2.   当退出while循环后，迭代器会指向最后集合中最后一个元素。**如果希望再次遍历集合，则需要重置迭代器**

#### 示例

```Java
public class Main {
    public static void main(String[] args) {
        Collection list = new ArrayList();
        list.add(new Book("Core Java", 100));
        list.add(new Book("Effective Java", 150));
        list.add(new Book("Thinking in Java", 200));

        Iterator iterator = list.iterator();
        while (iterator.hasNext()) {
            Object next = iterator.next();
            System.out.println(next);
        }

        iterator = list.iterator(); //重置迭代器
        System.out.println("====再次遍历集合====");
        while (iterator.hasNext()) {
            Object next = iterator.next();
            System.out.println(next);
        }
    }
}

class Book {
    private String name;
    private double price;

    public Book(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public String toString() {
        return String.format("书名：%s，价格：%.2f", name, price);
    }
}
```

### 增强for循环

1.   增强for循环就是简化版的iterator，**只能用于遍历集合或数组**
2.   **增强for循环的底层依然是迭代器**

#### 基本语法

```Java
for (元素类型 元素名 : 集合名或数组名) {
    //访问元素
}
```

#### 示例

```Java
public class EnhancedFor {
    @SuppressWarnings("all")
    public static void main(String[] args) {
        Collection list = new ArrayList();
        list.add(new Book("Core Java", 100));
        list.add(new Book("Effective Java", 150));
        list.add(new Book("Thinking in Java", 200));

        System.out.println("====增强for循环遍历集合====");
        for (Object book : list) {
            System.out.println(book);
        }
        
        System.out.println("====增强for循环遍历数组====");
        int[] intArr = {1, 3, 5, 7, 9};
        for (int i : intArr) {
            System.out.println(i);
        }
    }
}
```
