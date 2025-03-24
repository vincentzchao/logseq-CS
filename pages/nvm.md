alias:: [[Node Version Manager]]
tags:: [[Node.js]], [[Version Manager]] 
---

- ## 官方资料
	- [nvm 官方库](https://github.com/nvm-sh/nvm)
	  logseq.order-list-type:: number
- ## 安装 nvm
	- ``` bash
	  # Download and install nvm:
	  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.2/install.sh | bash
	  
	  # in lieu of restarting the shell (代替重启 shell)
	  \. "$HOME/.nvm/nvm.sh"
	  ```
- ## 使用 nvm
	- ``` bash
	  # Download and install Node.js:
	  nvm install 22
	  
	  # Verify the Node.js version:
	  node -v # Should print "v22.14.0".
	  nvm current # Should print "v22.14.0".
	  ```
	-
-