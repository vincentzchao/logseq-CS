tags:: [[Bash]], [[环境变量]]
---

- 先参阅：[[Unix-like 环境变量]]
- ## Bash Startup Files
	- 参见: [Bash manual -  Bash Startup Files](https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html)
	- 涉及的文件：
		- ``` bash
		  # ===========  系统级配置文件 (/etc 目录下的都是系统级)
		  # 系统环境变量配置 
		  /etc/profile
		  /etc/profile.d
		  
		  # 指定 shell 的系统环境变量配置
		  /etc/bashrc
		  
		  # =========== 用户级配置文件 (不同用户使用独立的配置文件)
		  ~/.bash_profile
		  ~/.bash_login
		  
		  ~/.profile
		  
		  ~/.bashrc
		  
		  ~/.bash_logout
		  ```
	- ==注意:==
		- Startup Files 文件中的所谓环境变量配置，并非静态的文本配置，而是执行 `export` , `env` 等命令。
		  logseq.order-list-type:: number
			- 所以，后面执行命令设置的环境变量，肯定会覆盖前面设置的名称相同的环境变量。
			  logseq.order-list-type:: number
			- 所以，程序并非从文件中读取环境变量，而是在程序启动前，先执行 Startup Files 中的命令，将环境变量放到内存中，供之后读取；因此，每个进程都有环境变量副本，程序中修改环境变量，并不影响其他进程。
			  logseq.order-list-type:: number
		- 任何子进程，都会继承其父进程设置的环境变量，且子进程的修改不会影响其父进程的环境变量值。
		  logseq.order-list-type:: number
			- Shell 也一样，任何模式的子 Shell ，都会继承其父 Shell 设置的环境变量，且子 Shell 的修改不会影响其父 Shell 的环境变量值。
	- 下文中的 Login、Interactive 等模式，参见 [[Unix-like Shell]]；
	- ### 进入 Bash 的 Login Shell (无论是否为 Interactive)
		- 读取并执行 `/etc/profile` 文件中的命令。
		  logseq.order-list-type:: number
			- **Linux 中** ：
				- 一般来说, `/etc/profile` 中会读取并执行 `/etc/profile.d` 目录下的所有 `.sh` 文件中的命令。
				- ==貌似，在有些系统中, `/etc/profile` 中也会读取并执行  `/etc/bashrc` 文件中的命令。==
					- ``` bash
					  # 阿里云服务器 `/etc/profile` 文件末尾
					  if [ -n "${BASH_VERSION-}" ] ; then
					          if [ -f /etc/bashrc ] ; then
					                  # Bash login shells run only /etc/profile
					                  # Bash non-login shells run only /etc/bashrc
					                  # Check for double sourcing is done in /etc/bashrc.
					                  . /etc/bashrc
					         fi
					  fi
					  ```
			- **macOS 中** ：一般来说，`/etc/profile`
		- 按 `~/.bash_profile` , `~/.bash_login` , `~/.profile` 的顺序，选择 **第一个存在且可读** 的文件，读取并执行其中的内容。
		  logseq.order-list-type:: number
			- 一般来说, `~/.bash_profile` 中会读取并执行 `~/.bashrc` 文件中的命令。
			  id:: 675e8ab6-c476-4b17-81ff-4b7c3984311b
				- 一般来说, `~/.bashrc` 中会读取并执行 `/etc/bashrc` 文件中的命令。
	- ### 退出 Bash 的 Login Shell (无论是否为 Interactive)
		- 读取并执行 `~/.bash_logout` 文件中的命令。
	- ### 进入 Bash 的 Interactive Non-login Shell
		- 读取并执行 `~/.bashrc` 文件中的命令。
			- 一般来说, `~/.bashrc` 中会读取并执行 `/etc/bashrc` 文件中的命令。
	- ### 进入 Bash 的 Non-interactive Non-login Shell
		- 读取并执行以 `BASH_ENV` 环境变量的值为名称的文件中的命令。
			- 相当于执行了如下脚本：
			- ```bash
			  if [ -n "$BASH_ENV" ]; then . "$BASH_ENV"; fi
			  ```
	- ### 退出 Bash 的 Non-login Shell (无论是否为 Interactive)
		- 无相关 Startup Files 。
- ## 最佳实践
	- Linux 系统更新时, `/etc` 目录下的内容会被更新。
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number
- ## 参考
	- [macOS/Linux 环境变量设置](https://zhuanlan.zhihu.com/p/25976099)
	  logseq.order-list-type:: number
	- [关于终端、Shell、Bash以及环境变量那点事](https://www.ethanzhang.xyz/2024/04/25/%E5%85%B3%E4%BA%8E%E7%BB%88%E7%AB%AFShellBash%E4%BB%A5%E5%8F%8A%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%E9%82%A3%E7%82%B9%E4%BA%8B/)
	  logseq.order-list-type:: number
-