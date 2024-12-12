tags:: [[Swift]]
---

-
- ## print (打印)
	- ``` swift
	  print("Hello, world!")
	  ```
- ## Simple Values (简单值)
	- ### let 与 var 的使用
		- `let` 关键字定义 **常量(constant)** , 在程序中必须赋一次值 (如果没用到的话, 不赋值也可以)，且只能赋一次值 .
		- `var` 关键字定义 **变量(variable)** .
		- ``` swift
		  var myVariable = 42
		  myVariable = 50
		  let myConstant = 42
		  ```
	- ### 常量与变量的类型
		- 无需 **显式(explicitly)** 指定 **常量或变量** 的类型, **编译器** 可以通过赋值来推断其类型 .
		- **变量或常量** 如果在声明时未被赋值的话，则必须 显式 声明其类型。
		- 一个变量被赋的多个值的类型, 必须一致 .
		- ``` swift
		  // 显式声明 常量 的类型。
		  let explicitDouble: Double = 70
		  ```
		- 一个类型从来不会被 **隐式地(implicitly)** 转换成另一种类型，必须 显式地 转换 .
		- ``` swift
		  let label = "The width is "
		  let width = 94
		  let widthLabel = label + String(width)
		  ```
	- ### 将 value 转成 String
		- 使用 `\(变量名)` 将值转成字符串。
		- ``` swift
		  let apples = 3
		  let oranges = 5
		  let appleSummary = "I have \(apples) apples."
		  let fruitSummary = "I have \(apples + oranges) pieces of fruit."
		  ```
	- ### 三个双引号
		- 使用 **三个双引号** 可以定义多行字符串 .
		- ``` swift
		  let apples = 3
		  let oranges = 5
		  let quotation = """
		         Even though there's whitespace to the left,
		      the actual lines aren't indented.
		              Except for this line.
		          Double quotes (") can appear without being escaped.
		  
		          I still have \(apples + oranges) pieces of fruit.
		      """
		  print(quotation)
		  ```
		- 实际的字符串的值，将会忽略与 结尾 `"""`保持一致 **缩进** 的行的前面的缩进；其他行，都会参照结尾 `"""` 保留相应的缩进。
	- ### array (数组)
		- 数组大小会根据元素的增加 (使用 `append()` 方法) 而增大 .
		- ``` swift
		  var shoppingList = ["catfish", "water", "tulips", "blue paint"]
		  shoppingList[1] = "bottle of water"
		  
		  shoppingList.append("apples")
		  print(shoppingList)
		  
		  shoppingList[4] = "bananas"
		  
		  print(shoppingList)
		  ```、
		- 空数组: `shoppingList = []` .
		- 数组类型是这样声明的
			- ``` swift
			  let emptyArray: [String] = []
			  ```
	- ### dictionary (字典)
		- ``` swift
		  var occupations = [
		      "Malcolm": "Captain",
		      "Kaylee": "Mechanic",
		  ]
		  occupations["Jayne"] = "Public Relations"
		  ```
		- 空字典: `occupations = [:]` .
		- 字典类型是这样声明的
			- ``` swift
			  let emptyDictionary: [String: Float] = [:]
			  ```
- ## Control Flow (控制流)
	- ### 条件与循环的种类
		- Conditional (条件): if, switch
		- Loop (循环): for-in, while, repeat-while
	- ### 括号可有可无
		- **条件语句** 和 **循环变量** 的 **小括号 (Parentheses)** 可以去掉，但语句块的 **大括号 (Braces)** 还是要保留。
		- ``` swift
		  let individualScores = [75, 43, 103, 87, 12]
		  var teamScore = 0
		  for score in individualScores {
		      if score > 50 {
		          teamScore += 3
		      } else {
		          teamScore += 1
		      }
		  }
		  print(teamScore)
		  // Prints "11"
		  ```
	- ### 条件语句赋值
		- `if` 和 `switch` 语句块可以紧跟在 `=` 后面进行赋值; 或跟在 `return` 后面返回.
		- ``` swift
		  var teamScore = 11
		  let scoreDecoration = if teamScore > 10 {
		      "🎉"
		  } else {
		      ""
		  }
		  print("Score:", teamScore, scoreDecoration)
		  // Prints "Score: 11 🎉"
		  ```
- ## Optional Value (可选值)
	- ### nil
		- swift 中，值的缺失，用 `nil` 表示。
	- ### 声明 optional value
		- 如果一个值可能为 `nil`, 则他是一个 `optional value` .
		- 常量或变量在被声明时，如果未明确指定它是  `optional value` ，则它不能被赋值为 `nil` .
		- 声明 `optional value`  时，需要在 `type` 后面使用 `?` , 如下所示：
		  id:: 651e7829-cd38-4e6a-b191-a8e65e07e695
			- ``` swift
			  var optionalString: String? = nil
			  print(optionalString == nil)
			  // Prints "false"
			  ```
	- ### 什么是 unwrap (解包)
		- optional value 和 上面的 simple value 不同, 使用时, 需要进行 `unwrap` 操作。
		- 参见如下例子:
			- ``` swift
			  var aaa: String? = "xxx"
			  print(aaa)
			  ```
			- 执行结果:
			- ``` swift
			  Unwrap.swift:2:7: warning: expression implicitly coerced from 'String?' to 'Any'
			  print(aaa)
			        ^~~
			  Unwrap.swift:2:7: note: provide a default value to avoid this warning
			  print(aaa)
			        ^~~
			            ?? <#default value#>
			  Unwrap.swift:2:7: note: force-unwrap the value to avoid this warning
			  print(aaa)
			        ^~~
			           !
			  Unwrap.swift:2:7: note: explicitly cast to 'Any' with 'as Any' to silence this warning
			  print(aaa)
			        ^~~
			            as Any
			  Optional("xxx")
			  ```
			- optional value 无法直接使用, 直接打印回打印出 `Optional("xxx")` 这样的字符串和一些警告, 需要先进行 unwrap 解包操作.
		- `unwrap` 就是将 `optional value` 转成 `simple value` 进行使用 .
	- ### unwrap 的几种方式
		- 参考: [Swift 程式語言 — 解開可選類型 (Unwrapping Optionals)](https://medium.com/jeremy-xue-s-blog/swift-%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80-%E8%A7%A3%E9%96%8B%E5%8F%AF%E9%81%B8%E9%A1%9E%E5%9E%8B-unwrapping-optionals-6198f307a92d)
		- #### `??` 操作符
			- 如果前面的值为 `nil` , 则表达式的结果为后面的值 .
			- ``` swift
			  let nickname: String? = nil
			  let fullName: String = "John Appleseed"
			  let informalGreeting = "Hi \(nickname ?? fullName)"
			  ```
		- #### 条件语句中的 unwrap
			- 可以在条件语句中将 `optional value` 赋值给另一个新的常量或变量，从而达到解包的目的.
			  id:: 65202a72-fced-43a8-b1fc-0851245906de
			- 当 `optional value`为 `nil`时, 语句块不会被执行, 否则会被执行.
			- 这个新的常量或变量的作用域只存在于这个语句块中.
			- 可以使用与这个 `optional value` 名称相同的名称, 这样可以省略后面的赋值语句.
			- ``` swift
			  var optionalName: String? = nil
			  var greeting = "Hello!"
			  if let name = optionalName {
			      greeting = "Hello, \(name)"
			  }
			  print(greeting)
			  // Prints "Hello!"
			  
			  if let optionalName = optionalName {
			      greeting = "Hello, \(optionalName)"
			  }
			  print(greeting)
			  // Prints "Hello!"
			  
			  if let optionalName {
			      greeting = "Hello, \(optionalName)"
			  }
			  print(greeting)
			  // Prints "Hello!"
			  ```
			-
- ---
- ## 参考
	- [A Swift Tour](https://gitbook.swiftgg.team/swift/) (中文版: [Swift 初见](https://gitbook.swiftgg.team/swift/huan-ying-shi-yong-swift/03_a_swift_tour))
	-