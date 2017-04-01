# 数据库

使用[mongodb](https://github.com/LearnBoost/mongoose)

## 数据库设计

```js
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
```

## 关于设计

```js
var Keywords = new mongoose.Schema({
  keyword: String
});
var Book = new mongoose.Schema({
  title: String,
  author: String,
  releaseDate: Date,
  keywords: [Keywords]
});

var BookModel = mongoose.model( 'Book', Book );
```


首先实现分类列表，这个最初始需求

Mongodb中的Schema细节：

```js
// 定义对象模型
var CategoryScheme = new Schema({
  _parent_id:  Schema.Types.ObjectId,
  key: String,
  name: String,
  slug: String,//分类可用于路由
  alias: [String],//别名
  quality: Number,              //该分类下url数量
  rank: Number, //排序/权重
  icon: String,

  add_time: Date,
  last_modified: Date,
});
var Category = mongoose.model('category', CategoryScheme);
```

```js
//定义对象模型
var TagScheme = new Schema({
  key:String,
  name:String,
  alias:String,

  add_time: Date,
  last_modified: Date,
});
var Tag = mongoose.model('tag', TagScheme);
```

```js
//定义对象模型
var UrlScheme = new Schema({
  key: String,
  title: String,    //标题
  desc: String,   //描述
  url: String,      //url
  icon: String,   //icon或标识
  img: String,    //logo或大图
  host:String,  //域
  rank: Number,
  _group_id: [Schema.Types.ObjectId],
  _category_id: Schema.Types.ObjectId,
  _tag_ids:[Schema.Types.ObjectId],
  shared: Boolean,
  views: Number,         //浏览次数
  firstletter:  String,

  add_time: Date,
  last_modified: Date,
});
var Article = mongoose.model('article',  UrlScheme);
```







