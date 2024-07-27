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
- ## Array (数组)
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
- ## Dictionary (字典)
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
- ## Optional
	- ### nil
		- swift 中，值的缺失，用 `nil` 表示。
	- ### 什么是 Optional
		- 如果一个变量可能为 `nil` , 则它是一个 `Optional` .
		- 语法 (type 后 使用 `?` )：
		  id:: 651e7829-cd38-4e6a-b191-a8e65e07e695
			- ``` swift
			  var optionalString: String? = nil
			  print(optionalString == nil)
			  // Prints "true"
			  
			  // 如果 Optioanl 未赋值，则有默认值 nil
			  var surveyAnswer: String?
			  ```
		- 常量或变量在被声明时，如果未明确指定它是  `Optional` ，则它不能被赋值为 `nil` .
		- 我们无法像使用普通变量一样使用 Optional , 需要进行 `unwrap(解包)`  操作。
			- ``` swift
			  var aaa: String? = "xxx"
			  // aaa 无法直接打印, 
			  // 直接打印会打印出 `Optional("xxx")` 这样的字符串和一些警告, 
			  print(aaa)
			  
			  // 但是如果值是 nil ，可以直接打印出 nil
			  var bbb: String? = nil
			  print(bbb) // nil
			  
			  // 无法进行运算，会报错
			  var newAaa = aaa + "yyy"
			  
			  // 但是可以重新赋值
			  aaa = "yyy"
			  ```
	- ### 使用 Optional Binding 解包
		- ``` swift
		  let possibleNumber = "123"
		  let myNumber = Int(possibleNumber)
		  // Here, myNumber is an optional integer
		  if let myNumber = myNumber {
		      // Here, myNumber is a non-optional integer
		      print("My number is \(myNumber)")
		  } else {
		      // Here, myNumber is a optional integer (nil)
		      if (myNumber == nil) {
		          print("My number is \(myNumber)")
		      }
		      print("My number is \(myNumber)")
		  }
		  // Here, myNumber is an optional integer
		  // Prints "My number is 123"
		  
		  ```
		- 如果 if 语句块的 myNumber 被赋的值不是 nil ，则执行第一个分支，并且此时 myNumber 是 `Int` 类型，而不是 `Int?` .
		- 如果 if 语句块的 myNumber 被赋的值是 nil , 则执行第二个分支，此时 myNumber 是 `Int?` 类型 .
		- if 语句块的变量作用域只在 if 语句块中，所以可以和外部变量同名，外部 myNumber 一直是 `Int?` 类型 .
		- ``` swift
		  let possibleNumber = "123"
		  let myNumber = Int(possibleNumber)
		  // Here, myNumber is an optional integer
		  if let myNumber {
		      // Here, myNumber is a non-optional integer
		      print("My number is \(myNumber)")
		  }
		  // Prints "My number is 123"
		  ```
		- if 语句块的 变量使用和 Optional 相同的名称，将可以直接省略赋值语句。
		- ``` swift
		  if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
		      print("\(firstNumber) < \(secondNumber) < 100")
		  }
		  // Prints "4 < 42 < 100"
		  
		  if let firstNumber = Int("4") {
		      if let secondNumber = Int("42") {
		          if firstNumber < secondNumber && secondNumber < 100 {
		              print("\(firstNumber) < \(secondNumber) < 100")
		          }
		      }
		  }
		  // Prints "4 < 42 < 100"
		  
		  // 以上两个语句块等价
		  ```
		- 可以一行写多个 Optional Binding 。
	- ### 使用 `??` 操作符 (Nil-Coalescing Operator) 解包
		- 如果前面的值为 `nil` , 则表达式的结果为后面的值 .
		- ``` swift
		  let nickname: String? = nil
		  let fullName: String = "John Appleseed"
		  let informalGreeting = "Hi \(nickname ?? fullName)"
		  ```
	- ### 强制解包 (Force unwrapping)
		- 使用 `!` 符号 (exclamation mark)
		- ``` swift
		  let possibleNumber = "123"
		  let convertedNumber = Int(possibleNumber)
		  
		  // 此时 number 是 Int 类型
		  let number = convertedNumber!
		  ```
		- 如果 convertedNumber 值为 nil ，会报错。
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
- ---
- ## 参考
	- [A Swift Tour](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/guidedtour/) (中文版: [Swift 初见](https://gitbook.swiftgg.team/swift/huan-ying-shi-yong-swift/03_a_swift_tour))
	-