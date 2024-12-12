tags:: [[JDK]]
---

- ## JDK 产品
	- **参考:**
		- [【方向盘】逐渐碎片化的Java生态圈：Oracle JDK、OpenJDK、阿里Dragonwell、华为毕昇](https://developer.aliyun.com/article/1108370)
		- [Java Is Still Free 3.0.0 (Oct 2021)](https://medium.com/@javachampions/java-is-still-free-3-0-0-ocrt-2021-bca75c88d23b)
		- [What is the difference between Azul OpenJDK, Zulu OpenJDK and OpenJDK?](https://stackoverflow.com/a/61337953)
	- Oracle JDK: Oracle 官方 JDK ，并不完全免费 (8u211 以下版本 (比如JDK 8u202) 不升级就不收费，升级但不商用也不收费) 。
	- [[OpenJDK]]: ((64b0478b-19e5-44e2-a920-5f1903492e00))
	- [[AdoptOpenJDK]]: ((64b0a03c-4c2b-480b-9c6e-feef4022f315))
	- [[Temurin]]: ((64b0a72d-0290-46e2-9f16-ef3aec627ae5))
	-
- ## Oracle JDK 安装
	- ### Linux 安装
		- #### tar.gz 包的安装
			- 下载指定版本和系统的 tar.gz 安装包: [Oracle JDK Download](https://www.oracle.com/java/technologies/downloads/#java21)
			  logseq.order-list-type:: number
			- 解压: `tar -xvf xxxxx.tar.gz`
			  logseq.order-list-type:: number
			- 设置环境变量, 编辑 `/etc/profile` 文件, 加入如下内容, 然后执行 `source /etc/profile`
			  logseq.order-list-type:: number
				- ``` sh
				  export JAVA_HOME=解压后产生的目录的路径
				  export PATH=$JAVA_HOME/bin:$PATH
				  ```
			- 执行 `java -verison` 查看 java 版本.
			  logseq.order-list-type:: number
		-