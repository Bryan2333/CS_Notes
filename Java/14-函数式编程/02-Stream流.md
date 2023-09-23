# Stream流

## 介绍

Stream流可以用来对集合和数组进行链状流式操作

## 快速入门

```java
List<Author> authors = getAuthors();
authors.stream() // 把集合转换为stream流
       .distinct() // 去重
       .filter(author -> author.getAge() < 18) // 筛选出年龄小于18岁的作家
       .forEach(author -> System.out.println(author.getName())); // 将作家的名字打印输出
```

## 常用操作

### 创建流对象

#### 单列集合

创建方法：`集合对象.stream()`

```java
List<Integer> nums = new ArrayList<>();
nums.stream();
```

#### 数组

创建方法：`Arrays.stream(数组名)` 或 `Stream.of(数组名)`

```java
Integer[] arr = {1, 2, 3, 4};
Stream<Integer> stream = Arrays.stream(arr);
```

或者

```java
Integer[] arr = {1, 2, 3, 4};
Stream<Integer> stream = Stream.of(arr);
```

#### 双列集合

将双列集合转换为单列集合

```java
Map<String, Integer> map = new HashMap<>();
map.put("张三", 24);
map.put("李四", 27);
map.put("王五", 30);

Set<Map.Entry<String, Integer>> entries = map.entrySet();
Stream<Map.Entry<String, Integer>> stream = entries.stream();
```

### 中间操作

#### filter

可以对流当中的元素进行筛选，符合条件的元素才可保留在流当中

#### map

该方法用于将流中的每个元素按照指定的映射函数进行转换，然后返回一个新的流，新流中的元素类型与映射函数的返回类型相同。

```java
List<Author> authors = getAuthors();
authors.stream()
        // 只对作家的姓名进行操作
        .map(author -> author.getName())
        .forEach(s -> System.out.println(s));
```

#### distinct

可以去除流中重复的元素，但是该方法默认依赖Object类的equals方法，因此需要重写类中equals方法

#### sorted

可以对流中的元素进行排序

注意：
1. 如果调用无参数的`sorted`方法，则流中的元素对应的类型需要实现`Comparable`接口

#### limit

可以限制流的最大长度(元素个数)，超出的部分将会被抛弃

#### skip

可以跳过流中的前n个元素，返回剩下的元素

#### flatMap

`flatMap` 方法用于将流中的每个元素按照指定的映射函数进行转换，但与`map`不同的是，映射函数的返回值是一个流（Stream），然后`flatMap`方法会将这些流合并成一个新的流。

### 终结操作

#### forEach

对流中的元素进行遍历操作

#### count

可以用来获取当前流中元素的个数，需要使用变量接收返回值

#### max & min

可以用来获取流中的最值

```java
Optional<Integer> max = authors.stream()
        .flatMap(author -> author.getBooks().stream())
        .distinct()
        .map(book -> book.getScore())
        .max((score1, score2) -> score1 - score2); // 按升序规则
```

#### collect

将当前的流转换成一个集合

**转换成List集合**

```java
List<String> nameList = authors.stream()
        .map(author -> author.getName())
        .collect(Collectors.toList());
```

**转换成Set集合**

```java
Set<Book> bookName = authors.stream()
        .flatMap(author -> author.getBooks().stream())
        .collect(Collectors.toSet());
```

**转换成Map集合**

```java
Map<String, List<Book>> map = authors.stream()
        .distinct()
        .collect(Collectors.toMap(author -> author.getName(), author -> author.getBooks()));
```

#### 查找和匹配

`anyMatch` : 用来判断流中是否存在任何符合条件的元素，返回值是Boolean类型

```java
Boolean res = authors.stream()
                     .anyMatch(author -> author.getAge() > 29);
```

`allMatch`: 用来判断流中的所有元素是否都符合条件，返回值是Boolean类型

```java
Boolean res = authors.stream()
                     .allMatch(author -> author.getAge() > 18);
```

`findAny`: 用来获取流中的任意一个元素

`findFirst`: 用来获取流中的第一个元素

#### reduce

`reduce`归并: 它用于将流中的元素**通过指定的二元操作符（BinaryOperator）进行聚合，最终得到一个单一的结果**。reduce方法的主要作用是将流中的元素合并、计算或者组合成一个最终的值。

```java
// 求作家年龄的最大值
Integer maxAge = authors.stream()
        .distinct()
        .map(author -> author.getAge())
        .reduce(Integer.MIN_VALUE, (result, element) ->
                element > result ? element : result
        );
```

## 注意事项

1. 惰性求值，即如果没有终结操作，中间操作是不会被执行的
2. 流是一次性的，即一个流对象一旦经过一个终结操作就不可以再被使用
3. 流是不会影响原数据的
