-
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