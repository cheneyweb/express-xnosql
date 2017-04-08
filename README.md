# express-xnosql
NoSql服务应用，基于express-xnosql中间件，快速构建轻量小巧灵活的NoSql服务

整体框架使用说明
>
	1,config/default.js中设置数据库连接，执行npm install
	2,node app.js(启动)

单独使用x-nosql中间件(任意express应用均可集成)
>
	1, npm install x-nosql --save

	2, let nosql = require('x-nosql')

	3, xnosql.dburl = 'mongodb://localhost:27017/test'

	4, app.use('/xnosql/', xnosql)

框架目录结构（后台）
>
	├── README.md
	├── app.js (应用服务入口)
	├── config (应用服务配置)
	│   ├── default.json
	│   └── production.json
	├── node_modules
	├── package.json
	├── src
	└── xnosql_modules
	    └── express-xnosql

RESTful规则
>
	[POST]http://host:port/xnosql/MODEL/create
	[POST]http://host:port/xnosql/MODEL/update
	[POST]http://host:port/xnosql/MODEL/query
	[GET]http://host:port/xnosql/MODEL/get/:id
	[GET]http://host:port/xnosql/MODEL/destroy/:id

例子
>
	以一个用户模块为例，需要对用户进行增删改查:
	需要注意的是默认自动创建id,createdAt,updatedAt三个字段，无须人工处理
	[POST]http://host:port/xnosql/user_model/create
		post body:{"username":"cheney","password":"123"}
	[POST]http://host:port/xnosql/user_model/update
		post body:{id:1,"username":"cheney","password":"456"}
	[POST]http://host:port/xnosql/user_model/query
		post body:{"username":"cheney","password":"123"}
	[GET]http://host:port/xnosql/user_model/get/1
	[GET]http://host:port/xnosql/user_model/destroy/1

框架整合（开源力量）
>
    "body-parser": "^1.17.1",
    "config": "^1.25.1",
    "connect-flash": "^0.1.1",
    "express": "^4.15.2",
    "express-session": "^1.15.1",
    "moment": "^2.17.1",
    "mongodb": "^2.2.25",
    "passport": "^0.3.2",
    "passport-local": "^1.0.0",
    "tracer": "^0.8.7"

帮助联系
>
	作者:cheneyxu，chenxingling
	邮箱:457299596@qq.com
	QQ:457299596

更新日志
>
	2017.03.25:无后端理念确认，1.0版本推出
	2017.03.27:使用async...await封装mongodb使用
	2017.04.01:为支持ES7做准备，代码优化
	2017.04.02:以express中间件的形式提供服务，更加高内聚低耦合