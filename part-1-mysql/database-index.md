# 数据库索引

### 什么是索引?

* 索引是一种数据结构,可以以一个或者多个字段的值为输入,并能"快速地"找出具有该值的记录.
* 索引是一种特殊的文件\(InnoDB 数据表上的索引是表空间的一个组成部分\),他们所包含着对数据表里所有记录的引用指针
* 索引是一个文件,需要占用物理空间

### 索引的作用是什么?

* 索引使我们自只需查看所有可能记录中的一小部分就能够找到所需记录

### 索引有哪些优点？

#### 优点：

* 可以大大加快数据的检索速度，这也是创建索引的最主要原因
* 通过索引，可以在查询过程中使用优化隐藏器，提高系统的性能

#### 缺点：

* 时间：
  * 创建索引和维护索引需要耗费时间，具体的，对表的数据进行增加、删除、修改的时候，索引需要动态的进行维护，会降低  增、删、改、查的执行效率
* 空间：
  * 索引需要占用物理空间

### 索引的使用场景有哪些？

* **where**

![](../.gitbook/assets/b2ca1b2357d2739db8ff385979b5f96.png)

               上图中，根据 id 查询记录，因为id字段仅建立了主键索引，因此此SQL执行可选的索引只有主键索引，如果有多个，最终会选一个较优的作为检索的依据

```text
-- 增加一个没有建立索引的字段
alter table innodb1 add sex char(1);

-- 按sex检索时可选的索引为null
EXPLAIN SELECT * from innodb1 where sex='男';
```

![](../.gitbook/assets/456cc8373554de5fe1686fc5e57ffc6.png)

{% hint style="info" %}
可以尝试在一个字段未建立索引时，根据该字段查询的效率，然后对该字段建立索引（alter table 表名 add index\(字段名\)），同样的SQL执行的效率，这样操作查询效率会有明显的提升（数据量越大越明显）。
{% endhint %}

* **order by**
  * \*\*\*\*
* **join**

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

\*\*\*\*

**参考:** 

1. \*\*\*\*[**https://blog.csdn.net/ThinkWon/article/details/104778621**](https://blog.csdn.net/ThinkWon/article/details/104778621)\*\*\*\*
2. \*\*\*\*[**https://juejin.im/post/6844903569632526343**](https://juejin.im/post/6844903569632526343)\*\*\*\*
3. \*\*\*\*[**https://github.com/CyC2018/CS-Notes/blob/master/notes/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%B3%BB%E7%BB%9F%E5%8E%9F%E7%90%86.md\#%E4%B8%8D%E5%8F%AF%E9%87%8D%E5%A4%8D%E8%AF%BB**](https://github.com/CyC2018/CS-Notes/blob/master/notes/%E6%95%B0%E6%8D%AE%E5%BA%93%E7%B3%BB%E7%BB%9F%E5%8E%9F%E7%90%86.md#%E4%B8%8D%E5%8F%AF%E9%87%8D%E5%A4%8D%E8%AF%BB)\*\*\*\*
4. \*\*\*\*[**https://github.com/wolverinn/Waking-Up/blob/master/Database.md**](https://github.com/wolverinn/Waking-Up/blob/master/Database.md)\*\*\*\*





