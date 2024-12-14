tags:: [[环境变量]]
---

- ## 查看环境变量
	- ``` sh
	  # 查看指定名称的环境变量
	  echo $环境变量名称
	  printenv 环境变量名称
	  
	  # 查看所有环境变量
	  printenv
	  ```
- ## 环境变量分类
	- ### 按生命周期分
		- 临时环境变量
		  logseq.order-list-type:: number
			- 即，执行 `export 环境变量名称=环境变量值` 设置的当前终端会话的环境变量；
			- 该环境变量只在当前会话有效，其他会话读取不到此环境变量。
		- 永久环境变量
		  logseq.order-list-type:: number
			- 存放在环境变量配置文件中的环境变量。
			- 永久有效。
	- ### 按作用域分
		- 系统环境变量/全局环境变量：对所有用户都有效的环境变量。
		  logseq.order-list-type:: number
		- 用户环境变量：只对特定用户有效的环境变量。
		  logseq.order-list-type:: number
- ## macOS 环境变量配置文件
	- ### 使用 bash 时配置文件加载顺序
		- ``` sh
		  # ===========  系统级环境变量配置
		  # 全局环境变量配置
		  /etc/profile
		  
		  # 指定 shell 的环境变量配置
		  /etc/bashrc
		  
		  # macOS 特有的环境变量配置，用于配置 PATH 变量
		  /etc/paths
		  # paths.d 目录下的每一个文件的每一行都会被作为 PATH 变量的一个目录
		  /etc/paths.d/xxx
		  
		  # =========== 用户级环境变量配置 (不同用户使用独立的配置文件)
		  # 以下文件如果不存在，则往下查找; 如果存在，则忽略后面的文件
		  ~/.bash_profile
		  ~/.bash_login
		  ~/.profile
		  ```
	- ### 使用 zsh 时配置文件加载顺序
		- 参见 [[zsh]] 的 **Startup Files**
- ## Linux 环境变量配置文件
	- ### 使用 bash 时配置文件加载顺序
		- ``` sh
		  # ===========  系统级环境变量配置
		  # 全局环境变量配置
		  /etc/profile
		  
		  # 指定 shell 的环境变量配置
		  /etc/bashrc
		  
		  # =========== 用户级环境变量配置 (不同用户使用独立的配置文件)
		  ~/.bashrc
		  ~/.bash_login
		  ~/.profile
		  ```
		-
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