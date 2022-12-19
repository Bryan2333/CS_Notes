# Arrays类

Arrays类里面包含一系列用于管理或操作数组的静态方法

## 常用方法

### toString

以字符串形式显示数组元素

```Java
Integer[] array = {1, 20, 100};
System.out.println(Arrays.toString(array));
```

### sort

可以使用默认的排序方法或自定的排序方法

-   默认排序方法

```Java
Integer[] array = {1, -1, 7, 0, 89};
Arrays.sort(array);
System.out.println(Arrays.toString(array));
```

-   使用自定的排序方法

```Java
Integer[] array = {1, -1, 7, 0, 89};
Arrays.sort(array, new Comparator<Integer>() {
    @Override
    public int compare(Integer o1, Integer o2) {
        return o2 - o1;
    }
});
System.out.println(Arrays.toString(array));
```

#### 模拟自定义排序

```Java
public class Main {
    public static void main(String[] args) {
        Integer[] array2 = {1, -1, 7, 0, 89};
        bubbleSort02(array2, new Comparator() {
            @Override
            public int compare(Object o1, Object o2) {
                int i1 = (Integer) o1;
                int i2 = (Integer) o2;
                return i1 - i2;
            }
        }); 
    }
    
    public static void bubbleSort02(Integer[] array, Comparator c) {
        int temp = 0;
        if (array != null) {
            for (int i = 0; i < array.length - 1; i++) {
                for (int j = 0; j < array.length - 1 - i; j++) {
                    if (c.compare(array[j], array[j+1]) > 0) {
                        temp  = array[j];
                        array[j] = array[j+1];
                        array[j+1] = temp;
                    }
                }
            }
        }
    }
}
```

### binarySearch

-   通过二分搜索法查找数组元素，**要求数组必须排好序**
-   如果数组中不存在该元素，就返回应该在的下标取 - 1

```Java
Integer array = {1, 2, 30, 50, 72};
int index = Arrays.binarySearch(array, 30); //index为2
int index = Arrays.binarySearch(array, 32); //index为-4
```

### copyOf

-   从一个数组中复制指定数量个元素到新的数组
-   如果指定数量大于原数组的元素个数，新的数组会在后面添加null
-   如果指定数量为负数，程序会抛出异常

```Java
Integer array3 = {1, 2, 30, 50, 72};
Integer[] array4 = Arrays.copyOf(array3, array3.length);
System.out.println(Arrays.toString(array4));
```

### fill

用指定数字填充数组，可以理解**将数组所有元素替换为指定数字**

```Java
Integer[] array5 = {1, 5, 2, 10};
Arrays.fill(array5, 20);
System.out.println(Arrays.toString(array5)); //输出[20, 20, 20, 20]
```

### equals

用于判断两个数组的元素是否完全一致

```Java
Integer[] array6 = {1, 2, 3, 4, 5};
Integer[] array7 = {1, 2, 3, 4, 5};
Integer[] array8 = {1, 3, 2, 4, 5};
System.out.println(Arrays.equals(array6, array7)); //输出true
System.out.println(Arrays.equals(array6, array8)); //输出false
```

