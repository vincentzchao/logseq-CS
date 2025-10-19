tags:: [[Flutter]], [[Visual Studio Code]] 
---

- ## 环境搭建
	- [[VS Code 安装与配置]]
	  logseq.order-list-type:: number
	- 安装 [Flutter 插件](https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter) .
	  logseq.order-list-type:: number
		- 安装 Flutter extension 也会安装 Dart extension .
- ## Flutter 插件 - 项目相关
	- ### 创建项目
		- `Command + Shift + P` -> 输入 `flutter:` > 选择 `Flutter: New Project`
	- ### 选择运行设备
		- `Command + Shift + P` -> 输入 `flutter:` > 选择 `Flutter: Select Device`
		- 接下来界面点击运行, 会使用此处选择的设备.
- ## Flutter 插件 - 编码相关
	- ### 提取组件
		- 光标移到声明组件的代码上 > `Command + .` > 点击 `Extract Widget`
			- 即可将这部分代码抽为自定义组件.
	- ### 查看方法参数
		- 光标移动到方法括号内 > `Cmd + Shift + Space`
- ## 参考
	- [Flutter Docs - Visual Studio Code](https://docs.flutter.dev/tools/vs-code) ==待学习==
	  logseq.order-list-type:: number
	-