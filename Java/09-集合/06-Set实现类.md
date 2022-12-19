# HashSet

## 基本介绍

1.   HashSet类实现了Set接口
2.   HashSet实际上是HashMap
     1.   ![HashSet1.jpg](https://s2.loli.net/2022/12/19/pDTd5y1VPgfseN6.jpg)
3.   可以存放null值，但是只能有一个
4.   HashSet不保证元素是否有序。元素的顺序取决于Hash后，再确定索引的结果

## 底层机制

### 添加元素

1.   **HashSet底层是HashMap，HashMap的底层是数组+链表+红黑树**
2.   添加元素的步骤：
     1.   添加一个元素时，会先得到这个元素的hash值，再根据hash值转成对应的索引
     2.   找到数据表table，判断该索引的位置上是否已经存放元素 
          -   没有：直接加入 
          -   有：调用equals方法，如果结果相同就放弃添加。如果不同，就放在链表的末尾

#### 模拟数组+链表

```Java
public class HashSetStructure {
    public static void main(String[] args) {

        //1. 创建一个数组，数组类型是Node[]
        Node[] table = new Node[16];
        System.out.println("table = " + Arrays.toString(table));

        Node john = new Node("john", null);
        table[2] = john;//将john放到table表索引为3的地方

        Node jack = new Node("jack", null);
        john.next = jack; //将jack结点挂载到john的下一个结点


        Node rose = new Node("Rose", null);
        jack.next = rose;

        Node lucy = new Node("Lucy", null);
        table[3] = lucy; //将luck放到table表索引为3的地方
       
        Node peter = new Node("Peter", null);
        lucy.next = peter;
      
        System.out.println("table = " + Arrays.toString(table));
        
       	/*	
       	table[2] = john -> jack -> rose
       	table[3] = lucy -> peter
       	*/

    }
}

//结点，存放数据，指向下一个结点
class Node {
    Object item; //存放数据
    Node next; //指向下一个结点

    public Node(Object item, Node next) {
        this.item = item;
        this.next = next;
    }
}
```

#### 源码分析

```Java
//先执行HashSet()
public HashSet() {
    map = new HashMap<>();
}

//执行add()
public boolean add(E e) {
    //PRESENT: private static final Object PRESENT = new Object();
    return map.put(e, PRESENT)==null; //如果put返回的是null,则添加成功,否则就是添加失败
}

//执行put()
public V put(K key, V value) { //key是我们要添加的元素, value是共享的
    return putVal(hash(key), key, value, false, true); //返回putVal的返回值
}

//先用hash()算出key的hash值
static final int hash(Object key) {
    int h;
    //key为空就返回null,否则返回对应的hash值
    //算法 h = key.hashCode() ^ (h >>> 16)
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
}

//再执行puVal()
final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
           boolean evict) {
		//table 就是 HashMap 的一个数组，类型是 Node[]
        Node<K,V>[] tab; Node<K,V> p; int n, i; //定义辅助变量
        //if语句表示如果table是空的或者大小为0
    	//就进行第一次扩容，扩容到16个空间
        if ((tab = table) == null || (n = tab.length) == 0)
            n = (tab = resize()).length;
        //1. 根据key得到hash，去计算该key应该放到table的哪一个索引位置
        // 并将这个位置的对象赋给p
        //2. 判断p是否为空，如果p为null，就表示还没有元素，就直接创建Node
    	//放在tab[i] = newNode(hash, key, value, null)
        if ((p = tab[i = (n - 1) & hash]) == null)
            tab[i] = newNode(hash, key, value, null);// (key="java", value=PRESENT)
        else {
        // 一个开发技巧提示：在需要的地方定义局部变量(辅助变量)
            Node<K,V> e; K k; //定义辅助变量
            //将当前的hash值给p.hash
            //如果当前索引位置对应的链表的第一个元素和准备添加的key的hash值一样,并且满足以下条件之一
            //1.满足准备加入的key 和 p指向的Node结点 的 key 是同一个对象
            //2.p指向的Node 结点的 key 的equals方法和准备加入的key比较后相同
            //就无法加入
            if (p.hash == hash &&
                ((k = p.key) == key || (key != null && key.equals(k))))
                e = p;
            //再判断 p 是不是一棵红黑树
            //如果是红黑树，就调用 putTreeVal 方法来添加元素
            else if (p instanceof TreeNode)
                e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, valu
            else { //如果当前table对应的索引位置已经是一个链表，就用for循环依次比较
                   //1.如果都不相同，就挂载到该链表的最后
                for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) { //如果p的下一个结点为空，就直接挂载上去
                        p.next = newNode(hash, key, value, null);
                        //3.添加元素到链表后，立即判断该链表是否已经有8个结点
                  		//如果达到8个结点，就调用treeifyBin方法将链表树化
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    //2.如果比较过程中有相同的情况，就直接break退出循环
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k)
                        break;
                    p = e;
                }
            }
            if (e != null) { // existing mapping for key
                V oldValue = e.value;
                if (!onlyIfAbsent || oldValue == null)
                    e.value = value;
                afterNodeAccess(e);
                return oldValue;
            }
        }
        ++modCount;
        if (++size > threshold)
            resize();
        afterNodeInsertion(evict);
        return null; //返回null
    }
```

### 扩容

1.   HashSet底层是HashMap。第一次添加元素时，table数组扩容到16，临界值  `threshold` 是16 * 加载因子 `loadFactor` 的0.75 = 12
2.   如果table数组使用到了临界值12，就会扩容到16 * 2 = 32，新的临界值就是32 * 0.75 = 24，依此类推
     1.   **注意：使用到了临界值12不是指有十二条链表，而是整个table有12个元素**
3.   在Java8以及后来的版本中，如果一条链表的元素个数**到达** `TREEIFY_THRESHOLD` (默认是8)，并且table大小**大于等于** `MIN_TREEIFY_CAPACITY` (默认是64)，就会进行树化，否则依然采用数组的扩容机制

#### 示例

-   扩容（有12个链表且有12个元素）

```Java
public class HashSetIncrement {
    public static void main(String[] args) {
        HashSet hashSet = new HashSet();
        
        for (int i = 1; i <= 100; i++) {
            hashSet.add(i);
        }
    }
}
```

-   扩容（达到了12个元素）

```Java
public class HashSetIncrement02 {
    public static void main(String[] args) {
        HashSet hashSet = new HashSet();
        for (int i = 0; i < 7; i++) {
            hashSet.add(new A(100)); //单条链表上有7个元素
        }
        
        for (int i = 0; i < 7; i++) {
            hashSet.add(new B(200)); //另外一条链表上有7个元素
        }
    }
}

class A {
    private int n;

    public A(int n) {
        this.n = n;
    }

    @Override
    public int hashCode() {
        return 100;
    }
}

class B {
    private int n;
    
    public B(int n) {
        this.n = n;
    }
    
    @Override
    public int hashCode() {
        return 200;
    }
}
```

-   树化

```Java
public class HashSetTreeify {
    public static void main(String[] args) {
        HashSet hashSet = new HashSet();
        for (int i = 0; i < 12; i++) {
            hashSet.add(new A(100));
        }
    }
}

class A {
    private int n;

    public A(int n) {
        this.n = n;
    }

    @Override
    public int hashCode() {
        return 100;
    }
}
```

# LinkedHashSet

## 基本介绍

1.   LinkedHashSet 是 HashSet 的一个子类
2.   LinkedHashSet 的底层是 LinkedHashMap，维护了一个（数组+双向链表）
3.   LinkedHashSet 根据元素的 HashCode 决定元素的存放位置，同时使用双向链表维护元素的次序
4.   LinkedHashSet 不允许重复的元素

## 底层机制

### 添加元素

1.   在 LinkedHashSet 中维护了一个Hash表和双向链表(有 head 和 tail)
2.   双向链表中每一个结点有 before 和 after 属性，这样可以形成双线链表
3.   在添加一个元素时，先算出元素的hash值，再求索引以确定该元素的 table 中的位置，然后再将该元素添加到双向链表中
4.   **因此 LinkedHashSet 能保证插入顺序和遍历顺序一致**

# TreeSet

