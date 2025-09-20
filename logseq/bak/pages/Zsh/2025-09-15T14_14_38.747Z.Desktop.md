tags:: [[Unix Shell]]
---

- ==子目录==
	- [[Oh My Zsh]]
	- [[zsh 缩短用户名和路径的配置]]
- ---
- ## 官方资料
	- [官网](https://zsh.sourceforge.io/)
- ## 优点与缺点
	- 如果要编写脚本，建议不要选 Zsh ，因为它不兼容 [[Bash]] ，可移植性不好
- ## Startup Files
	- 参考:  [Chapter 2: What to put in your startup files](https://zsh.sourceforge.io/Guide/zshguide02.html#l6)
	- `/etc` 开头的为所有用户都会生效的配置; `~` 为只有当前用户会生效的配置。
	- ``` zsh
	  /etc/zshenv
	  	Always run for every zsh.
	  /etc/zprofile
	  	Run for login shells.
	  /etc/zshrc
	  	Run for interactive shells.
	  /etc/zlogin
	  	Run for login shells.
	      
	  ~/.zshenv
	  	Usually run for every zsh (see below).
	  ~/.zprofile
	  	Run for login shells.
	  ~/.zshrc
	  	Run for interactive shells.
	  ~/.zlogin
	  	Run for login shells.
	  ```
	-
-