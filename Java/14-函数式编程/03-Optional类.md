# Optional类

## 基本介绍

在Java8中引入了`Optional`类，可以更加优雅的地处理空指针异常

## 使用

### 创建对象

`ofNullable`: **Optional类的静态方法**。我们一般使用该方法将对象封装成一个Optional类对象。不管数据属否为null，都不会出现问题。

```
Author author = getAuthor();
Optional<Author> authorOption = Optional.ofNullable(author);
```

`of`: **Optional类的静态方法**。**如果一个对象确定不是空的**，则可以使用该方法将对象封装成Optional类对象，否则会抛出空指针异常。

`empty`: **Optional类的静态方法**。可以将null值封装成一个Optional类对象

### 安全消费值

我们可以使用Optional类的方法`ifPresent`方法来消费其中的对象

```
Optional<Author> author = getAuthor();
author.ifPresent(authorOption -> System.out.println(authorOption.getName() + ":" + authorOption.getAge()));
```

### 获取值

我们可以使用Optional类的`get`方法来获取被封装的对象，但是如果对象为null，则会抛出`NoSuchElementException`。**因此不建议使用该方法。**

### 安全获取值

#### orElseGet

我们可以使用Optional类的`orElseGet`方法来获取被封装的对象，并设置对象为空时返回的默认值。

```
Author author1 = author.orElseGet(() -> new Author());
System.out.println(author1.getName());
```

#### orElseThrow

我们可以使用Optional类的`orElseThrow`方法来获取被封装的对象，并设置对象为空时要抛出的异常

```
Optional<Author> author = Optional.ofNullable(null);
Author author1 = author.orElseThrow(() -> new RuntimeException("对象为空"));
System.out.println(author1.getName());
```

### 过滤

我们可以使用Optional类的`filter`方法对被封装的对象进行过滤，如果对象不符合条件，则会返回一个空对象的Optional对象

```
author.filter(author1 -> author1.getAge() > 50).ifPresent(author1 -> System.out.println(author1.getName()));
```

### 数据转换

我们可以使用Optional类的`map`方法对数据进行转换，转换后的数据依然被Optional类对象封装着

```
Optional<Author> author = getAuthor();
author.map(author1 -> author1.getBooks()).ifPresent(books -> System.out.println(books));
```
