tags:: [[Linux]], [[RPM]], [[YUM]] 
---

- ## 安装 YUM
	-
- ## 安装常用工具
	- ``` sh
	  ################# 安装 unzip 和 zip #################
	  yum install unzip
	  yum install zip
	  
	  
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
	  
	  
	  ################# 安装 sdkman #################
	  ################# https://sdkman.io/install
	  curl -s "https://get.sdkman.io" | bash
	  source "$HOME/.sdkman/bin/sdkman-init.sh"
	  # 查看 sdkman 版本
	  sdk version
	  # 发现好像 sdkman 中没有 openjdk 或 oracle jdk 的 1.8 版本
	  
	  
	  ################# 安装 openjdk 1.8 #################
	  ################# https://openjdk.org/install/
	  su -c "yum install java-1.8.0-openjdk"
	  # 查看 java 版本
	  java -version
	  
	  ################# 安装 Maven #################
	  ################# https://maven.apache.org/download.cgi
	  # 貌似官方未提供 yum 包
	  yum install maven
	  # 查看 Maven 版本
	  mvn -version
	  # 新建 ~/.m2/settings.xml 文件编辑如下内容
	  
	  ```
- ## 安装一些服务
	- ``` sh
	  ################# 安装 Caddy #################
	  ################# https://caddyserver.com/docs/install#fedora-redhat-centos
	  yum install yum-plugin-copr
	  yum copr enable @caddy/caddy
	  yum install caddy
	  
	  
	  ################# 安装 Redis #################
	  ################# https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/install-redis-on-linux/
	  # 官方文档中没有提到 redis 在 yum 仓库的包
	  yum install redis
	  # 后台启动 redis
	  systemctl start redis
	  # 设置 redis 开机自启
	  systemctl enable redis
	  # 连接 redis 进行测试
	  redis-cli
	  
	  
	  ################# 安装 MySQL #################
	  ################# https://dev.mysql.com/doc/refman/8.4/en/linux-installation-yum-repo.html
	  
	  ```