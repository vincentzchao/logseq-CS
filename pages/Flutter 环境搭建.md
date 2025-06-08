tags:: [[Flutter]]
---

- ## 安装并配置 Flutter
	- ### 下载并解压
		- [Flutter SDK 归档列表](https://docs.flutter.cn/release/archive?tab=macos)
	- ### 添加 bin 目录环境变量
		- 将 `/Users/vincent/ZHU/dev/sdk/flutter-3.24.4/bin` 加到 `PATH` 环境变量。
	- ### 添加镜像环境变量
		- 添加如下两个环境变量：
			- ``` zsh
			  # CFUG 镜像
			  export PUB_HOSTED_URL="https://pub.flutter-io.cn"
			  export FLUTTER_STORAGE_BASE_URL="https://storage.flutter-io.cn"
			  
			  # 上海交通大学 镜像
			  export PUB_HOSTED_URL="https://mirror.sjtu.edu.cn/dart-pub"
			  export FLUTTER_STORAGE_BASE_URL="https://mirror.sjtu.edu.cn"
			  
			  # 清华大学 镜像
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
	- [在中国网络环境下使用 Flutter](https://docs.flutter.cn/community/china)
	  logseq.order-list-type:: number
	- [开始在 macOS 上构建 Flutter iOS 应用](https://docs.flutter.cn/get-started/install/macos/mobile-ios)
	  logseq.order-list-type:: number