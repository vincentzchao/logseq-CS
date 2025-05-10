tags:: [[Homebrew]]
---

- ## Tap 安装目录
	- `$(brew --prefix)/Library/Taps`
	- ``` zsh
	  ➜  ~ cd $(brew --prefix)/Library/Taps
	  ➜  Taps git:(stable) ll
	  total 0
	  drwxr-xr-x  3 vincent  admin    96B Apr 30  2023 microsoft
	  drwxr-xr-x@ 3 vincent  admin    96B May 10 17:47 redis
	  ➜  Taps git:(stable) tree -L 3
	  .
	  ├── microsoft
	  │   └── homebrew-git
	  │       ├── Casks
	  │       ├── LICENSE
	  │       ├── NOTICE
	  │       ├── README.md
	  │       ├── SECURITY.md
	  │       └── tap_migrations.json
	  └── redis
	      └── homebrew-redis
	          ├── Casks
	          ├── README.md
	          ├── configs
	          └── scripts
	  ```
- ## `tap [options] [user/repo] [URL]` 命令
	- 参见: [Manpage - brew tap](https://docs.brew.sh/Manpage#tap-options-userrepo-url)
	- ### 列出所有已安装的 tap
		- `brew tap`
		- ``` zsh
		  ➜  Taps git:(stable) brew tap
		  microsoft/git
		  redis/redis
		  ```
	- ### 从代码仓库安装 tap
		- `brew tap user/repo https://github.com/user/homebrew-repo` 等价于 `brew tap user/repo`
			- 后者会默认从 Github 的 `https://github.com/user/homebrew-repo` 地址安装 tap .
			- 前者虽然多了一个参数, 但是可以从 Github 以外的仓库安装 tap , 同时也可以使用除了 HTTPS 以外的协议, 比如 SSH、git、HTTP、FTP(S)、rsync .
		-
		-
-