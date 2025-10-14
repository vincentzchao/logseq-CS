tags:: [[Flutter]]
---

- ## 安装必备软件
	- [[Git 安装与配置]]
	  logseq.order-list-type:: number
		- macOS 建议执行 `xcode-select --install` 安装 Git .
	- [[VS Code 安装与配置]]
	  logseq.order-list-type:: number
	- 安装 [[VS Code Extension - Flutter]]
	  logseq.order-list-type:: number
- ## 安装并配置 Flutter
	- ### 下载并解压
		- 下载地址: [Flutter SDK archive](https://docs.flutter.dev/install/archive), 下载 `Stable Channel` 的版本.
		- ==注意, Flutter SDK 内是包含 Dart 的.==
	- ### 添加 bin 目录环境变量
		- 将 `/Users/vincent/ZHU/dev/sdk/flutter-3.24.4/bin` 加到 `PATH` 环境变量。
	- ### 添加镜像环境变量
		- 添加如下两个环境变量 (选一个镜像即可) ：
			- ``` zsh
			  # CFUG 镜像
			  export PUB_HOSTED_URL="https://pub.flutter-io.cn"
			  export FLUTTER_STORAGE_BASE_URL="https://storage.flutter-io.cn"
			  
			  # 上海交通大学 镜像
			  # https://github.com/sjtug/mirror-requests
			  export PUB_HOSTED_URL="https://mirror.sjtu.edu.cn/dart-pub"
			  export FLUTTER_STORAGE_BASE_URL="https://mirror.sjtu.edu.cn"
			  
			  # 清华大学 镜像
			  # https://tuna.moe/
			  export PUB_HOSTED_URL="https://mirrors.tuna.tsinghua.edu.cn/dart-pub"
			  export FLUTTER_STORAGE_BASE_URL="https://mirrors.tuna.tsinghua.edu.cn/flutter"
			  ```
- ## 配置 iOS 开发
	- ### 安装 Xcode
		- 参照 [[Xcode 安装与配置]]
		  logseq.order-list-type:: number
		- 配置命令行工具使用已安装的 Xcode 版本
		  logseq.order-list-type:: number
			- `sudo sh -c 'xcode-select -s /Applications/Xcode.app/Contents/Developer && xcodebuild -runFirstLaunch'`
		- 签署 Xcode 许可证协议
		  logseq.order-list-type:: number
			- 执行 `sudo xcodebuild -license` 输入 `agree`
	- ### 安装 CocoaPods
		- 参见 [[CocoaPods 安装与配置]]
- ## 验证安装
	- 执行 `flutter doctor` .
	  logseq.order-list-type:: number
		- ``` zsh
		  ➜  logs flutter doctor
		  Doctor summary (to see all details, run flutter doctor -v):
		  [✓] Flutter (Channel stable, 3.24.4, on macOS 15.5 24F74 darwin-arm64, locale en-US)
		  [✓] Android toolchain - develop for Android devices (Android SDK version 35.0.1)
		  [!] Xcode - develop for iOS and macOS (Xcode 16.4)
		      ✗ CocoaPods not installed.
		          CocoaPods is a package manager for iOS or macOS platform code.
		          Without CocoaPods, plugins will not work on iOS or macOS.
		          For more info, see https://flutter.dev/to/platform-plugins
		        For installation instructions, see https://guides.cocoapods.org/using/getting-started.html#installation
		  [✓] Chrome - develop for the web
		  [✓] Android Studio (version 2024.3)
		  [✓] IntelliJ IDEA Ultimate Edition (version 2024.3.4.1)
		  [✓] VS Code (version 1.100.2)
		  [✓] Connected device (4 available)
		  [✓] Network resources
		  ```
	- 按照提示处理问题.
	  logseq.order-list-type:: number
-
- ## 参考
	- [Using Flutter in China](https://docs.flutter.dev/community/china)
	  logseq.order-list-type:: number
	- [Flutter  Docs - Quick Start](https://docs.flutter.dev/get-started/quick)
	  logseq.order-list-type:: number
	- [开始在 macOS 上构建 Flutter iOS 应用](https://docs.flutter.cn/get-started/install/macos/mobile-ios)
	  logseq.order-list-type:: number
-