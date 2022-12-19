# System类

## 常见方法

### exit

退出当前程序

```Java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello");
        System.exit(0); //程序正常退出。0是状态值，表示正常状态
        System.out.println("Java");
    }
}
```

### arraycopy

`System.arraycopy(src, srcPos, dest, destPos, length)`

1.   `src` 表示原数组
2.   `srcPos` 表示从原数字哪个下标开始拷贝
3.   `dest` 表示目标数组
4.   `destPos` 表示将原数组的数据拷贝到目标数组的哪个下标
5.   `length` 表示从原数组拷贝多少个元素

```Java
int[] srcArr = {1, 2, 3};
int[] destArr = new int[3];
System.arraycopy(srcArr, 0, destArr, 0, 3);
System.out.println(Arrays.toString(destArr)); //输出[1, 2, 3]
```

### currentTimeMillis

返回的是当前时间与协调世界时 1970 年 1 月 1 日午夜之间的时间差（毫秒）

```Java
System.out.println(System.currentTimeMillis());
```

