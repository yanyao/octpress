---
layout: post
title: "knife-solo"
date: 2014-02-11 17:54:24 +0800
comments: true
categories: [chef, knife, knife-solo]
---

`knife-solo`
是knife的一个插件。主要是用在没有chef-server的情况下，代替一部分chef-server的功能。其实本质就是将chef中的cookbook、data bag、roles的信息传递给chef-client，之后再调用目标节点上的`chef-solo`程序。`knife-solo`本身主要包括以下三个命令：

*`knife solo init DIRECTORY`*

用来设置knife-solo的工作环境，这个命令需要一个目录作为输入.这个命令的作用类似于chef构架中的workstation. 所以在这个目录上，我们可以调用`knife`源生命令`cookbook`、`data bag`以及`role`。
``` bash
$knife solo init solo
$tree solo
.
├── cookbooks
├── data_bags
├── nodes
├── roles
├── site-cookbooks
└── solo.rb
```

*`knife solo prepare user@hostname`*
        
`prepare`命令主要是在目标节点上安装`chef-client`。这个命令之后就需要给该节点制定一个`run_list`了。在`knife
sole
init`之后，会产生一个`nodes`的目录，该目录将要存放各个目标节点的`run_list`的配置文件。节点对应的文件是该节点的IP地址或者主机名命名的。例如主机`192.168.1.33`所对应的文件是`nodes/192.168.1.33.json`。该文件是json格式的。

        {"run_list":["recipe[test]"]}

该配置只包含了一个recipe，多个recipe或者role都可以添加在里面。

*`knife solo cook user@hostname`*
        
`cook`
命令主要是在目标节点上执行`chef-solo`命令。也就是将`run_list`里面对应的cookbook展开，实现cookbook定义的行为。




