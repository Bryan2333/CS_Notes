# StringBuilder类

## 基本介绍

1.   一个可变的字符序列。该类提供一个与StringBuffer兼容的API，但不保证同步（StringBuilder不是线程安全的）
2.   该类被设计为StringBuffer的简易替代，用在字符串缓冲区被单个线程使用的时候

## 特点

1.   实现了Serializable，说明StringBuilder对象是可以串行化的
2.   StringBuilder是final类，不可以被继承
3.   String Builder对象的字符序列依然是放在父类AbstractStringBuilder的 `char[] value` ，因此字符序列是放在堆内存中

## 比较

1.   StringBuilder和StringBuffer非常类似，**都是可变字符序列**，而且**方法兼容**
     1.   StringBuffer：效率较高，线程安全
     2.   StringBuilder：效率最高，线程不安全
2.   String：**不可变字符序列**，效率低，但复用率高
3.   效率：StringBuilder > StringBuffer > String
4.   如果要对字符串做大量修改，不要用String类

## 使用场景

1.   如果字符串存在大量的修改操作，用StringBuffer或StringBuilder
     1.   单线程情况用StringBuilder
     2.   多线程情况用StringBuffer
2.   如果字符串很少有修改操作，且被多个对象引用，用String类