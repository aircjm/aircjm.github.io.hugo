---
cards-deck: Default
createAt: 2022-03-03 13:23
draft: false
publish: true
title: "\u8E29\u5751\u65E5\u8BB0-\u5904\u7406pg\u7684\u81EA\u589E\u957F\u4E3B\u952E\
  \u6570\u636E\u5F02\u5E38\u95EE\u9898"
updateAt: 2022-03-03 13:23:22
---
tags:  #postgresql #踩坑

备份迁移完 postgresql的表之后，插入数据的时候发现了报错。
```txt
DETAIL:  Key (id)=(2) already exists.
```
这个实际上是由于自增长的id重复出现导致的，我们要刷新下自增长的id的值。
```sql
SELECT MAX(id) FROM duties;
```
![Pasted_image_20220303133529.png](/images/Pasted_image_20220303133529.png)

可以看到最大的id已经是80242了，但是自增长的id还是2，这个就导致了这个问题  
可以通过设置id自增长来解决这个问题。
```sql
select setval('tablename_id_seq', max(id)) from tablename;
```

实际例子：
```sql
SELECT setval('duties_id_seq', (SELECT MAX(id) FROM duties));
```

tablename_id_seq取得并不是id，取得是nextval的参数
![Pasted_image_20220303132816.png](/images/Pasted_image_20220303132816.png)



[[postgist创建表]]