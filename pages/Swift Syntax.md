tags:: [[Swift]]
---

- ## print (打印)
	- ``` swift
	  print("Hello, world!")
	  
	  print("Hello, world, ", "Jack")
	  ```
- ## 注释
	- ``` swift
	  // Single-line comments 单行注释
	  // This is a comment.
	  
	  // Multiline comments 多行注释
	  /* This is also a comment
	  but is written over multiple lines. */
	  
	  // Nested multiline comments 嵌套多行注释
	  /* This is the start of the first multiline comment.
	      /* This is the second, nested multiline comment. */
	  This is the end of the first multiline comment. */
	  ```
- ## 分号
	- 除非你想在一行中编写多个语句，否则，分号不是必须的。
		- ``` swift
		  let cat = "🐱"; print(cat)
		  ```
- ## 常量与变量
	- ### 语法
		- `let` 定义 **常量 (constant)** ,  必须且只能赋一次值 (如果没用到，则可不赋值) 。
		- `var` 定义 **变量 (variable)** .
		- ``` swift
		  var myVariable = 42
		  myVariable = 50
		  
		  let myConstant = 42
		  ```
	- ### 命名
		- 常量与变量的名称几乎可以是任何字符，包括 Unicode 字符：
			- ``` swift
			  let π = 3.14159
			  let 你好 = "你好世界"
			  let 🐶🐮 = "dogcow"
			  ```
		- 命名有如下几条规则：
			- 不能使用禁用字符，参见: [Naming Constants and Variables](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/thebasics/#Naming-Constants-and-Variables)
			  logseq.order-list-type:: number
			- 数字不能在开头。
			  logseq.order-list-type:: number
			- 如果非要使用保留字，则需要使用 ` 字符围住变量名。
			  logseq.order-list-type:: number
				- ``` swift
				  let `let`: String = "hhh";
				  ```
		- ==建议使用小驼峰==
- ## 类型注解 (Type Annotation)
	- 类型注解的使用：
		- ``` swift
		  // 声明单个变量的类型
		  var explicitDouble: Double
		  
		  // 声明多个变量的类型
		  var red, green, blue: Double
		  ```
	- 如果未 **显式 (explicitly)** 指定 **常量或变量** 的类型, **编译器** 可以通过赋值来推断其类型 .
		- ``` swift
		  // 被推断为 String
		  var myVariable = "hello"
		  
		  // 被推断为 Int
		  var myNum = 42
		  
		  // 被推断为 Double
		  let pi = 3.14159
		  ```
	- **常量或变量** 如果在声明时未被赋值，则必须 显式 声明其类型。
		- ``` swift
		  // 如下代码会报错
		  let a;
		  // 如下代码会报错
		  var b;
		  ```
	- 一个变量被赋的多个值的类型, 必须一致 。
	- 一个类型从来不会被 **隐式地 (implicitly)** 转换成另一种类型，必须 显式地 转换 .
		- ``` swift
		  let label = "The width is "
		  let width = 94
		  let widthLabel = label + String(width)
		  ```
- ## Type Aliases
	- 使用类型别名。
	- ``` swift
	  // 定义类型别名
	  typealias AudioSample = UInt16
	  ```
- ## Number
	- ### Integer
		- UInt8  Int8
		- UInt16  Int16
		- UInt32  Int32
		- UInt64  Int64
		- 也可以直接使用 `UInt` 和 `Int` 来声明变量，具体类型视平台位数而定：32-bit 平台则默认类型是 32 位 ，32-bit 平台则默认类型是 64 位 。
		- ==官方建议: ==
			- 除非有限定整数大小的要求，否则，建议直接使用 `UInt` 和 `Int`  
			  logseq.order-list-type:: number
			- 除非有整数大小的限制，否则，即便要存储非负整数，也应使用 `Int` 而不是 `UInt`
			  logseq.order-list-type:: number
			- 上述两点的目的是避免做类型转换。
	- ### Floating-Point Numbers
		- Double: 64 位浮点数
		- Float: 32 位浮点数
		- ==官方建议：==
			- 首选 Double 。
	- ### Numeric Literals
		- 十进制: 没有前缀
		- 二进制: 带 `0b` 前缀
		- 八进制:  带 `0o` 前缀
		- 十六进制: 带 `0x` 前缀
		- `1.25e2` means 1.25 x 10²
		- `0xFp2` means 15 x 2²
		- `1_000_000.000_000_1` means `1000000.0000001`
	- ### Number Conversion
		- 相同类型才能进行运算，必须显式转换类型。
		- ``` swift
		  // 整型与整型
		  let twoThousand: UInt16 = 2_000
		  let one: UInt8 = 1
		  let twoThousandAndOne = twoThousand + UInt16(one)
		  
		  // 整型与浮点数
		  let three = 3
		  let pointOneFourOneFiveNine = 0.14159
		  let pi = Double(three) + pointOneFourOneFiveNine
		  ```
- ## Bool
	- ``` swift
	  let orangesAreOrange = true
	  let turnipsAreDelicious = false
	  
	  let val: Bool = false
	  ```
- ## String
	- ### 字符串插值 (String Interpolation)
		- 使用 `\(变量名)` 在字符串中插入变量当前的值。
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
		  
		  // 最终字符串
		     Even though there's whitespace to the left,
		  the actual lines aren't indented.
		          Except for this line.
		      Double quotes (") can appear without being escaped.
		  
		      I still have \(apples + oranges) pieces of fruit.
		  ```
		- 实际的字符串的值，将会忽略与 结尾 `"""`保持一致 **缩进** 的行的前面的缩进；其他行，都会参照结尾 `"""` 保留相应的缩进。
- ## Tuple
	- ### 语法
		- 元组可以存储多个数据，数据类型可以不一致。
		- ``` swift
		  let http404Error = (404, "Not Found")
		  ```
	- ### Decompose
		- 将元组中的内容分别赋值给不同的变量。
			- ``` swift
			  let (statusCode, statusMessage) = http404Error
			  print("The status code is \(statusCode)")
			  // Prints "The status code is 404"
			  print("The status message is \(statusMessage)")
			  // Prints "The status message is Not Found"
			  ```
		- 只取一部分值，忽略剩下的值。
			- ``` swift
			  let (justTheStatusCode, _) = http404Error
			  print("The status code is \(justTheStatusCode)")
			  // Prints "The status code is 404"
			  ```
	- ### 使用索引访问元组中的元素
		- ``` swift
		  print("The status code is \(http404Error.0)")
		  // Prints "The status code is 404"
		  print("The status message is \(http404Error.1)")
		  // Prints "The status message is Not Found"
		  ```
	- ### 使用名称访问元组中的元素
		- ``` swift
		  let http200Status = (statusCode: 200, description: "OK")
		  print("The status code is \(http200Status.statusCode)")
		  // Prints "The status code is 200"
		  print("The status message is \(http200Status.description)")
		  // Prints "The status message is OK"
		  ```
- ## array (数组)
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
- ## dictionary (字典)
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
			  // Prints "true"
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
	- [A Swift Tour](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/guidedtour/) (中文版: [Swift 初见](https://gitbook.swiftgg.team/swift/huan-ying-shi-yong-swift/03_a_swift_tour))
	-