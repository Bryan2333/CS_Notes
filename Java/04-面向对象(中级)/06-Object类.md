# Object类

## equals方法

-   `==` 是一个比较运算符
    -   既可以判断基本类型，又可以判断引用类型
    -   如果判断基本类型，就判断值是否相当
    -   如果判断引用类型，就判断引用对象的地址是否相同，即引用变量是否指向一个对象
-   `equals` 是Object类的一个方法，只能用来判断引用类型
    -   默认用来判断对象地址是否相等，子类通常会重写该方法，用于判断内容是否相同

### 重写equals方法

**示例**

```Java
public class Person {
    private String name;
    private int age;
    private char gender;

    public Person(String name, int age, char gender) {
        setName(name);
        setAge(age);
        setGender(gender);
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public char getGender() {
        return gender;
    }

    public void setGender(char gender) {
        this.gender = gender;
    }

    //重写equals方法
    public boolean equals(Object obj) {
        //如果引用的对象是同一个对象
        if (this == obj) {
            return true;
        }
        if (obj instanceof Person p) {
            // Person p = (Person) obj;
            return this.name.equals(p.name) && p.age == this.age && p.gender == this.gender;
        }
        return false;
    }
}
```

## hashCode方法

-   hashCode可以提高具有哈希结构的容器的效率
-   两个引用，如果都指向同一个对象，则哈希值肯定一样
-   两个引用，如果指向的不是同一个对象，则哈希值肯定不同
-   hashCode主要根据对象的地址生成 

**示例**

沿用上述例子

```Java
public class Main{
    public static void main(String[] args) {
        Person p1 = new Person("Jack", 18, '男');
        Person p2 = new Person("Smith", 19, '男');
        Person p3 = p1;
        
        System.out.println(p1.hashCode() == p2.hashCode()); // false;
        System.out.println(p1.hashCode() == p3.hashCode()); // true
    }
}
```

## toString方法

-   默认返回：全类名+@+哈希值的十六进制字符串
-   子类通常会重写toString方法

**示例**

沿用上述例子

```Java
public class Person {
    private String name;
    private int age;
    private char gender;
    
    public String toString() {
        return "Person Info { "
            	+ "name: " + name + ","
            	+ " age: " + age + ","
            	+ " gender: " + gender
            	+ " }";
    }
}
```
