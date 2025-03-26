tags:: [[macOS Command]]
---

- ## pkgutil --forget
	- 移除系统中执行安装包的信息.
	- ``` zsh
	  sudo pkgutil --forget org.nodejs.node.pkg.bom
	  sudo pkgutil --forget org.nodejs.npm.pkg
	  
	  # 执行如上命令后, 以下四个文件被移出
	  ➜  bin ll /var/db/receipts | grep 'nodejs'
	  -rw-r--r--  1 root  wheel   647K Nov 21  2022 org.nodejs.node.pkg.bom
	  -rw-r--r--  1 root  wheel   244B Nov 21  2022 org.nodejs.node.pkg.plist
	  -rw-r--r--  1 root  wheel   549K Nov 21  2022 org.nodejs.npm.pkg.bom
	  -rw-r--r--  1 root  wheel   240B Nov 21  2022 org.nodejs.npm.pkg.plist
	  ```
	-