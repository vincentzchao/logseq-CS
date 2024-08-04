## 字符串插值 (String Interpolation)
	- 使用 `\(变量名)` 在字符串中插入变量当前的值。
	- ``` swift
	  let apples = 3
	  let oranges = 5
	  let appleSummary = "I have \(apples) apples."
	  let fruitSummary = "I have \(apples + oranges) pieces of fruit."
	  ```
- ## 三个双引号
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