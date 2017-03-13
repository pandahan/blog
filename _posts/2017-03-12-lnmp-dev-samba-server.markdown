LNMP开发--samba服务

[Samba](https://zh.wikipedia.org/wiki/Samba)是种用来让UNIX系列的操作系统与微软Windows操作系统的SMB/CIFS（Server Message Block/Common Internet File System）网络协议做链接的自由软件。在UNIX系统上配置并开启samba服务后，在windows下映射相应的UNIX目录。这样，在windows下，就像想浏览普通windows路径一样访问UNIX资源。

本文以centos为例，配置samba服务。  

###centos处理  
1. centos安装samba  
		`[gongmh@localhost ~]$ sudo yum install samba `  
2. 添加samba用户  
		`smbpasswd -a gongmh`  
3. 配置samba  
		`echo -e "\n[mydisk]\n\tcomment = Home Directories\n\tbrowseable = no\n\twritable = yes\n\tpath=/home/gongmh\n\tvalid users =gongmh\n" >> /etc/samba/smb.conf`  
4. 启动samba服务  
		`sudo service smb start`  
		`service smb status`
5. 处理权限限制  

###windows处理  
1. 创建【映射网络驱动器】，配置\\ip\samba_name

2. 输入账号、密码连接服务
	![pic](https://cl.ly/2O2j0H2E2E42)  
	![pic](https://cl.ly/3q0Y3o0D1A2x)  
done
