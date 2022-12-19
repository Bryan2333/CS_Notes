# Collections工具类

1.   Collections 是一个操作Set、List 和 Map 等集合的工具类
2.   Collections 中提供了一系列对集合元素进行排序、查询和修改的静态方法

## 常用方法

### reverse

反转List中的元素

```Java
 List list = new ArrayList();
 list.add("tom");
 list.add("smith");
 list.add("king");
 list.add("milan");
 Collections.reverse(list);
 System.out.println(list); //输出[milan, king, smith, tom]
```

### shuffled

对List中的元素随机排序

```Java
Collections.shuffle(list);
System.out.println(list); //输出[king, tom, smith, milan]
```

### Sort

默认情况下，根据元素的自然顺序进行排序

```Java
Collections.sort(list);
System.out.println(list); //输出[king, milan, smith, tom]
```

可以使用指定的比较器产生的顺序进行排序

```Java
Collections.sort(list, new Comparator<Object>() {
    @Override
    public int compare(Object o1, Object o2) {
        //按字符串长度排序
        return ((String) o1).length() - ((String) o2).length();
    }
});
System.out.println(list); //输出[tom, king, milan, smith]
```

### swap

`swap(List, int, int)` 将指定的List中 i 处 和 j 处的元素交换

```Java
Collections.swap(list, 1, 3);
System.out.println(list); //输出[tom, milan, king, smith]
```

### max

默认情况下，根据元素的自然顺序，返回集合中的最大元素

```Java
System.out.println(Collections.max(list)); //输出tom
```

可以使用指定的比较器产生的顺序返回最大值

```Java
Object maxObj = Collections.max(list, new Comparator() {
    @Override
    public int compare(Object o1, Object o2) {
        return ((String) o1).length() - ((String) o2).length();
    }
});
System.out.println(maxObj);
```

### frequency

返回集合中指定元素的出现次数

```Java
System.out.println(Collections.frequency(list, "tom")); //输出1
```

### Copy

`copy(list dest, list src)` 复制src的内容到dest

注意如果 dest 的 size 小于 src 的 size 会报错

```Java
List dest = new ArrayList();
//先对dest扩容，否则会报错
for (int i = 0; i < list.size(); i++) {
    dest.add(null);
}
Collections.copy(dest, list);
System.out.println(dest); //输出[tom, king, milan, smith]
```

### ReplaceAll

`replaceAll(List list, Object oldValue, Object newValue)` 用新值替换掉List中所有的旧值

```Java
list.add("tom");
System.out.println(list); //输出[tom, king, milan, smith, tom]
Collections.replaceAll(list, "tom", "TOM");
System.out.println(list); //输出[TOM, king, milan, smith, TOM]
```

