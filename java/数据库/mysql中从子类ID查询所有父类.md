# mysql中从子类ID查询所有父类（做无限分类经常用到）

> 先来看数据表的结构如下：

```shell
+------+----------+-----------+
| id   | name     | parent_id |
+------+----------+-----------|
| 1    | Home     |   0       |
| 2    | About    |   1       |
| 3    | Contact  |   1       |
| 4    | Legal    |   2       |
| 5    | Privacy  |   4       |
| 6    | Products |   1       |
| 7    | Support  |   1       |
+------+----------+-----------+
```

假定使用以下SQL进行初始化：

```sql
create table h2yong(id int not null primary key auto_increment, name varchar(10),parent_id int);
insert into h2yong values('a', 2);
insert into h2yong values('a', 1);
insert into h2yong values('a', 3);
insert into h2yong values('b', 5);
insert into h2yong values('b', 3);
insert into h2yong values('b', 2);
insert into h2yong values('b', 4);
insert into h2yong values('b', 1);
```

> 我要的要求是根据一个分类ID（这个分类ID可能是一个子分类），得到所有的父分类

_由于mysql 不支持类似 oracle with ...connect的 递归查询语法，故采用以下SQL完成该功能：_

```sql
SELECT T2.id, T2.name
FROM (
    SELECT
        @r AS _id,
        (SELECT @r := parent_id FROM h2yong WHERE id = _id) AS parent_id,
        @l := @l + 1 AS lvl
    FROM
        (SELECT @r := 5, @l := 0) vars,
        h2yong h
    WHERE @r <> 0) T1
JOIN h2yong T2
ON T1._id = T2.id
ORDER BY T1.lvl DESC
```

代码 `@r := 5` 表示查询id为5的所有父类。

> 结果如下：

```shell
+------+----------+
| id   | name     |
+------+----------+
|  1   |  Home    |
|  2   |  About   |
|  4   |  Legal   |
|  5   |  Privacy |
+------+----------+
```
