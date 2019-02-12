# MSSQL 迁移至 Mysql 记录
*此文章介绍的方法 不好用，改用下面 Navicat 传输的方式尝试*

* 参考：[https://www.cnblogs.com/gaizai/p/3237907.html](https://www.cnblogs.com/gaizai/p/3237907.html)

## 遇到 MySQL 链接 1512 问题
### 由于是新安装的 MySQL 8.0 
  
* 用 Navicat（最新版）连接
    
      ALTER USER 'root'@'localhost' IDENTIFIED BY 'password' PASSWORD EXPIRE NEVER; #修改加密规则 
      # password 改成实际密码
      ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'; #更新一下用户的密码
      FLUSH PRIVILEGES; #刷新权限
    
* 参考：[https://blog.csdn.net/qq_36068954/article/details/80175755](https://blog.csdn.net/qq_36068954/article/details/80175755)


# Navicat 传输的方式尝试
##  注意注意：Mysql 数据库创建的时候选择正确的 字符集 和 字符序
*数据库创建和数据传输已经成功*

* 添加目标Mysql 链接
* 添加源 MSSQL 数据库链接
* 选择 Tool-> Data Tranfer ,然后选择源，目标（可以指定新的数据库名称）
* 已经成功，等我验证效果……（程序 EF 需要切换到 MySQL）

# Azure Database for MySQL 服务器 相关问题

1) 创建数据库服务后，首先在控制台修改字符集为：utf8mb4
2) 然后创建数据库（character set: utf8mb4 ,collation: utf8mb4_general_ci）
3) 用 navicat Tools->Data Transfer 重新同步数据
4) 此步骤之后的方法忽略

* 默认字符集/字符序（数据库，数据表）
* 手动更改了数据库字符集/字符序
* 利用语句生成了修改所有表字符集的语句，语句如下
    
    SELECT TABLE_NAME,CONCAT('ALTER TABLE  ',TABLE_NAME,' DEFAULT CHARACTER SET ',a.DEFAULT_CHARACTER_SET_NAME,' COLLATE ',a.DEFAULT_COLLATION_NAME,';') executeSQL FROM information_schema.SCHEMATA a,information_schema.TABLES b
WHERE a.SCHEMA_NAME=b.TABLE_SCHEMA
AND a.DEFAULT_COLLATION_NAME!=b.TABLE_COLLATION
AND b.TABLE_SCHEMA='zhdj71' 
  
  手动执行生成的语句

* 然后再用 navicat Tools->Data Transfer 重新同步数据

# 视图 
* 根据 MSSQl 视图创建语句手动修改为适用于 mysql 的语句（自己转换时保留脚本）


