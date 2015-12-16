###安装

```
npm install mproxy -g
```

###启动


```
mproxy --p=777  

```

###后台启动(linux)

```
nohup mproxy --p=777  &

```

###启动参数

```
	/*
		p=777			--代理监听端口，必选
		m=middleware	--中间件文件路径，可选
		b=x.x.x.x:777	--桥接代理地址，可选
		n=mproxy		--代理名称，将传给下一个代理
		save			--保存本次启动参数，下次可省略
		kill			--kill已启动的mproxy(linux)
		track			--打印转发信息，默认不打印
	*/
	//完整示例
	mproxy -p=777 -m=middleware -b=192.168.0.1:777 -n=mproxy --kill --track --save

```

###桥接

你可以将部署在不同服务器上的mproxy桥接起来

```
mproxy --b=服务器IP:服务器端口

```

###中间件

```
module.exports = function(request,response,next){
	
	//你的代码
	
	/*
		你可以通过request读取或修改这些值来改变你的请求
		request.url,请求地址，字符串,如有修改请更新request.headers['Host']
		request.headers,请求头，Key-Value对象
		request.body,请求体，Buffer
		request.address,目标地址，字符串，格式："IP:端口"，比如："xx.xx.xx.xx:80"
		request.cookies,Key-Value对象,修改无效，修改cookie请设置request.headers['Cookie']
	*/

	/*
		你可以通过response来向客服端直接输出内容
		response.write,向客户端写入内容
		response.end,向客户端写入内容并关闭
	*/

	//如果需要继续执行下去，主动调用next。如有异步操作请在异步回调函数中调用
	next()
}

```


