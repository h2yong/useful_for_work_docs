> 先来看数据表的结构如下：

```shell
+------+------+
| name | val  |
+------+------+
|  a   |  2   |
|  a   |  1   |
|  a   |  3   |
|  b   |  5   |
|  b   |  3   |
|  b   |  2   |
|  b   |  4   |
|  b   |  1   |
+------+------+
```

假定使用以下SQL进行初始化：

```sql
create table h2yong(name varchar(10),val int);
insert into h2yong values('a', 2);
insert into h2yong values('a', 1);
insert into h2yong values('a', 3);
insert into h2yong values('b', 5);
insert into h2yong values('b', 3);
insert into h2yong values('b', 2);
insert into h2yong values('b', 4);
insert into h2yong values('b', 1);
```

## 按name分组取val最大的值所在行的数据

```sql
-- 方法1：
select a.* from h2yong a where val =
(select max(val) from h2yong where name = a.name)
order by a.name
-- 方法2：
select a.* from h2yong a where not exists
(select 1 from h2yong where name = a.name and val > a.val)
-- 方法3：
select a.* from h2yong a,(select name,max(val) val from h2yong group by name) b
where a.name = b.name and a.val = b.val
order by a.name
-- 方法4：
select a.* from h2yong a inner join
(select name , max(val) val from h2yong group by name) b
on a.name = b.name and a.val = b.val order by a.name
-- 方法5：
select a.* from h2yong a
where 1 > (select count(*) from h2yong where name = a.name and val > a.val )
order by a.name
```

> 结果如下：

```shell
+------+------+
| name | val  |
+------+------+
|  a   | 3    |
|  b   | 5    |
+------+------+
```

## 按name分组取val最小的值所在行的数据

```sql
-- 方法1：
select a.* from h2yong a
where val = (select min(val) from h2yong where name = a.name)
order by a.name
-- 方法2：
select a.* from h2yong a
where not exists(select 1 from h2yong where name = a.name and val < a.val)
-- 方法3：
select a.* from h2yong a,(select name,min(val) val from h2yong group by name) b
where a.name = b.name and a.val = b.val order by a.name
-- 方法4：
select a.* from h2yong a
inner join (select name , min(val) val from h2yong group by name) b
on a.name = b.name and a.val = b.val order by a.name
-- 方法5
select a.* from h2yong a
where 1 > (select count(*) from h2yong where name = a.name and val < a.val)
order by a.name
```

> 结果如下：

```shell
+------+------+
| name | val  |
+------+------+
|  a   | 1    |
|  b   | 1    |
+------+------+
```

## 按name分组取第一次出现的行所在的数据

```sql
select a.* from h2yong a
where val = (select val from h2yong where name = a.name LIMIT 1)
order by a.name
```

> 结果如下：

```shell
+------+------+
| name | val  |
+------+------+
|  a   | 2    |
|  b   | 5    |
+------+------+
```

## 按name分组随机取一条数据

```sql
SELECT * FROM (SELECT * FROM h2yong ORDER BY RAND()) as a GROUP BY a.name
```

> 结果如下：

```shell
+------+------+
| name | val  |
+------+------+
|  a   | 3    |
|  b   | 4    |
+------+------+
```

## 按name分组取最小的两个(N个)val

```sql
-- 方法1：
select a.* from h2yong a
where 2 > (select count(*) from h2yong where name = a.name and val < a.val )
order by a.name,a.val
-- 方法2：
select a.* from h2yong a where exists
(select count(*) from h2yong where name = a.name and val < a.val having Count(*) < 2)
order by a.name
```

> 结果如下：

```shell
+------+------+
| name | val  |
+------+------+
|  a   | 1    |
|  a   | 2    |
|  b   | 1    |
|  b   | 2    |
+------+------+
```

## 按name分组取最大的两个(N个)val

```sql
-- 方法1：
select a.* from h2yong a where 2 >
(select count(*) from h2yong where name = a.name and val > a.val )
order by a.name,a.val
-- 方法2：
select a.* from h2yong a where exists
(select count(*) from h2yong where name = a.name and val > a.val having Count(*) < 2)
order by a.name
```

> 结果如下：

```shell
+------+------+
| name | val  |
+------+------+
|  a   | 2    |
|  a   | 3    |
|  b   | 4    |
|  b   | 5    |
+------+------+
```
