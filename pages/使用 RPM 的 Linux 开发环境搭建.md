tags:: [[Linux]], [[RPM]], [[YUM]] 
---

- ## 安装 YUM
	-
- ## 安装常用工具
	- ``` sh
	  ################# 安装 git #################
	  ################# https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git
	  yum install git-all
	  # 查看版本
	  git version
	  
	  
	  ################# 安装 node.js #################
	  ################# https://nodejs.org/en/download/package-manager 
	  # installs nvm (Node Version Manager)
	  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
	  # download and install Node.js (you may need to restart the terminal)
	  nvm install 20
	  # verifies the right Node.js version is in the environment
	  node -v # should print `v20.15.0`
	  # verifies the right NPM version is in the environment
	  npm -v # should print `10.7.0`
	  
	  ################# 配置 npm 淘宝镜像 #################
	  npm config set registry https://registry.npmmirror.com
	  # 查看配置
	  npm config get registry
	  
	  ################# 安装 hexo #################
	  ################# https://hexo.io/docs/index.html#Install-Hexo
	  npm install hexo-cli -g
	  # 查看 hexo 版本
	  hexo version
	  
	  ################# 安装 java #################
	  ################# 
	  ```
-