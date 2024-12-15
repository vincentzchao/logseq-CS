tags:: [[环境变量]]
---

- ## 查看环境变量
	- ``` bash
	  # 查看指定名称的环境变量
	  echo $环境变量名称
	  printenv 环境变量名称
	  
	  # 查看所有环境变量
	  printenv
	  ```
- ## 移除环境变量
	- ``` bash
	  # 移除指定名称的环境变量
	  unset 环境变量名称
	  ```
- ## 环境变量分类
	- ### 按生命周期分
		- 临时环境变量
		  logseq.order-list-type:: number
			- 即，执行 `export 环境变量名称=环境变量值` 设置的当前终端会话的环境变量；
			- 该环境变量只在当前会话有效，其他会话读取不到此环境变量。
		- 永久环境变量
		  logseq.order-list-type:: number
			- 在环境变量配置文件中的配置的环境变量。
			- 永久有效。
	- ### 按作用域分
		- 系统环境变量/全局环境变量：对所有用户都有效的环境变量。
		  logseq.order-list-type:: number
		- 用户环境变量：只对特定用户有效的环境变量。
		  logseq.order-list-type:: number
- ## 重载环境变脸配置文件
	- `source 文件路径`
		- 作用是，在当前 Shell 中将文件中的命令执行一遍。
	- `source 文件路径` 等价于 `. 文件路径`
	- `source 文件路径` 与 `bash 文件路径` / `zsh 文件路径` 等命令的区别是：
		- 前者，是在当前 Shell 中执行。
		- 后者，是在一个子 Shell 中执行，只在子 Shell 中生效；执行完成后，子 Shell 自动关闭。
- ## PATH 变量
	- ### 作用
		- Shell 会在 `PATH` 变量配置的路径中，寻找可执行文件。
	- ### 增加路径
		- ``` sh
		  # 在配置文件中添加如下格式的内容
		  export PATH="你要添加的路径:$PATH"
		  ```
	- ### 查看命令的路径
		- ``` sh
		  which 你的命令 
		  whereis 你的命令
		  ```
- ## 参考
	- [macOS/Linux 环境变量设置](https://zhuanlan.zhihu.com/p/25976099)
	  logseq.order-list-type:: number
	- [关于终端、Shell、Bash以及环境变量那点事](https://www.ethanzhang.xyz/2024/04/25/%E5%85%B3%E4%BA%8E%E7%BB%88%E7%AB%AFShellBash%E4%BB%A5%E5%8F%8A%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%82%A3%E7%82%B9%E4%BA%8B/)
	  logseq.order-list-type:: number