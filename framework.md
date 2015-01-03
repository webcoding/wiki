##网站架构设计

##前言
因为都是web前端开发者出身，因为对node的喜爱。所以采用 linux+[express](http://www.expressjs.com.cn/)+[mysql](https://github.com/felixge/node-mysql)的设计。
使用开源库里比较火的两个库，API相对稳定，也有较全面的测试用例。

##路由设计
> 一期设计

	/index 首页
	/tools 工具分类
	/tools/sublime  工具下的sublime分类（一级类英文名, 二级类英文名）
	/about 关于网站团队的介绍
	

> 后续设计，补充文章的URL设计.

	/tools/sublime/{id}.html   工具sublime类下的文章 （文章id，每篇递增.不重复，可以考虑简单id加密，避免爬虫）

##模块划分

	--public 存放公共文件，浏览器端的js
	--views  后端模板
	--routes 模板路由
	--libs   后端程序库, DB、services等
	----DAO

##网站模板设计
使用[jade](https://github.com/jadejs/jade)模板，简洁明了.
	  
