# String类

1.   String对象用于保存字符串，也就是一组字符序列
2.   字符转常量对象使用双引号括起来的字符序列
3.   字符串的字符用的是Unicode字符编码，不管是字母还是汉字都占用两个字节
4.   String类比较常用的构造器
     1.   `String s1 = new String();`
     2.   `String s2 = new String(String original)`
     3.   `String s3 = new String(char[] a)`
     4.   `String s4 = new String(char[] a, int startIndex, int count)`
5.   String类实现了如下接口：
     1.   Serializable：String对象可以串行化，即可以在网上传输
     2.   Comparable：String对象可以比较大小
6.   String对象有属性 `private final char[] value` 用处存储字符串内容，所以value不可以修改(value不可以指向新的地址)

## 创建对象

1.   直接赋值 `String str1 = "Hello, World!";`
2.   调用构造器 `String str2 = new String("Hello, World!");`

### 细节

1.   第一种方法会检查常量池里是否有 "Hello, World!" 的数据空间。如果有，则直接指向这个空间。如果没有，就先创建，再指向数据空间。**因此str1最终指向常量池的数据空间**
2.   第二种方式会在堆中创建一个空间，里面有 value 属性指向常量池的数据空间。如果常量池中已经有 "Hello, World!" 的数据空间，就直接指向过去；没有的话，就先创建再指向。**因此str2最终指向堆中的空间**

![StringJVM.jpg](https://s2.loli.net/2022/12/19/JdiUnySo39uzgkb.jpg)

3.   `str2.intern()` 方法会返回常量池的地址

## 特性

1.   **String是个final类，代表不可改变的字符序列**
2.   字符串是不可变的。一个字符串对象一旦被分配，其内容不可以改变
3.   `String a = "Hello"; String b = "abc"; String c = a + b;` 相当于 `StringBuilder sb = new StringBuilder(); sb.append(a); sb.append(b); String c = sb.toString()`
     1.   sb是在堆中，append是在原来字符串的基础上追加
     2.   如果是字符串常量相加，看常量池。变量相加是在堆中

## 常用方法

1.   equals：判断字符串内容是否相同
2.   equalsIgnoreCase：忽略大小写判断字符串内容是否相同
3.   length：获取字符个数，即字符串的长度
4.   indexOf：获取字符或字符串在字符串对象中第一次出现的下标，如果找不到就返回-1
5.   lastIndexOf：获取字符或字符串在字符串对象中最后一次出现的下标，如果找不到就返回-1
6.   substring()：截取指定范围的字符串
     -   substring(n) : 从下标为n的字符开始截取后面所有的内容
     -   substring(m, n) : 从下标为m的字符开始截取到下标为n-1的字符（不包括n），即**[m, n-1]**
7.   toUpperCase：将字符串转为大写
8.   toLowerCase：将字符串转为小写
9.   concat：拼接字符串
10.   replace：替换字符串的内容
11.   split：根据某些字符对字符串进行分割
12.   format格式字符串：%s 字符串、%c 字符、%d 整形、%f 浮点数

**示例**

```Java
public class Main {
    public static void main(String[] args) {
        
        String str1 = "Hello, World!";
        String str2 = "hello, world!";
        
        System.out.println(str1.equals(str2)); //false
        System.out.println(str1.equalsIgnoreCase(str2)); //true
        System.out.println(str1.length()); //输出13
        
        System.out.println(str1.indexOf('o')); //输出4
        System.out.println(str1.lastIndexOf('o')); //输出8
        
        System.out.println(str1.substring(7)); //输出 World!
        System.out.println(str1.substring(1, 8)); //输出ello, W
        
        System.out.println(str1.toUpperCase()); //输出HELLO, WORLD!
        System.out.println(str1.toLowerCase()); //输出hello, world!
        
        System.out.println(str1.concat(str2)); //输出Hello, World!hello, world!
        
        System.out.println(str1.replace("World", "Java")); //输出 Hello, Java!
        
        String str3 = "abc def ghi";
        String[] strArray = str3.split(" "); //根据空格分割字符串
        for (String i : strArray) { //每行分别输出abc def ghi
            System.out.println(i);
        }
        
        String str4 = String.format("%s %c %d %.2f", "Hello", 'a', 100, 0.5);
        System.out.println(str4); //输出：Hello a 100 0.50
    }
}
```
