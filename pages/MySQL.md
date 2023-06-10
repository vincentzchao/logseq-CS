tags:: #[[RDBMS]]

- ---
-
- ## 命令速查
	- ### 数据库参数相关
		- ``` sql
		  -- 查询数据版本
		  select version();
		  ```
	- ### SQL最大大小
		- ``` sql
		  -- 查询MySQL支持的最大SQL字符串大小，单位为 Byte
		  select @@max_allowed_packet;
		  ```
-
-