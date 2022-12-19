# HashMap

1.   HashMap 是Map接口中使用最多的实现类
2.   HashMap 没有线程同步，因此是**线程不安全的**

# HashTable

1.   **HashTable 的键和值都不能为空，否则会抛出空指针异常**
2.   HashTable 的使用方法和 HashMap基本上相同
3.   **HashTable 是线程安全的**，而HashMap是线程不安全的
4.   第一次扩容到大小11。从第二次扩容开始，每次扩容后的容量为 原理容量 * 2 + 1

### 比较

|           | 版本 | 线程安全 | 效率 | 允许null |
| :-------: | :--: | :------: | :--: | :------: |
|  HashMap  | 1.2  |  不安全  |  高  |   允许   |
| HashTable | 1.0  |   安全   |  低  |  不允许  |

# Properties

1.   Properties 继承自 HashTable并且实现类 Map接口，也是使用键值对形式来保存数据
2.   Properties 还可以从 .properties 文件中加载数据到 properties对象，进行读取和修改

### 常见方法

-   `load` ：加载配置文件的键值对到 Properties 对象
-   `list` ：将数据显示到指定设备
-   `getProperty(key)` ：根据键获得值
-   `setProperty(key, value)` ：设置键值对到 Properties 对象
-   `store` ：将 Properties 中的键值对存储到配置文件中
