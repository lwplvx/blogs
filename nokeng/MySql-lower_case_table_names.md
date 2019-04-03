# MySql 大小写敏感修改
lower_case_table_names
表示表名是否大小写敏感，可以修改。

lower_case_table_names = 0时，mysql会根据表名直接操作，大小写敏感。 
lower_case_table_names = 1时，mysql会先把表名转为小写，再执行操作。 

设置lower_case_table_names的值

进入docker的MySQL容器，编辑/etc/mysql/mysql.conf.d/mysqld.cnf文件，在[mysqld]下添加如下：

[mysqld] 
lower_case_table_names=1

保存，退出容器；

执行sudo docker restart MySQL-xxx ，重启MySQL即可查看： 

## docker 中不能用vim编辑文件

更新来源
  apt-get update

安装vim
  apt-get install -y vim
