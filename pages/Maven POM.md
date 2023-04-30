alias:: POM,

- tags:: Maven
-
-
- # Maven POM
	- ## 官方资料
		- [Maven POM 参考手册](https://maven.apache.org/pom.html)
	- ## <dependencyManagement>
		- 参考：[Dependency Management](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html#dependency-management)
		- `<dependencyManagement>` 的优先级 高于 传递依赖 ( transitive dependencies ) 。
		- 当前项目的 `<dependencyManagement>` 的优先级 高于 父项目的 `<dependencyManagement>` 。
		- ### Importing Dependencies
			- `<dependencyManagement>` 除了可以引入具体依赖的管理，还可以通过 `<scope>import</scope>` 引入 pom 类型的依赖中的 `<dependencyManagement>`
-
-
-