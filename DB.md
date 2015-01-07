##数据库设计
使用相对来说，比较稳定的[mysql](https://github.com/felixge/node-mysql)

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
          //"tagids": [125,126]         //冗余设计
        }
      },
      tag_list: {
        "125": {
          "id": 125,
          "name": "javascript",       //若为英文，全部用小写？
          "enname": "english-name",   //用作路由
          "rank": 4,
          "alias": ["js"],            //别名
          "quality": 23,              //该tag下url数量
          "links":[23,34453,3434]
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
