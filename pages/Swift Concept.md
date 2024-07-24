tags:: [[Swift]]
---

- ## 安装 Swift
	- 下载 Swift : [Install Swift](https://www.swift.org/install/)
	- macOS 直接在 App Store 安装 Xcode 。
	- 安装 Xcode 也会安装其内置的 Swift 。
	- 在 App Store 升级 Xcode 也会升级其内置的 Swift 。
	- 执行 `swift --version` 查看 Swift 版本。
- ## 如何运行 Swift 代码
  id:: 651d39e1-512d-4825-acf3-5c403015217f
	- **Xcode**: 在 Xcode 中创建 Project 编写代码并运行。 ==初学阶段不推荐，太重==
	- **Swift Playground**: 在 [Swift Playground](https://developer.apple.com/swift-playgrounds/) 中编写代码并运行; 除了编写自己的代码运行，里面还有一些编程小游戏可以玩 . ==一键运行，推荐==
	- **[[Swift REPL]]**: 执行 `swift repl` 即可进入互动式编程环境. ==如果有代码需要快速验证，可以采用这种方式==
	- **swift 命令**: 使用趁手的文本编辑器编辑源代码，然后使用 `swift <run> ${文件名}` 命令执行 swift 代码 (run 可以加，也可以不加，后续版本将会去掉 run )。 ==个人推荐有编程基础者初学阶段采用这种方式==
- ## 包管理四大实体
  id:: 651d1806-f5c5-4134-8598-908f479b656d
	- ==参考== : [SwiftPM - Conceptual Overview](https://www.swift.org/package-manager/)
	- ### 四大实体
		- Module
		- Package
		- Product
		- Dependency
	- ### Module
		- 一个 Module 指定了它自己的 `namespace` 和 `允许外部访问的部分代码` 。
		- 一个程序可能只有一个 Module ，也可能会 import 其他 Module 。
	- ### Package
		- 一个 package 由 `Swift source files` 和 `a manifest file` 组成。
		- `manifest file` 文件名为 `Package.swift`, 定义了 `package name` 和 `package contents` 。
		- 一个 package 有一个或多个 `target`, 每一个 `target` 都指定 一个 `product` 以及 一个或多个 `dependency` 。
	- ### Product
		- 每个 `target` 都可以 build 成一个 `library` 或 `executable` 作为它的 `product` 。
		- 一个 `library` 包含了一个可以被其他 `Swift code` import 的 `module` .
		- `executable` 是可以被任何操作系统执行的程序。
		  id:: 651d2af5-c641-4a19-be55-580b97546508
	- ### Dependency
		- `target` 的 `dependencies` 就是这个 `package` 需要 `import` 的 `module` .
		-
-