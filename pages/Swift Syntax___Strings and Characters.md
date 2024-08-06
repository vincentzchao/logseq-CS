## String Literals
	- ``` swift
	  let someString = "Some string literal value"
	  ```
- ## Multiline String Literals
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
	- 实际的字符串的值，每一行将会参照结尾 `"""` (closing quotation marks) 的缩进位置去掉缩进。
	- ``` swift
	  let softWrappedQuotation = """
	  The White Rabbit put on his spectacles.  "Where shall I begin, \
	  please your Majesty?" he asked.
	  
	  "Begin at the beginning," the King said gravely, "and go on \
	  till you come to the end; then stop."
	  """
	  ```
	- 每一行末尾的 `\` 不是字符串的一部分，只是用来表明最终字符串不换行 (声明时换行只是让代码更可读)。
- ## 字符串插值 (String Interpolation)
	- 使用 `\(变量名)` 在字符串中插入变量当前的值。
	- ``` swift
	  let apples = 3
	  let oranges = 5
	  let appleSummary = "I have \(apples) apples."
	  let fruitSummary = "I have \(apples + oranges) pieces of fruit."
	  ```
- ---
- ## 参考
	- [Swift Language Guide - Strings and Characters](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/stringsandcharacters)
	  logseq.order-list-type:: number