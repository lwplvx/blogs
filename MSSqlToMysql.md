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
*数据库创建和数据传输已经成功*

* 添加目标Mysql 链接
* 添加源 MSSQL 数据库链接
* 选择 Tool-> Data Tranfer ,然后选择源，目标（可以指定新的数据库名称）
* 已经成功，等我验证效果……（程序 EF 需要切换到 MySQL）
