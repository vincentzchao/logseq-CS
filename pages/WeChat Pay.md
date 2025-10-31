tags:: [[Payment Product]], [[WeChat Dev]]
---

- ## 子目录
	- [[微信支付 - APP 支付业务流程 (V3)]]
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number
	- 各 语言/框架 集成:
		- [[Flutter 微信支付 SDK]]
		- [[Java 微信支付 SDK]]
	-
- ## 遇到的问题
	- [new: #3402 [微信支付]支持配置微信支付公钥](https://github.com/binarywang/WxJava/pull/3425)
	  logseq.order-list-type:: number
		- `weixin-java-pay` 4.6.0 版本不支持 `微信支付公钥` , 升级到 4.7.0
	- [{"errMsg":"requestPayment:fail [payment微信:-1]General errors","errCode":-100,"code":-100}](https://ask.dcloud.net.cn/question/121117)
	  logseq.order-list-type:: number
		- `weixin-java-pay` 生成的字段大小写与 uni-app 的 `uni.requestPayment` 的 `orderInfo` 对象中的字段不一样.
			- Android 用 appid
			- iOS 用 appId
	- 商户传入的 appid 不正确, 请联系商户处理
	  logseq.order-list-type:: number