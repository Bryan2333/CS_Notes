# Map接口

## 基本介绍

1.   Map 和 Collection接口并列存在，其实现类用于保存具有映射关系的数据：Key-Value
2.   Map 中的 Key 和 Value 可以是任意引用类型的数据
3.   **Map 中的 Key 不允许重复，但是 Value 可以重复**
4.   Key 可以为null，但只能有一个。Value 可以为null，且可以有多个
5.   **一般情况下用字符串作为 Key**
6.   Key 和 Value 存在单向一对一的关系，总能通过 Key 找到对应的 Value

## 常用方法

### put

添加或替换 K-V

```Java
Map map = new HashMap();
map.put("1", "Java");
map.put("2", "Scheme");
map.put("3", "Python");
System.out.println(map); //输出{1=Java, 2=Scheme, 3=Python}
map.put("1", "C"); //将1对应的value从Java替换为C
System.out.println(map); //输出{1=C, 2=Scheme, 3=Python}
```

### get

通过键获取对应的映射值

```java
System.out.println(map.get("2")); //输出Scheme
```

### remove

根据键删除映射关系

```java
map.remove("2"); //删除"2"的映射关系
System.out.println(map); //输出{1=C, 3=Python}
```

### size

获取元素的个数

```Java
System.out.println(map.size()); //输出2
```

### isEmpty

判断元素个数是否为0

```Java
System.out.println(map.isEmpty()); //输出false
```

### clear

删除所有元素

```Java
map.clear();
System.out.println(map); //输出{}
```

### containsKey

查找键是否存在

```Java
map.put("3", "Python");
System.out.println(map.containsKey("3")); //输出true
System.out.println(map.containsKey("4")); //输出false
```

## 遍历方式

### 第一种

先取出所有的 Key，再通过Key 取出对应的 Value

#### 增强for循环

```Java
Map map = new HashMap();
map.put("1", "C");
map.put("2", "C++");
map.put("3", "Java");
Set set = map.keySet();
for (Object o : set) {
    System.out.println(o + "-" + map.get(o));
}
```

#### 迭代器

```Java
Iterator iterator = set.iterator();
while (iterator.hasNext()) {
    Object next = iterator.next();
    System.out.println(next + "-" + map.get(next));
}
```

### 第二种

将所有 Value 取出来**（只有Value，没有Key）**

#### 增强for循环

```Java
Collection values = map.values();
for (Object value : values) {
    System.out.println(value);
}
```

#### 迭代器

```Java
iterator = values.iterator();
while (iterator.hasNext()) {
    Object next = iterator.next();
    System.out.println(next);
}
```

### 第三种

通过 EntrySet 中 Entry 的 getKey 和 getValue 方法

#### 增强for循环

```Java
Set set1 = map.entrySet();
for (Object entry : set1) {
    Map.Entry mapEntry = (Map.Entry) entry;
    System.out.println(mapEntry.getKey() + "-" + mapEntry.getValue());
}
```

#### 迭代器

```Java
iterator = set1.iterator();
while (iterator.hasNext()) {
    Object entry = iterator.next();
    Map.Entry mEntry = (Map.Entry) entry;
    System.out.println(mEntry.getKey() + "-" + mEntry.getValue());
}
```

