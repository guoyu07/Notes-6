# 错误处理

## 包缺失

> Package 'vim' has no installation candidate

---

需要更新 apt-get 的镜像源

1. 打开配置文件

	```shell
	sudo vi /etc/apt/sources.list
	```

2. 使用新的镜像源，如，使用 Aliyun 的镜像

	```
	#deb http://mirrordirector.raspbian.org/raspbian/ jessie main contrib non-free rpi
	# Uncomment line below then 'apt-get update' to enable 'apt-get source'
	#deb-src http://archive.raspbian.org/raspbian/ jessie main contrib non-free rpi
	deb http://mirrors.aliyun.com/raspbian/raspbian/ wheezy main non-free contrib
	```
	
3. 更新包列表

	```shell
	sudo apt-get update
	sudo apt-get upgrade
	```

4. 再次安装

	```shell
	sudo apt-get install vim
	```

## 包损坏

> Unable to correct problems, you have held broken packages.


```shell
sudo apt-get remove vim-common # 引起错误的包
sudo apt-get clean && sudo apt-get purge
sudo apt-get update && sudo apt-get install vim
```

## 远程连接出错

> WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
> ...
> ECDSA host key for xxx.xxx.x.xxx has changed and you have requested strict checking

清除之前的缓存

```shell
ssh-keygen -R xxx.xxx.x.xxx
```

