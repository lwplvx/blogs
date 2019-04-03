# MySql 大小写敏感修改
lower_case_table_names
表示表名是否大小写敏感，可以修改。

lower_case_table_names = 0时，mysql会根据表名直接操作，大小写敏感。 
lower_case_table_names = 1时，mysql会先把表名转为小写，再执行操作。 

设置lower_case_table_names的值

打开my.cnf文件，加入以下语句后重启。
  
  lower_case_table_names = 0 或 lower_case_table_names = 1

## docker 中不能用vim编辑文件

更新来源
  apt-get update

安装vim
  apt-get install -y vim
