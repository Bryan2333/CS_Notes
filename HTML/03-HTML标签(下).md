# HTML 标签（下）

## 表格标签

### 主要作用

表格**用于显示、展示数据**，可以让数据显示的**规整、清晰**，提高可读性

### 基本语法

```Html
<table>
    <tr>
        <td>单元格内文字</td>
    </tr>
</table>
```

1.   `<table></table>` ：用于定义表格的标签
2.   `<tr></tr>` ：用于定义表格中的**行**，必须嵌套在 `table` 标签中
3.   `<td></td>` ：用于定义表格中的**列**，必须嵌套在 `tr` 标签中
4.   字母 `td` 指表格数据(table data)，即数据单元格的内容

**示例：**

```html
<table>
    <tr><td>姓名</td> <td>年龄</td> <td>性别</td></tr>
    <tr><td>张三</td> <td>23</td> <td>男</td></tr>
    <tr><td>Smith</td> <td>39</td> <td>男</td></tr>
</table>
```

### 表头单元格标签

表头单元格一般位于**表格的第一行或第一列**，表头单元格内的文本内容**加粗居中**显示

`<th>` 标签表示 HTML 表格的**表头部分**(table head)

**示例：**

```html
<table>
    <tr><th>name</th> <th>age</th> <th>sex</th></tr>
    <tr><td>张三</td> <td>23</td> <td>男</td></tr>
    <tr><td>Smith</td> <td>39</td> <td>男</td></tr>
</table>
```

### 表格属性

表格属性一般不用，实际开发中通常用 CSS 来设置

| 属性名      | 属性值            | 说明                             |
| ----------- | ----------------- | -------------------------------- |
| align       | left right center | 规定表格相对周围元素的对齐方式   |
| border      | 1 或 ""           | 规定表格单元是否有边框           |
| cellpadding | 像素值            | 规定单元格边沿与其内容之间的空白 |
| cellspacing | 像素值            | 规定单元格之间的空白             |
| width       | 像素值            | 规定表格的宽度                   |
| height      | 像素值            | 规定表格的高度                   |

### 表格结构标签

在表格中，可以用 `<thead>` 标签表示表格 **头部** 区域， `<tbody>` 标签表示表格 **主体** 区域，来使表格的结构更加清晰

**示例：**

```html
<table>
    <!-- 表格头部 --> 
    <thead> 
        <tr><th>name</th> <th>age</th> <th>sex</th></tr>
    </thead>
    <!-- 表格主体 -->
    <tbody> 
        <tr><td>张三</td> <td>23</td> <td>男</td></tr>
	<tr><td>Smith</td> <td>39</td> <td>男</td></tr>
    </tbody>
</table>
```

### 合并单元格

**合并方式：**

1.   跨行合并：`rowspan="合并单元格个数"`
2.   跨列合并：`colspan="合并单元格个数"`

**目标单元格：**

1.   跨行：最上侧单元格为目标单元格，写合并代码
2.   跨列：最左侧单元格为目标单元格，写合并代码

**合并步骤：**

1.   先确定式跨行还是跨列合并单元格
2.   找到目标单元格，写上对应的合并代码
3.   删除多余的单元格

**示例：**

```html
<table border="1" width="500" height="250" cellspacing="0">
    <tr>
        <td></td>
        <td colspan="2"></td>
        <!-- <td></td> -->
    </tr>
    <tr>
        <td rowspan="2"></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <!--  <td></td> -->
        <td></td>
        <td></td>
    </tr>
</table>
```

![合并单元格.jpg](https://s2.loli.net/2022/12/19/TwPEyFI7ro1iJe2.jpg)

## 列表标签

### 主要作用

表格用来展示数据，列表是用来布局的

列表可以分为三大类：**无序列表**、**有序列表**、**自定义列表**

### 无序列表

`<ul>` 标签用来表示 HTML 中的无序列表，而列表项用 `<li>` 标签定义

```html
<ul> <!-- ul: Unordered list -->
    <li>Item One</li> <!-- li: list item -->
    <li>Item Two</li>
    <li>Item Three</li>
</ul>
```

1.   `<ul>` 标签中只能嵌套 `<li>` 标签，直接在 `<ul>` 标签中输入其他标签或文字是不允许的
2.   `<li>` 标签相当于一个容器，可以**容纳所有元素**
3.   无序列表带有自己的样式属性，但在实际开发中，会用 CSS 来设置

### 有序列表

`<ol>` 标签用来表示 HTML 中的有序列表，而列表项用 `<li>` 标签定义

```html
<ol> <!-- ol: Ordered list -->
    <li>First Item</li> <!-- li: list item -->
    <li>Second Item</li>
    <li>Third Item</li>
</ol>
```

1.   `<ol>` 标签中只能嵌套 `<li>` 标签，直接在 `<ol>` 标签中输入其他标签或文字是不允许的
2.   `<li>` 标签相当于一个容器，可以**容纳所有元素**
3.   无序列表带有自己的样式属性，但在实际开发中，会用 CSS 来设置

### 自定义列表

在 HTML 标签中，`<dl>` 标签用于定义描述列表(或定义列表)，该标签会与 `<dt>` (定义项目/名字)和 `<dd>` (描述每一个项目/名字)一起使用

```html
<dl> <!-- dl: Definition List -->
    <dt>关注我们</dt> <!-- dt: Definition Terms -->
    <dd>新浪微博</dd> <!-- dd: Definition Description -->
    <dd>官方微信</dd>
    <dd>联系我们</dd>
    
    <dt>Word</dt>
    <dd>Word Desc1</dd>
    <dd>Word Desc2</dd>
    <dd>Word Desc3</dd>
</dl>
```

1.   `<dl>` 标签里只能包含 `<dt>` 标签和 `<dd>` 标签
2.   `<dt>` , `<dd>` 标签没有个数限制，通常是**一个** `<dt>` 标签对应**多个** `<dd>` 标签

### 其他

1.   可以使用 `list-style: none;` 去掉列表的小圆点

## 表单标签

### 表单作用

1.   收集用户信息
2.   网页中需要与用户交互，收集用户信息，这个时候就需要表单

### 表单的结构

在 HTML 中，一个完整的表单通常由**表单域**、**表单控件**(也成为表单元素)和**提示信息**构成

![表单结构.jpg](https://s2.loli.net/2022/12/19/GgnNy7LjFXMY5hl.jpg)

### 表单域

**表单域**是一个**包含表单元素的区域**。

在 HTML 标签中，**`<form>`** 标签用于定义表单域，以实现用户信息的收集和传递

**`<form>` 会把它范围内的表单元素信息提交给服务器**

```html
<form action="demo.php" method="post" name="表单域Demo">
	<!-- 各种表单元素 -->
</form>
```

**常用属性：**

| 属性   | 属性值      | 说明                                            |
| ------ | ----------- | ----------------------------------------------- |
| action | URL地址     | 用于指定接收并处理表单数据的服务器程序的URL地址 |
| method | get 或 post | 用于设置表单数据的提交方式                      |
| name   | 名称        | 用于设置表单域的名称，以区别同一页面的表单域    |

### 表单元素

#### \<input> 标签

在表单中，`<input>` 标签用于收集用户信息

`<input>` 标签中，包含一个 `type` 属性，根据不同的 `type` 值，**输入字段可以有多种形式**

```html
<input type="属性值">
```

-   `<input>` 标签为单标签
-    `type` 的属性设置不同的值来指定使用不同的控件

**type 属性的值：**

| 属性值   | 说明                                             |
| -------- | :----------------------------------------------- |
| button   | 定义可点击按钮，通常配合 Javascript 使用         |
| checkbox | 定义复选框                                       |
| file     | 定义输入字段和"浏览"按钮，供文件上传             |
| hidden   | 定义隐藏的输入字段                               |
| image    | 定义图片形式的提交按钮                           |
| password | 定义密码字段，字段中的字符会被隐藏               |
| radio    | 定义单选按钮                                     |
| reset    | 定义重置按钮，重置按钮会重置表单中的所有数据     |
| submit   | 定义提交按钮，点击后会将表单数据发送给服务器程序 |
| text     | 定义单行的输入字段默认宽度为20个字符             |

除了 `type` 属性外，`<input>` 标签还有其他的属性：

| 属性名    | 属性值   | 说明                                |
| --------- | -------- | ----------------------------------- |
| name      | 用户自定 | 定义 `input` 元素的名称             |
| value     | 用户自定 | 定义 `input` 元素的默认值           |
| checked   | checked  | 规定此 `input` 元素首次加载时被选中 |
| maxlength | 正整数   | 规则输入字段的最大宽度              |

1.   `name` 属性是当前表单元素的名字，后端程序可以通过 `name` 属性来找到表单元素。`name` 元素的主要作用就是**区分不同的表单元素**
2.   **同一组 `radio` 或 `checkbox` ，必须给它们同一个 `name` 属性值**

**示例：**

```html
<form action="demo.php" method="get" name="input">
    <!-- text 为文本框 用户可以在框内输入任何文字 --> <!-- value 给表单元素设置默认的值-->
    用户名: <input type="text" name="username" value="请输入用户名" maxlength="10"> <br>
    <!-- password 为密码框 -->
    密码: <input type="password" name="password"> <br>
    <!-- radio 为单选按钮 -->
    性别: 男 <input type="radio" name="sex" value="男"> 女 <input type="radio" name="sex" value="女"> <br>
    
    <!-- checkbox 为复选框 -->
    爱好: Coding <input type="checkbox" name="hobby" checked="checked"> Gaming <input type="checkbox" name="hobby"> Music <input type="checkbox" name="hobby"> <br>
    上传头像: <input type="file" name="file" id=""> <br>
    <!-- botton 为普通按钮 一般与 Javascript 配合使用 -->
    <input type="button" value="获取短信验证码"> <br>
    <!-- submit 为提交按钮 点击后会将 表单域 里的表单元素 里的值 提交给服务器程序 -->
    <input type="submit" value="免费注册"> 
    <!-- reset 为重置按钮 点击后会重置表单元素里的值 -->
    <input type="reset" value="重新填写">
</form>
```

#### \<label> 标签

`<label>` 标签为 input 元素定义标注(标签)

`<label>` 标签用于**绑定一个表单元素**，当点击 `<label>` 标签内的文本时，浏览器会自动将焦点转到对应的表单元素，用来增加用户体验

```html
<label for="sex">男</label> <input type="radio" name="sex" id="sex"/>
```

**核心：`<label>` 标签的 for 属性应当与相关元素的 id 属性相同**

#### \<select> 标签

在页面中，如果有**多个选项**让用户选择，并且要**节省页面的空间**，开发者可以使用 **`<select>`** 标签定义**下拉列表**

```html
<form action="">
    <select>
        <option>Option 1</option>
        <option>Option 2</option>
    </select>
    
    籍贯: <select name="" id="">
        <option value="">山东</option>
        <option value="">广东</option>
        <option value="">地球</option>
        <option value="" selected>赛博</option>
    </select>
</form>
```

1.   `<select>` 标签里至少包含一对 `<option>` 标签
2.   在 `<option>` 标签中定义 `selected="selected"` 时，被定义项为默认选项

#### \<textarea> 标签

```html
<form action="">
    今日反馈: 
    <textarea name="" id="" cols="30" rows="10">
        This is a text area
    </textarea>
</form>
```

1.   通过 `<textarea>` 标签可以创建多行文本输入框
2.   实际开发中，开发者一般通过 CSS 控制文本框的大小
