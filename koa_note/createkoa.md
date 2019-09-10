### 本教程来自--[简书](https://www.jianshu.com/p/1a91f36e5153)

#### 使用typescript 和 koa构建node应用

1. 创建基础、安装依赖

	```
	git init  	//初始化git文件

	//安装依赖
	npm init 	//初始化package.json
	npm install -S koa koa-router
	npm install -S typescript ts-node
	npm install -g nodemon
	npm install -S @types/koa @types/koa-router

	```


2. 修改编译配置

 添加`tsconfig.json`配置,为了使用远程的Async/Await ,我们将编译的目标版本设置为`es2017`
	
	```
	 
		{
	    "compilerOptions": {
		"module": "commonjs",
		"target": "es2017",
		"noImplicitAny": true,
		"moduleResolution": "node",
		"sourceMap": true,
		"outDir": "dist",  // TS文件编译后会放入到此文件夹内
		"baseUrl": ".",
		"paths": {
		    "*": [
			"node_modules/*",
			"src/types/*"
		    ]
		}
	    },
	    "include": [
		"src/**/*"
	    ]
	}
	
	 ```
3. 创建koa应用

	```
	import * as Koa from 'koa';
	import * as Router from 'koa-router';

	const app = new Koa();
	const router = new Router();

	router.get('/*', async (ctx) => {
	    ctx.body = 'Hello World!';
	});

	app.use(router.routes());

	app.listen(3000);

	console.log('Server running on port 3000');

	```

4. 启动项目
	
	添加脚本到package.json中

	```
	"scripts":{
		"start": "tsc && node dist/server.js"
	}
	```

	之后我们可以使用命令来启动项目： `npm start`




5. 热更新

	启动脚本如下：
	```
	"scripts": {
	  "start": "tsc && node dist/server.js",
	  "watch-server": "nodemon --watch 'src/**/*' -e ts,tsx --exec 'ts-node' ./src/server.ts"
	}
	```
	之后执行`npm run watch-server` 启动项目
