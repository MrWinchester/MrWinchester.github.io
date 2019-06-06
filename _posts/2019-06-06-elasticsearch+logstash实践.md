---
layout:     post
title:      "elasticsearch+logstash实践"
date:       2019-06-06 11:42:00
description: "elasticsearch+logstash实践"
tag :      [elasticsearch,logstash]
---

# 为logstash添加自定义环境变量
* You can set environment variable references in the configuration for Logstash plugins by using ${var}.（可以使用${var}的方式设置环境变量）
* At Logstash startup, each reference will be replaced by the value of the environment variable.（在logstash启动时，会自动替换环境变量）
* The replacement is case-sensitive.（大小写敏感）
* References to undefined variables raise a Logstash configuration error.（如果启动时环境变量未定义会报错）
* You can give a default value by using the form ${var:default value}. Logstash uses the default value if the environment variable is undefined.（可以给环境变量设置默认值，这样在启动时即使没有设置环境变量，也会取默认值，方式：${var:default value}）
* You can add environment variable references in any plugin option type : string, number, boolean, array, or hash.（可以添加任何类型的环境变量）
* Environment variables are immutable. If you update the environment variable, you’ll have to restart Logstash to pick up the updated value.（环境变量是不可变的，如果改了环境变量，请重启logstash）


# 变量放在哪里？
* 新建一个环境变量的文件，类似 environmentExport.sh，文件内容 `export jdbc_driver_library=xxxx`
* 在启动文件中加入这个shell脚本，bin/logstash,头部加入  `. environmentExport.sh`