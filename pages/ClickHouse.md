tags:: [[RDBMS]]
---

- ==子目录==
	- [[ClickHouse/Engine]]
	-
-
- ## 命令速查
	- ### 数据库参数
		- #### 查询SQL最大长度
			- ``` sql
			  -- 单位：byte
			  SELECT name, value
			  FROM system.settings
			  WHERE name LIKE 'max_query_size%' OR name LIKE 'max_query_size%';
			  ```
			-
-