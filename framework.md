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
	  
##数据库设计

    {
      category_list: {
        "123": {
          "id": 123,
          "img": "icon",
          "name": "框架",
          "enname": "english-name",   //用作路由
          "parentid": 12,
          "rank": 4,                  //排序/权重
          "quality": 23,              //该分类下url数量
          "add_date": "1399467780",
          "last_modified": "1418038405",
          "lock": "0",
          "childrenids": [23,34,67],  //冗余设计
          "tagids": [125,126]         //冗余设计
        }
      },
      tag_list: {
        "125": {
          "id": 125,
          "name": "javascript",       //若为英文，全部用小写？
          "enname": "english-name",   //用作路由
          "rank": 4,
          //"alias": "js",            //别名
          "quality": 23,              //该tag下url数量
          "add_date": "1399467780",
          "last_modified": "1418038405"
        },
      },
      url_list: {
        "c265e4bd629300c50de2010597425b5591f4e87ccc6ed240": {
          "hash": "c265e4bd629300c50de2010597425b5591f4e87ccc6ed240",
          "id": 234,
          "title": "git教程",
          "disc": "描述",
          "url": "//baidu.com/***.html",
          "host": "//host.com",   //冗余设计z
          "author": "作者",
          "logo": "icon或标识",
          "img": "",
          "rank": 4,
          "views": 345,         //浏览次数
          "votes": 23,          //投票/赞
          "categoryid": 3202,   //分类
          "groupid": 0,         //分组
          "tagids": [123,456],
          "firstletter": "G",
          "add_date": "1399467780",
          "last_modified": "1418038405"
        }
      }
    }
