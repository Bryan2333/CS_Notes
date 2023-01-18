# CRUD语句

## insert 语句

```sql
INSERT INTO tablename (col1, col2) VALUES (value1, value2);
```

**使用细节**

-   插入数据应该与列表类型相同
-   数据长度需要在列规定的范围之内
-   `VALUES` 里面的数据位置必须与列的排序位置对应
-   字符和日期类型的数据需要放在单引号内
-   列可以插入空值，前提是列允许空值
-   `insert into table_name (col_names, ) values () () ()` 形式添加多条数据
-   如果是给表中的所有列添加数据，可以不写列名
-   如果该列没有声明 `NOT NULL` , 那么在添加数据时没有给值，则默认给 `null`

## update 语句

```sql
UPDATE tablename SET col_name = expr WHERE where_definition;
```

**使用细节**

-   **如果没有 `WHERE` 字句，则更新该表所有的记录**
-   如果需要修改多个字段可以使用 `set col1 = value1, col2 = value2`

## delete 语句

```sql
DELETE FROM tablename WHERE where_definition
```

**使用细节**

-   如果不使用` WHERE` 子句，则默认删除表中的所有数据
-   `DELETE` 语句不能删除某一列的值
-   `DELETE` 语句本身只能删除表中的记录，不能删除表

## select 语句

```sql
SELECT [DISTINCT] *|{column1, colum2, ...} FROM tablename;
```

**注意事项**

-   `DISTINCT` 关键字可选，用于去除重复记录

**使用表达式对查询的列进行运算**

```sql
SELECT *|{column1|expr1, colum2|expr2, ...} FROM tablename;
```

**使用 AS 关键字为查询的列起别名**

```sql
SELECT column1 AS 别名 from tablename;
```

