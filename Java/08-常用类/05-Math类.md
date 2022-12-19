# Math类

Math类包含各种数学运算的方法

## 常见方法

### abs

求一个数字的绝对值

```Java
int absNum = Math.abs(-10);
System.out.println(absNum); //输出10
```

### pow

求幂

```Java
int powNum = Math.pow(2, 3);
System.out.println(powNum); //输出8
```

### ceil

向上取整，返回大于等于该数的最小整数

```Java
double ceilNum = Math.ceil(3.8);
System.out.println(ceilNum); //输出4.0
```

### floor

向下取整，返回小于等于该数的最大整数

```Java
double floorNum = Math.floor(4.5);
System.out.println(floorNum); //输出4
```

### round

四舍五入

```Java
long roundNum = Math.round(5.3);
System.out.println(roundNum); //输出5
```

### sqrt

开方，如果参数是负数会返回NaN（Not a Number）

```Java
double sqrtNum = Math.sqrt(9);
System.out.println(sqrtNum); //输出3
```

### random

返回区间 [0,1) 内的一个随机小数

#### 示例

取 [a,b] 之间的数字：`(int)(a + Math.random() * (b - a + 1))`

```Java
//随机生成1~10的整数并输出 10次
for (int i = 0; i < 10; i++) {
    int random = (int)(1 + Math.random() * 10);
    System.out.println(random);
}
```

