-
- # Redis命令
	- ## 批量删除Key
		- ```sh
		  redis-cli -h IP -p PORT -a PASSWORD -n DBIndex keys 'key*' | xargs redis-cli -h IP -p PORT -a PASSWORD -n DBIndex del
		  ```