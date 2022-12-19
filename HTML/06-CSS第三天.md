# CSS 三大特性

## 层叠性

相同的选择器设置相同的样式，此时一个样式就会**覆盖 (层叠)**另一个冲突的样式。层叠性主要解决样式冲突的问题

层叠性原则：

-   样式冲突，遵循**就近原则**。哪个样式离结构近，就执行哪个样式
-   不冲突的样式，不会被层叠

```css
div {
    color: red;
    font-size: 48px; /* 不会被覆盖 */
}
div {
    color: blue; /* 会覆盖上一个选择器的color */
}
```

## 继承性

CSS 中的继承性指：子标签会继承父标签的某些样式，例如文字颜色和字号

![继承性.jpg](https://s2.loli.net/2022/12/19/jBF3NVvfhZS8Yp6.jpg)

-   子元素可以继承父元素的样式 (`text-` , `font-` , `line-` 这些元素开头的可以继承，以及 `color` 属性)

### 行高的继承性

```css
body {
    color: blue;
    font: 12px/1.5 'Microsoft YaHei';
}
div {
    font-size: 14px;
}
p {
    font-size: 18px;
}
```

-   行高可以跟单位也可以不跟单位
-   当行高不带单位时，其真实大小为 **字体大小 * 数值**
-   不带单位的写法的优势在于可以**让子元素根据自己的文字大小调整行高**

## 优先级

当同一个元素指定多个选择器，就会有优先级的产生

-   选择器相同，则执行层叠性原则
-   选择器**不同**，则根据**选择器权重**执行

| 选择器               | 权重            |
| -------------------- | --------------- |
| 继承 或者 *          | 0,0,0,0         |
| 元素选择器           | 0,0,0,1         |
| 类选择器，伪类选择器 | 0,0,1,0         |
| ID选择器             | 0,1,0,0         |
| 行内样式 `style=""`  | 1,0,0,0         |
| 重要 `!important`    | $\infty$ 无穷大 |

**重要 `!important` > 行内样式 `style=""` > ID选择器 > 类选择器、伪类选择器 > 元素选择器 > 继承 或者 ***

**示例：**

```html
<head>
    <style>
        div {
            color: aqua;
        }

        .nav {
            color: blue!important;
        }

        #demo {
            color: brown;
        }
    </style>
</head>
<body>
    <div class="nav" id="demo" style="color: purple">CSS选择器的优先级</div>
</body>
</html>
```

**注意事项**

-   权重是由4位数字组成，**不会有进位**
-   等级判断从左向右，如果某一个数值相同，则判断下一位
-   **继承的权重是 0**，如果该元素没有直接选中，不管父元素权重多高，子元素得到的权重都是 0

**权重叠加**

```css
ul li { /* 0,0,0,1 + 0,0,0,1 = 0,0,0,2 */
    color: blue;
}

li { /* 0,0,0,1 */
    color: red;
}
.nav li { /* 0,0,1,0 + 0,0,0,1 = 0,0,1,1 */
    color: aqua;
}
```

<hr>

# CSS 盒子模型

## 看透网页布局

网页布局过程：

1.   先准备好相关的网页元素，网页元素基本都是盒子 Box
2.   利用 CSS 设置好盒子样式，然后摆放到相应的位置
3.   往盒子里装内容

## 盒子模型

**盒子模型**：就是把 HTML 页面中的布局元素看作是个矩形的盒子

CSS 盒子模型本质就是一个盒子，封装周围的 HTML 元素，它包括：边框（Border）、外边距（Margin）、内边距（Padding）和实际内容（Content）

![boxmodel.jpg](https://s2.loli.net/2022/12/19/2TaNAGjvspbeQYE.jpg)

## 边框

border 可以设置元素的边框。边框由三部分组成：**边框宽度**、**边框样式**和**边框颜色**

```css
border: border-width || border-style || border-color;
```

| 属性           | 作用                                                         |
| -------------- | ------------------------------------------------------------ |
| `border-width` | 定义边框的粗细，单位是 `px`                                  |
| `border-style` | 边框的样式，常见有 : `solid` (实线) `dashed` (虚线) `dotted` (点线) |
| `border-color` | 边框的颜色                                                   |

边框简写 : `border: 1px solid blue;` **(无顺序)**

边框分开写法 : `border-top: 5px solid blue;`

**注意**

边框会额外增加盒子的实际大小，有如下两种方法解决：

-   测量盒子大小时，不量边框
-   如果测量盒子大小时包含了边框，则需要在 `width/height` 减去边框大小

 ## 表格细线边框

`border-collapse` 属性用于控制浏览器绘制表格边框的方法，它控制相邻单元格的边框

语法：

```css
border-collapse: collapse; /* 表示相邻的边框合并在一起 */
```

## 内边距

`padding` 属性用于设置内边距，即边框与内容之间的距离

| 属性             | 说明     |
| ---------------- | -------- |
| `padding-left`   | 左内边距 |
| `padding-right`  | 右内边距 |
| `padding-top`    | 上内边距 |
| `padding-bottom` | 下内边距 |

**`padding` 属性简写**

| 值的个数                       | 说明                                    |
| ------------------------------ | --------------------------------------- |
| `padding: 5px;`                | 代表上下左右都有 5px 内边距             |
| `padding: 5px 10px;`           | 代表上下内边距是 5px，左右内边距是 10px |
| `padding: 5px 10px 20px`       | 代表上5px，左右10px，下20px             |
| `padding: 5px 10px 20px 30px;` | 代表上5px，右10px，下20px，左30px       |

**注意**

-   内边距会额外增加盒子的实际大小，解决方法：让 `width/height` 减去多出来的内边距即可
-   如果盒子本身没有指定 `width/height` 的大小，则此时 `padding` 不会撑开盒子

## 外边距

`margin` 属性用于设置外边距，即控制盒子与盒子之间的距离

| 属性            | 说明     |
| --------------- | -------- |
| `margin-left`   | 左外边距 |
| `margin-right`  | 右外边距 |
| `margin-top`    | 上外边距 |
| `margin-bottom` | 下外边距 |

**`margin` 的简写方式和 `padding` 一致**

外边距可以让块级盒子**水平居中**，但是必须满足两个条件：

1.   盒子指定了宽度 `width`
2.   盒子**左右的外边距**设置为 `auto`

以上是块级元素水平居中对齐的方法，行内元素或行内块元素水平居中对齐，给其父元素添加 `text-align: center;` 即可

**示例**

```html
<head>
    <style>
        .header {
            width: 1000px;
            height: 300px;
            margin: 200px auto;
            background-color: aqua;
        }
    </style>
</head>
<body>
    <div class="header"></div>
</body>
```

### 外边距合并

外边距合并指的是，当两个垂直外边距相遇时，它们将形成**一个外边距**。合并后的外边距的高度等于两个发生合并的外边距的高度中的**较大者**。

当一个元素出现在另一个元素上面时，第一个元素的下外边距与第二个元素的上外边距会发生合并。

![margin_collapsing_1.gif](https://s2.loli.net/2022/12/19/gf6xe1mDdhFp9S8.png)

当一个元素包含在另一个元素中时 (假设没有内边距或边框把外边距分隔开) ，它们的上和/或下外边距也会发生合	并。

![margin_collapsing_example_2.gif](https://s2.loli.net/2022/12/19/mdSpDxV1BErAOw3.png)

**解决第二种情况的方法：**

1.   可以为父元素设置上边框
2.   可以为父元素设置上内边距
3.   可以为父元素添加 `overflow: hidden;`

## 清楚内外边距

网页元素很多都带有默认的内外边距，而且不同的浏览器的默认值也不一样，因此我们在网页布局前，需要清楚网页元素的内外边距

```css
* {
    margin: 0; /* 清楚外边距 */
    padding: 0; /* 清楚内边距 */
}
```

**注意：**行内元素为了照顾兼容性，尽量只设置左右内外边距，不要设置上下内外边距。如有需要，转为块级元素或行内块元素即可

# 圆角案例

`border-radius` 属性用于设置元素的外边框圆角

```css
border-radius: length;
```

圆角原理：圆与边框的交集形成圆角效果

-   参数值可以是**数值**或**百分比**的形式
-   如果是**正方形**，想要设置为一个圆，把数值改为边长的一半即可
-   该属性是一个简写属性，可以跟四个数值，分别代表左上角、右上角、右下角、左下角
-   分开写是 `border-top-left-radius` , `border-top-right-radius` , `border-bottom-right-radius` , `border-bottom-left-radius`

# 盒子阴影

我们可以使用 `box-shadow` 属性为盒子添加阴影

```css
box-shadow: h-shadow v-shadow blur spread color inset;
```

| 参数名     | 说明                           |
| ---------- | ------------------------------ |
| `h-shadow` | 必要，水平阴影的位置，允许负值 |
| `v-shadow` | 必要，垂直阴影的位置，允许负值 |
| `blur`     | 可选，模糊距离                 |
| `spread`   | 可选，阴影的尺寸               |
| `color`    | 可选，阴影的颜色               |
| `insrt`    | 可选，将外部阴影改为内部阴影   |

# 文字阴影

我们可以使用 `text-shadow` 属性将阴影应用于文本

```css
text-shadow: h-shadow v-shadow blur color;
```

| 参数名     | 说明                 |
| ---------- | -------------------- |
| `h-shadow` | 必要，水平阴影的位置 |
| `v-shadow` | 必要，垂直阴影的位置 |
| `blur`     | 可选，模糊的距离     |
| `color`    | 可选，阴影的颜色     |

![]()
