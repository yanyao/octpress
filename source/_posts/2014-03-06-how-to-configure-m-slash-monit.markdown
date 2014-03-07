---
layout: post
title: "how to configure m/monit"
date: 2014-03-06 10:36:54 +0800
comments: true
categories: 
---
M/Monit这边只需要启动就可以
``` bash
wget http://www.mmonit.com/dist/mmonit-3.1.2-macosx-universal.tar.gz
tar xfz mmonit-3.1.2-macosx-universal.tar.gz
cd mmonit-3.1.2
./mmonit
```

Monit需要更改指向该M/Monit的配置，配置在*/etc/monit.conf*.主要需要指定M/Monit的地址
```
set httpd port 2812
    allow <mmonit ip>
    allow localhost
    allow admin:monit      # require user 'admin' with password 'monit'
    allow @monit           # allow users of group 'monit' to connect (rw)
    allow @users readonly  # allow users of group 'users' to connect readonly
set mmonit http://monit:monit@<mmonit ip>:8080/collector
```
***
对于Monit,可以通过`monit`命令来打开或者关闭对于某个服务的监控
``` bash
monit monitor <name>
monit unmonitor <name>

```
