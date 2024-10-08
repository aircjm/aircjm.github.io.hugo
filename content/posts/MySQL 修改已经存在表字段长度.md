---
cards-deck: MySQL
createAt: 2022-04-22 13:54:15
draft: false
publish: true
title: "MySQL \u4FEE\u6539\u5DF2\u7ECF\u5B58\u5728\u8868\u5B57\u6BB5\u957F\u5EA6"
updateAt: 2022-04-22 13:54:15
---

tags:  #mysql 



[[mysql alter table]] 是修改表结构的语句。


```sql
ALTER TABLE `workorder_record`   
  CHANGE `deal_man` `deal_man` VARCHAR(255) CHARSET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT ''  NOT NULL   COMMENT '处理人';
```
具体语法为：
```sql
| CHANGE [COLUMN] _old_col_name_ _new_col_name_ _column_definition_ [FIRST | AFTER _col_name_]
```


link: https://dev.mysql.com/doc/refman/8.0/en/alter-table.html