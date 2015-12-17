###安装

```
npm install mproxy -g
```

###启动


```
mproxy  

```

###后台启动(linux)

```
nohup mproxy  &

```

###启动参数

```
	/*
		//常用参数
		p=9999			--代理监听端口，默认9999
		b=ip:port		--桥接代理地址，默认空
		t=normal		--代理类型（bridge | tunnel | node | normal）,默认normal
						--bridge 该代理仅有下级代理，下级代理地址通过--b传入，发送数据启用TLS
						--tunnel 该代理有上下级代理，接收和发送均启用TLS
						--node 该代理仅有上级代理，接收启用TLS

		//密钥对
		cert=""			--公钥路径，默认使用系统自带
		key=""			--私钥路径，默认使用系统自带

		//操作参数
		save			--保存本次启动参数，下次可省略，默认不保存
		kill			--kill已启动的mproxy(linux)，默认不kill
		debug			--打印调试信息，默认不打印
	*/
	//不完整示例
	mproxy -p=9999  -b=127.0.0.1:9998 -t=bridge --kill  --save

```

###代理桥接

你可以将部署在不同服务器上的mproxy桥接起来

```
mproxy --b=服务器IP:服务器端口

```

###加密传输

```
	/*
		mproxy会自动学习，在两个mproxy之间使用TLS加密传输
		建议主动申明代理的类型[bridge,tunnel,node,normal]
		建议传入cert和key参数，使用openssl生成自定义密钥对
	*/

```





