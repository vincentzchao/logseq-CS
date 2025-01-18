tags:: [[Maven]]
---

- ## 父子工程
	- ### 只部署父工程
		- ``` sh
		  mvn clean deploy -N
		  ```
	- ### 部分模块不部署
		- ``` sh
		  mvn clean deploy -pl "!module1,!module2"
		  ```
- ## 源码
	- ``` sh
	  # 下载依赖的源码
	  mvn dependency:resolve -Dclassifier=sources
	  ```
- ## 本地 Jar
	- ### 安装 Jar 文件到本地仓库
		- ``` sh
		  # 安装类文件 jar 包
		  mvn install:install-file \
		    -Dfile=demo.jar \
		    -DgroupId=com.example \
		    -DartifactId=demo \
		    -Dversion=0.0.1 \
		    -Dpackaging=jar
		  
		  # 安装源码 jar 包
		  mvn install:install-file \
		    -Dfile=demo-source.jar \
		    -DgroupId=com.example \
		    -DartifactId=demo \
		    -Dversion=0.0.1 \
		    -Dpackaging=jar \
		    -Dclassifier=sources
		  ```