tags:: [[Maven]]
---

- ## tar.gz 文件安装
	- 下载 tar.gz 文件: [Maven Download](https://maven.apache.org/download.cgi)
	  logseq.order-list-type:: number
	- 解压 tar.gz 文件: `tar -xvf xxxx.tar.gz`
	  logseq.order-list-type:: number
	- 设置环境变量:
	  logseq.order-list-type:: number
		- ``` sh
		  # bash：编辑 `/etc/profile` 文件, 加入如下内容, 然后执行 `source /etc/profile`
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
-