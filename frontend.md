##网站前端设计

##前言
参考了[stackoverflow](http://stackoverflow.com/)、[devdocs](http://devdocs.io/)的路由设计，网站一期准备采用前端单页应用

##路由设计

	列表页
		/javascript/date   //分类名

	tag聚合页
		/tagged/[tagname]  //tag标签

	搜索页
		/#q=[search word]  //==> 如果存在结果，自动切换到临时聚合页.

	临时聚合页
		/golbal_objects/[word]  //==> 临时按照特征词来临时聚合


##需要的数据接口支持

	分类接口
		http://server/ajax/classify?name=[classname]
	
	搜索接口
		http://server/ajax/search?word=[keyword]


##设计风格
遵循AMD规范设计，设计单页应用，使用seajs来做AMD模块框架.


