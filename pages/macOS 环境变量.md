alias:: [[macOS environment variable]]
tags:: [[macOS]], [[环境变量]], [[Unix-like 环境变量]] 
---

- 先参阅：[[Unix-like 环境变量]]
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
-
- /etc 目录下系统环境变量
- $HOME 目录下用户环境变量
-
- ---
- ## 参考
	- [macOS/Linux 环境变量设置](https://zhuanlan.zhihu.com/p/25976099)
	  logseq.order-list-type:: number
-