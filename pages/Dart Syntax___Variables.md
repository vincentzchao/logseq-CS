tags:: [[Dart]]
---

- ## 变量分类
	- `Top-level variables` : 直接定义在文件的最外层, 而不在任何 `method` 或 `class` 中的变量.
	  logseq.order-list-type:: number
	- `Class variables` : 定义在类中的变量.
	  logseq.order-list-type:: number
		- 又可分为两种:
			- `Instance variables` :  属于类的实例.
			  logseq.order-list-type:: number
			- `Static variables` : 属于类本身, 所有实例共享.
			  logseq.order-list-type:: number
	- `Local variables` : 定义在方法中的变量.
	  logseq.order-list-type:: number
- ## Declare a variable
	- ``` dart
	  // var
	  var name = 'Bob';
	  
	  // type
	  String name = 'Bob';
	  ```
	- 声明一个变量有如下方式:
		- 不声明类型 , 使用 `var` ,  dart 会进行类型推断.
		  logseq.order-list-type:: number
		- 声明具体类型.
		  logseq.order-list-type:: number
- ## Declare a nullable variable
	- 声明一个 Nullable 变量, 它可以被赋值为 `null` .
		- ``` dart
		  String? name = 'TOM';  // Nullable type. Can be `null` or string.
		  name = null;
		  ```
	- 未使用 `类型` + `?` 声明的变量都是 Non-nullable 变量, 它们不能被赋值为 `null` .
- ## Initialize a variable
	- ### Default Value
		- `Nullable` 变量若在声明时, 未进行初始化, 则会被给默认值 `null` .
			- 不管是什么类型的变量都为 `null` , 因为 Dart 中万物皆对象
			- ``` dart
			  String? name;   // Nullable type. Can be `null` or string.
			  print(name); // 打印 null , 因为 Nullable variable 有 默认值 null
			  ```
		- `Non-nullable` 变量没有默认值, 所以在访问前 (声明时或声明后) 必须进行初始化, 否则编译会报错:
			- ``` dart
			  String name;   // Non-nullable type. Cannot be `null` but can be string.
			  print(name); // 编译报错, 因为未给 Non-nullable variable 赋值就访问它
			  ```
	- ### Lazily initialization
		- `Top-level variables` 和 `Class variables` 采用延迟加载机制, 即:
			- 声明时等号右边的初始化代码, **会在变量首次被使用时执行** .
			- ``` dart
			  // Top-level variable
			  String description = init();
			  
			  void main() {
			    print("main");
			    print(description);
			  }
			  
			  String init() {
			    print("init");
			    return 'Initialized';
			  }
			  
			  // 打印顺序如下
			  // main
			  // init
			  // Initialized
			  ```
	- ### Late variables
		- #### Late variables 的两大作用
			- Initialize after declaration : 告知 Dart , 这个变量我后面会初始化.
			  logseq.order-list-type:: number
				- ``` dart
				  late String description;
				  ```
			- Lazily initialization : 告知 Dart , 这个变量等我用到的时候再执行初始化.
			  logseq.order-list-type:: number
				- ``` dart
				  // init() 方法会等用到 description 的时候才执行
				  late String description = init();
				  ```
		- #### Initialize after declaration
			- Dart 有时候可能无法判断一个 `Non-nullable` 变量在访问前, 是否已被初始化.
			- 所以, 需要在声明时指定 `late` 关键字, 以告知 Dart : *这个变量我后面会初始化的* . 否则会报错
				- 这种情况, 一般出现在 `Top-level variables` 和 `Instance variables`
					- ``` dart
					  // 不加 late 会报错
					  late String description;
					  
					  void main() {
					    description = 'Feijoada!';
					    print(description);
					  }
					  ```
				- 像 `Local variables` 就没这个问题:
					- ``` dart
					  void main() {
					    String description;
					    description = 'Feijoada!';
					    print(description); // 正常打印 Feijoada!
					  }
					  ```
			- ==注意: 声明了 late 也还是需要初始化, 否则还是会报错.==
		- #### Lazily initialization
			-
- ## Object 和 dynamic 变量
	- 声明动态类型 (即 变量的类型可以变化) , 使用 `Object` 类型 / `dynamic` 关键字.
		- ``` dart
		  Object obj = "This is an object";
		  print(obj);
		  obj = 3.14;
		  print(obj);
		  
		  dynamic dynamicVal = "I am dynamic";
		  print(dynamicVal);
		  dynamicVal = true;
		  print(dynamicVal);
		  ```
- ## 参考
	- [Dart Docs - Variables](https://dart.dev/language/variables)
	  logseq.order-list-type:: number