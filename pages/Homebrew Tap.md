tags:: [[Homebrew]]
---

- ## homebrew-services
	- 参见: [Homebrew Manpage - Services Subcommand](https://docs.brew.sh/Manpage#services-subcommand)
	- 用于管理 Homebrew 安装的服务。
		- 也具有设置开机自启的功能。
	- ``` zsh
	  # 清理旧的安装和缓存
	  brew cleanup
	  brew untap homebrew/services
	  # 安装 homebrew/services
	  brew tap homebrew/services
	  
	  # 列出当前所有服务的状态
	  brew services list
	  
	  # 启动某个服务
	  brew services start <服务名>
	  # 停止某个服务
	  brew services stop <服务名>
	  # 重启某个服务
	  brew services restart <服务名>
	  # 移除系统服务，但保留软件本身
	  brew services remove <服务名>
	  ```
-
-