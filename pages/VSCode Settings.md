tags:: [[VSCode]], [[Settings]]
---

-
- ## 概述
	- ### User 与 Workspace
		- `User Settings` 应用于全局，而 `Workspace Settings` 应用于单个 `Workspace` 。
		- `Workspace Settings` 会覆盖 `User Settings` 配置。
	- ## settings.json
		- ### 如何打开
			- `Ctrl + Shift + P` / `Command + Shift + P` 打开 `Command Palette` ，输入 `open settings` 。
		- ### 文件位置
			- **Windows** `%APPDATA%\Code\User\settings.json` e.g. `C:\Users\nigre\AppData\Roaming\Code\User\settings.json`
			- **macOS** `$HOME/Library/Application\ Support/Code/User/settings.json` (这里的 `\` 表示对空格的转义)
			- **Linux** `$HOME/.config/Code/User/settings.json`
			- PS: 若该文件从未被编辑过，则在上述路径下不存在该文件。
-
- ---
- ## 参考
	- [VSCode 官方文档](https://code.visualstudio.com/docs/getstarted/settings#_settings-editor)
-