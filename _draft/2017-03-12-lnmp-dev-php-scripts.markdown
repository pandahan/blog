---
layout: post
title:  "LNMP开发--常用脚本"
date:  "2017-03-12 08:30:40 -0700"
category: lnmp
tags: samba
keywords: samba
description: ""
---


###多个日志文件同时tail
multail.sh
``` shell  
	#multail.sh
	#!/bin/sh

	function clean()
	{
	      #echo $@;
	      #for file in "$@"; do ps -ef|grep $file|grep -v grep|awk '{print [}'|xargs kill -9; done
	        jobs -p|xargs kill -9  
	}
	
	files=$@
	    
	# When this exits, exit all back ground process also.
	#trap &quot;ps -ef|grep tail|grep -v grep|awk '{print &quot;'['&quot;}'|xargs kill -9&quot; EXIT
	
	trap "clean $files" EXIT
	
	# iterate through the each given file names,
	for file in "$@";
	do
	            # show tails of each in background.
	                    tail -f $file &
	                done
	    
	# wait .. until CTRL+C
	wait
	
```