tags:: #[[GNU Coreutils]], #GNU

- ---
-
- ---
- ## 查看系统信息
	- 执行 `uanme -a`，可得到如下类似内容：
	- ``` bash
	  uanme -a
	  Linux raspberrypi 5.15.61-v7l+ #1579 SMP Fri Aug 26 11:13:03 BST 2022 armv7l GNU/Linux
	  ```
	- ### 查看系统位数
		- `getconf LONG_BIT`
		- ``` bash
		  getconf LONG_BIT
		  32
		  ```
	-