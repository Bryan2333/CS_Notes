# StringBuffer类

## 基本介绍

1.   StringBuffer代表可变的字符序列，可以对字符串内容进行增删
2.   StringBuffer是一个容器
3.   StringBuffer的直接父类是AbstractStringBuilder，其父类有属性 `char[] value` (没有final修饰符)，该字符串数组用于存放字符串内容
4.   StringBuffer保存的是字符串变量，里面的值可以更改，而且不用每次更新地址，效率更高

## 构造器

1.   `StringBuffer()` : 构造一个不带字符串的字符缓冲区，其初始容量为16个字符
2.   `StringBuffer(int capacity)` : 通过构造器指定字符缓冲区的大小
3.   `StringBuffer(String str)` : 构造一个字符缓冲区，并将其内容初始化为指定的字符串内容

**示例**

```Java
public class Main {
    public static void main(String[] args) {
        StringBuffer stringBuffer1 = new StringBuffer(); //初始大小为16个字符
        
        StringBuffer stringBuffer2 = new StringBuffer(100); //大小为100个字符
        
        StringBuffer stringBuffer3 = new StringBuffer("Hello"); //大小为16+5 即21个字符串
    }
}
```

## 转换

### String转StringBuffer

1.   使用构造器
2.   使用 `append` 方法

**示例**

```Java
public class Main {
    public static void main(String[] args) {
        String str = "Hello, World!";
        
        //第一种方法
        StringBuffer stringBuffer1 = new StringBuffer(str);
        
        //第二种方法
        StringBuffer stringBuffer2 = new StringBuffer();
        stringBuffer2 = stringBuffer2.append(str);
    }
}
```

### StringBuffer转String

1.   使用 `toString` 方法
2.   使用构造器

**示例**

```Java
public class Main {
    public static void main(String[] args) {
        StringBuffer stringBuffer = new StringBuffer("Hello, World!");
        
        //第一种方法
        String str1 = stringBuffer.toString();
        
        //第二种方法
        String str2 = new String(stringBuffer);
    }
}
```

## 常用方法

### append

追加指定字符串到原字符串末尾

```Java
StringBuffer sb = new StringBuffer("Hello");
sb.append(" World!");
System.out.println(sb); //输出Hello World!
```

### delete(m, n)

删除下标为m到下标为n-1的字符，即删除[m, n-1]

```Java
StringBuffer sb = new StringBuffer("Hello,World!");
sb.delete(5, 11);
System.out.println(sb); //输出Hello!
```

### replace(m, n, str)

用str替换下标为m到下标为n-1的字符

```Java
StringBuffer sb = new StringBuffer("Hello, World!");
sb.replace(7, 12, "Java");
System.out.println(sb); //输出Hello, Java!
```

### indexOf(str)

查找子串在字符串中第一次出现的下标

```Java
StringBuffer sb = new StringBuffer("Java CPP Rust");
int index = sb.indexOf("CPP");
System.out.println(index); //输出5
```

### insert(n, str)

在下标为n的位置插入字符串str，原来下标为n的内容自动后移

```Java
StringBuffer sb = new StringBuffer("Hello!");
sb.insert(5, "Java");
System.out.println(sb); //输出HelloJava!
```

### length

获取字符缓冲区内字符串的长度

```Java
StringBuffer sb = new StringBuffer();
sb.append("Java");
System.out.println(sb.length()); //输出4
```

