# List接口

## 基本介绍

1.   List接口是Collection接口的子接口
2.   List集合类中的元素**有序**（添加顺序和取出顺序一致），而且**可以重复**
3.   List集合类的每个元素都有对应的顺序索引，索引从0开始

### 示例

```Java
List list = new ArrayList();
list.add("Java");
list.add("C");
list.add("C++");
System.out.println("list = " + list); //输出list = [Java, C, C++]
System.out.println(list.get(0)); //输出Java
```

## 常用方法

### add

`add(int index, Object obj)` : 在索引为index的位置插入obj元素

```Java
List list = new ArrayList();
list.add("C Primer Plus");
list.add("Head First Java");
list.add(1, "Thinking in Java");
System.out.println(list); //输出list = [C Primer Plus, Thinking in Java, Head First Java]
```

### addAll

`addAll(int index, Collection c)` : 在索引为index的位置插入多个元素

```Java
List list2 = new ArrayList();
list2.add("Effective C++");
list2.add("Effective Java");
list.add(1, list2);
System.out.println(list); 
//输出[C Primer Plus, Effective C++, Effective Java, Thinking in Java, Head First Java]
```

### indexOf

`indexOf(Object obj)` : 返回元素在集合中第一次出现的索引

```Java
System.out.println(list.indexOf("C Primer Plus")); //输出0
```

### lastIndexOf

`lastIndexOf(Object obj)` : 返回元素在集合中最有一次出现的索引

```Java
list.add("C Primer Plus");
System.out.println(list);
//输出[C Primer Plus, Effective C++, Effective Java, Thinking in Java, Head First Java, C Primer Plus]
System.out.println(list.lastIndexOf("C Primer Plus")); //输出5
```

### remove

`remove(int index)` : 删除索引为index的元素

```Java
list.remove(0);
System.out.println(list);
//输出[Effective C++, Effective Java, Thinking in Java, Head First Java, C Primer Plus]
```

### set

`set(int index, Object obj)` : 将索引为index的元素替换为obj

```Java
list.set(0, "TCPL");
System.out.println(list);
//输出[TCPL, Effective Java, Thinking in Java, Head First Java, C Primer Plus]
```

### subList

`subList(int m, int n)` : 返回从索引为m到n-1位置的子集合，即[m, n-1] 或 [m, n)

```Java
List returnList = list.subList(0,3);
System.out.println(returnList); //输出[TCPL, Effective Java, Thinking in Java]
```