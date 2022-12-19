# ArrayList

## 使用细节

1.   ArrayList允许存放所有元素，包括 `null`
2.   ArrayList是由数组来实现数据存储的
3.   ArrayList基本等同于Vector，但**ArrayList是线程不安全的**（执行效率高）。多线程情况下，不建议使用ArrayList

## 扩容方法

1.   ArrayList对象中维护了一个Object类型的数组 `transient Object[] elementData`
2.   如果使用无参构造器创建ArrayList对象，则elementData的初始容量为0，第一次添加元素时扩容为10。从第二次扩容开始，每次扩容后的容量为原来的1.5倍
3.   如果使用指定大小的构造器创建ArrayList对象，则elementData的初始容量为指定大小。从第一次扩容开始，每次扩容后的容量为原来的1.5倍

# Vector

## 使用细节

1.   Vector底层也是一个Object类的数组 `protected Object[] elementData`
2.   **Vector是线程同步，即线程安全的**
3.   在开发中，需要线程同步安全时，考虑使用Vector

## 扩容方法

1.   如果使用无参构造器创建Vector对象，则elementData的初始容量为10。从第一次扩容开始，每次扩容后的容量为原来的2倍
2.   如果使用指定大小的构造器创建Vector对象，则elementData的初始容量为指定大小。从第一次扩容开始，每次扩容后的容量为原来的2倍

# LinkedList

1.   LinkedList底层实现了双向链表和双端队列的特点
2.   可以添加任意元素，包括null
3.   线程不安全，没有实现同步

## 底层操作机制

1.   LinkedList底层是一个双向链表
2.   LinkedList中有两个属性 `first` 和 `last` 分别指向首节点和末节点
3.   每个节点（Node对象）里面有 `prev` 、`next` 、`item` 三个属性，其中通过 `prev` 指向前一个节点，通过 `next` 指向后一个节点，最终实现双向链表
4.   所有LinkedList的元素的添加与删除，不是通过操作数组来完成的，相对效率较高

### 模拟链表

```Java
public class Main {
    @SuppressWarnings("all")
    public static void main(String[] args) {

        Node jack = new Node("jack");
        Node tom = new Node("tom");
        Node smith = new Node("Smith");
        Node peter = new Node("peter");

        // jack -> tom -> peter
        jack.next = tom;
        tom.next = peter;

        //peter -> tom -> jack
        peter.prev = tom;
        tom.prev = jack;

        Node first = jack; //让first指向jack,就是双向链表的头
        Node last = peter; //让last指向peter，就是双向链表的尾

        //从头到尾
        System.out.println("==========从头到尾=========");
        while (true) {
            if (first == null) {
                break;
            }
            System.out.println(first);
            first = first.next;
        }

        System.out.println("========从尾到头==========");
        while (true) {
            if (last == null) {
                break;
            }
            System.out.println(last);
            last = last.prev;
        }

        // tom ----------- peter之间插入 smith
        // jack -> tom -> smith -> peter
        smith.prev = tom; //smith的前一个节点为tom
        smith.next = peter; //smith的后一个节点为peter 

        peter.prev = smith; //peter的前一个节点为smith
        tom.next = smith; //tom的后一个节点为smith

        first = jack;
        System.out.println("==========从头到尾=========");
        while (true) {
            if (first == null) {
                break;
            }
            System.out.println(first);
            first = first.next;
        }

        last = peter;
        System.out.println("========从尾到头==========");
        while (true) {
            if (last == null) {
                break;
            }
            System.out.println(last);
            last = last.prev;
        }
    }
}

class Node {
    public Object item; //真正存放元素的地方
    public Node next; //指向后一个节点
    public Node prev; //指向前一个结点
    public String name;

    public Node(Object name) {
        this.item = name;
    }

    public String toString() {
        return "Node Name = " + item;
    }
}
```

## 和ArrayList比较

|            | 底层结构 |     增删的效率     | 改查的效率 |
| :--------: | :------: | :----------------: | :--------: |
| ArrayList  | 可变数组 |   较低，数组扩容   |    较高    |
| LinkedList | 双向链表 | 较高，通过链表追加 |    较低    |

1.   如果改查操作比较多，一般选择用ArrayList
2.   如果增删操作比较多，一般选择用LinkedList
