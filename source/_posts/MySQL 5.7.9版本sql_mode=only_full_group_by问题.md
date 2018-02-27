title: MySQL 5.7.9 sql_mode=only_full_group_by
abbrlink: 36628
tags:
  - mysql
categories: []
date: 2018-02-10 13:02:00
---

---
# MySQL 5.7.9版本sql_mode=only_full_group_by问题

用到GROUP BY 语句查询时com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException: Expression #2 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'col_user_6.a.START_TIME' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by错误

解决方法 ：执行SET GLOBAL sql_mode = ''; 把sql_mode 改成非only_full_group_by模式。验证是否生效 SELECT @@GLOBAL.sql_mode 或 SELECT @@sql_mode


SET sql_mode ='STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';
