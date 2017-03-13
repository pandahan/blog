LNMP开发--samba服务

[Samba](https://zh.wikipedia.org/wiki/Samba)是种用来让UNIX系列的操作系统与微软Windows操作系统的SMB/CIFS（Server Message Block/Common Internet File System）网络协议做链接的自由软件。在UNIX系统上配置并开启samba服务后，在windows下映射相应的UNIX目录。这样，在windows下，就像想浏览普通windows路径一样访问UNIX资源。

本文以centos为例，配置samba服务。  
1. centos安装samba  
		`[gongmh@localhost ~]$ sudo yum install samba `
