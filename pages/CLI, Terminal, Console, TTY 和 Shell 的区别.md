tags:: [[Shell]]
---

- ## CLI 与 GUI
	- `CLI` 即 `Command-line Interface` ，命令行界面，早期的计算机程序都是 `CLI 程序` ，需要用到专门的 `Terminal` 设备进行交互。
	- 后来有了 `GUI` ，即 `Graphical User Interface`  ，图形用户界面，无需专门的 `Terminal` 设备，只需用到通用的键盘、鼠标和显示器即可进行交互。
- ## Terminal, TTY 与 Console
	- 早年间，计算机比较笨重，会被安置在单独的机房中；人们通过一些与机房连接的 **外部硬件设备** ，与计算机进行交互，这就是 `Terminal` (终端/终端机) 。
	  logseq.order-list-type:: number
	  id:: 675ce902-0dcb-447e-b3ef-b3922543ed8c
		- 这种外部设备通常需要提供输入功能以供用户 **输入** 、提供显示功能以供 **显示** 处理结果。
	- `Console` 属于 `Terminal` 的一种，也是 **外部硬件设备** ，专门用于系统管理员管理主机，比普通终端拥有更高的权限。
	  logseq.order-list-type:: number
		- 如今，随着个人电脑的普及，我们如今的外部设备 (键盘与显示器)，既可以认为是 `Console` ，也可以认为是 `Terminal` 。
			- 当你在管理系统时，它们是 `Console` ；
			- 当你在做一般的工作时，它们就是普通  `Terminal` 。
		- 所以，如今可以认为  `Console` 等同于 `Terminal` 。
- ## TTY
	- 由于外部设备都比较昂贵，所以 Unix 创始人当年采用 `Teletype` ( 即 `TTY` , **电传打字机** ) 当成 `Terminal` 设备使用。
		- `TTY` 是 Unix 系统的第一个 `Terminal` 。
		- `TTY` 演示：[TWO TELETYPE MODEL 37s LINK FOR RELAY CHAT AT 150 BAUD](https://www.youtube.com/watch?v=MikoF6KZjm0)
	-
- ## Terminal Emulator
	- 随着计算机的发展，我们已经看不到专门的 `Terminal` 设备了，而是通用的 **键盘和显示器** 。
	- 但是，由于早年的计算机都是 `CLI 程序` ，需要使用专门的 `Terminal` 设备处理用户的 **输入和显示** ，才能与这些 `CLI 程序` 进行交互。
	- 而如今通用的 **键盘和显示器** 只能通过 `图形化接口` 与 `GUI 程序` 交互，无法直接与 `CLI 程序` 进行交互。
	- 所以，为了解决这个问题，我们有了 `Terminal Emulator` (终端模拟器)，用于模拟传统的 `Terminal` 设备。它是这样工作的：
		- 接收用户的 `键盘` 输入。
		  logseq.order-list-type:: number
		- 将用户输入发送给 `CLI 程序` 。
		  logseq.order-list-type:: number
		- 获取程序执行结果 。
		  logseq.order-list-type:: number
		- 将执行结果渲染到 `显示器`
		  logseq.order-list-type:: number
	- 经典的 `Terminal Emulator` 有：
		- GNU/Linux：gnome-terminal、Konsole；
		- macOS：Terminal.app、iTerm2；
		- Windows：Win32 控制台、ConEmu 等。
	- 由于专门的 `Terminal` 设备已经快消失了，所以如今 `Terminal Emulator` 也被直接称为 `Terminal` 。
- ### Terminal Window 与 Virtual Console
	- 大部分 `Terminal Emulator` 运行在 `GUI 程序` 中，所以这种被称作 `Terminal Window` (终端窗口) 。
	- 也有由操作系统内核直接提供的 `Terminal Emulator` ，这种由内核提供的 `Terminal Emulator` 被称作 `Virtual Console` (虚拟控制器)
		- 比如 在 GNU/Linux 操作系统中，按下 Ctrl + Alt + F1,F2...F6 等组合键可以切换出好几个黑不溜秋的全屏终端界面，而按下 Ctrl + Alt + F7 才是切换回图形界面。
	- 如果 `GUI 程序`  挂掉了，会导致运行于它上面  `Terminal Emulator` 也挂掉，这个时候可以切到 `Virtual Console` 用于救火。
- ## 总结
	- 历史上：
		- `Terminal` 是用于与主机交互的 **外部硬件设备** 。
			- `Console` 是拥有更高权限的 `Terminal` 。
			- `TTY` 是当年 `Terminal`  的一种具体实现。
		- `Terminal Emulator` 是对 `Terminal` 设备的模拟。
			- 运行在 `GUI 程序` 中的 `Terminal Emulator` ，被称作 `Terminal Window` 。
			- 由 `操作系统内核` 直接提供的 `Terminal Emulator` ，被称作 `Virtual Console` 。
	- 如今：
		- `Console` 基本等同于 `Terminal` 。
		-
- ## 参考
	- [命令行界面 (CLI)、终端 (Terminal)、Shell、TTY，傻傻分不清楚？](https://segmentfault.com/a/1190000016129862)
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number