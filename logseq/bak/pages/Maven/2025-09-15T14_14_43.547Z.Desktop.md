alias:: [[Apache Maven]]
tags:: [[Build Tool]], [[Package Manager]]
---

- ==子目录==
	- [[Maven POM]]
	- [[Maven Settings]]
	- [[Maven Archetype]]
	- [[Maven Command]]
	-
- ---
- ## 官方资料
	- ### [官网](https://maven.apache.org/index.html)
		- [文档目录](https://maven.apache.org/guides/index.html)
		- [Central Repository Directory](https://repo.maven.apache.org/maven2/)
- ## 问题点
	- mvn spring-boot:run 为啥可以执行? ((6620bd09-1085-4f98-8ffd-4011f497fe85))
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number
- ---
- ## Maven 安装
	- ### Linux tar.gz 文件安装
		- 下载 tar.gz 文件: [Maven Download](https://maven.apache.org/download.cgi)
		  logseq.order-list-type:: number
		- 解压 tar.gz 文件: `tar -xvf xxxx.tar.gz`
		  logseq.order-list-type:: number
		- 设置环境变量, 编辑 `/etc/profile` 文件, 加入如下内容, 然后执行 `source /etc/profile`
		  logseq.order-list-type:: number
			- ``` sh
			  export MAVEN_HOME=解压后的目录
			  export PATH=$MAVEN_HOME/bin:$PATH
			  ```
		- 执行 `mvn -v` 查看 Maven 版本.
		  logseq.order-list-type:: number
		- 编辑 `conf/settings.xml` , 做如下修改:
		  logseq.order-list-type:: number
			- logseq.order-list-type:: number
			  ``` xml
			  <!-- <settings> 标签中加入如下内容 -->
			  <localRepository>maven 本地仓库地址</localRepository>
			  ```
			- logseq.order-list-type:: number
			  ``` xml
			  <!-- <settings>.<mirrors> 标签中加入如下内容 -->
			  <!-- maven 阿里云镜像 -->
			  <mirror>
			    <id>alimaven</id>
			    <name>aliyun maven</name>
			    <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
			    <mirrorOf>central</mirrorOf>
			  </mirror>
			  ```
- ## 环境变量配置
	- ### macOS
		- 添加如下环境变量至 Shell 对应的启动文件中：
		- ``` sh
		  export MAVEN_HOME=/Users/vincent/ZHU/dev/bin-tools/apache-maven-3.5.4
		  export PATH=$PATH:$MAVEN_HOME/bin
		  ```
-