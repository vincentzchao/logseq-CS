tags:: [[Dart]]
---

- ## Dart 版本介绍
	- 有如下几类版本：
		- Stable channel 版本
		  logseq.order-list-type:: number
			- 版本号格式: `x.y.z `
				- `x` : major version
				- `y` : minor version
				- `z` : patch version
			- 安装渠道: [Install the Dart SDK](https://dart.dev/get-dart#install)
		- Beta channel 版本
		  logseq.order-list-type:: number
			- 版本号格式: `x.y.z-a.b.beta`
				- `x` : major version
				- `y` : minor version
				- `z` : patch version
				- `a` : pre-release version
				- `b` : pre-release patch version
			- 安装渠道: [Dart SDK archive](https://dart.dev/get-dart/archive)
		- Dev channel 版本
		  logseq.order-list-type:: number
			- 版本号格式: `x.y.z-a.b.dev`
				- `x` : major version
				- `y` : minor version
				- `z` : patch version
				- `a` : development version
				- `b` : development patch version
			- 安装渠道: [Dart SDK archive](https://dart.dev/get-dart/archive)
- ## 安装 Dart
	- ``` zsh
	  brew tap dart-lang/dart
	  brew install dart
	  
	  # 安装指定版本
	  brew install dart@3.1
	  
	  # 查看已安装的 Dart
	  brew info dart
	  ```
- ## 更新 Dart
	- ``` zsh
	  brew upgrade dart
	  ```
- ## 切换 Dart 版本
	- ``` zsh
	  brew unlink dart@<old> \
	    && brew unlink dart@<new> \
	    && brew link dart@<new>
	  ```
- ## 卸载 Dart
	- ``` zsh
	  brew uninstall dart
	  
	  # 删除 Dart 配置文件
	  rm -rf  ~/.dart*
	  ```
-
- ## 参考
	- [Dart - Get the Dart SDK](https://dart.dev/get-dart)
	  logseq.order-list-type:: number
-