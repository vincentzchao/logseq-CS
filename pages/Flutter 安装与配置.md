tags:: [[Flutter]]
---

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
- ## 搭建 Flutter 开发环境
	- ### 安装 Git
		- [[Git 安装与配置]]
			- macOS 建议执行 `xcode-select --install` 安装 Git .
	- ### 使用 VS Code 开发
		- [[VS Code 安装与配置]]
		  logseq.order-list-type:: number
		- 安装 [[VS Code Extension - Flutter]]
		  logseq.order-list-type:: number
			- 具体使用, 参见: [[VS Code Extension - Flutter]]
- ## 搭建各目标平台开发环境
	- ### 搭建 Android 开发环境
		- 参见: [[使用 Android Studio 或 Intellij IDEA 开发 Flutter]]
	- ### 搭建 iOS 开发环境
		- #### 安装 Xcode
			- 参照 [[Xcode 安装与配置]]
			  logseq.order-list-type:: number
			- 配置命令行工具指定已安装的 Xcode 版本
			  logseq.order-list-type:: number
				- `sudo sh -c 'xcode-select -s /Applications/Xcode-16.4.0.app/Contents/Developer && xcodebuild -runFirstLaunch'`
			- 签署 Xcode 许可证协议
			  logseq.order-list-type:: number
				- 执行 `sudo xcodebuild -license` 输入 `agree`
		- ### 安装 iOS 模拟器
			- 参见: [[Xcode 安装模拟器]]
		- #### 安装 CocoaPods
			- 参见 [[CocoaPods 安装与配置]]
	- ### 搭建 Web 开发环境
		- 参考: [Flutter Docs - Set up web development](https://docs.flutter.dev/platform-integration/web/setup)
		- 安装 Chrome / Edge
	- ### 搭建 Windows 开发环境
		- 参见: [Flutter Docs - Set up Windows development](https://docs.flutter.dev/platform-integration/windows/setup) ==未阅==
	- ### 搭建 Linux 开发环境
		- 参见: [Flutter Docs - Set up Linux development](https://docs.flutter.dev/platform-integration/linux/setup) ==未阅==
	- ### 校验模拟器与真机环境
		- 执行 `flutter emulators` 以验证 **模拟器** 是否设置正确.
		  logseq.order-list-type:: number
			- 发现有我们已安装的 `Platform` 为 `Android/iOS` 的模拟器.
			- ``` zsh
			  ➜  ~ flutter emulators                   
			  2 available emulators:
			  
			  Id                  • Name           • Manufacturer • Platform
			  
			  apple_ios_simulator • iOS Simulator  • Apple        • ios
			  Pixel_9_Pro_XL      • Pixel 9 Pro XL • Google       • android
			  
			  To run an emulator, run 'flutter emulators --launch <emulator id>'.
			  To create a new emulator, run 'flutter emulators --create [--name xyz]'.
			  
			  You can find more information on managing emulators at the links below:
			    https://developer.android.com/studio/run/managing-avds
			    https://developer.android.com/studio/command-line/avdmanager
			  ```
		- 执行 `flutter devices` 以验证 **真机** 是否设置正确.
		  logseq.order-list-type:: number
			- 发现有我们已连接的 `Android/iOS/macOS/Chrome` 设备.
			- ``` zsh
			  ➜  ~ flutter devices   
			  Found 4 connected devices:
			    sdk gphone64 arm64 (mobile)     • emulator-5554         • android-arm64  • Android 16 (API 36) (emulator)
			    macOS (desktop)                 • macos                 • darwin-arm64   • macOS 15.5 24F74 darwin-arm64
			    Mac Designed for iPad (desktop) • mac-designed-for-ipad • darwin         • macOS 15.5 24F74 darwin-arm64
			    Chrome (web)                    • chrome                • web-javascript • Google Chrome 141.0.7390.108
			  
			  Found 1 wirelessly connected device:
			    Vince (mobile) • xxxxxxx • ios • iOS 18.6.2 22G100
			  
			  Device emulator-5570 is offline.
			  
			  Error: Browsing on the local area network for iPhone. Ensure the device is unlocked and attached with a cable or associated with the same local area network as this Mac.
			  The device must be opted into Developer Mode to connect wirelessly. (code -27)
			  
			  Run "flutter emulators" to list and start any available device emulators.
			  
			  If you expected another device to be detected, please run "flutter doctor" to diagnose potential issues. You may also try increasing the time to wait for connected devices with the
			  "--device-timeout" flag. Visit https://flutter.dev/setup/ for troubleshooting tips.
			  ```
- ## 验证安装
	- 查看版本 .
	  logseq.order-list-type:: number
		- ``` zsh
		  flutter --version
		  dart --version
		  ```
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