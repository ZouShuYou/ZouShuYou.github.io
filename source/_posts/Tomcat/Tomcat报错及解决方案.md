---
layout:     post
title:      "Tomcat报错及解决方案"
date:       2021-10-25
author:     "Zsy"
tags:      
    - tomcat
---

最近试着在wsl2中使用docker跑公司的web项目，但是tomcat容器会报错

# 报错

```xml
 java.lang.illegalargumentexception the main resource set specified [...] is not valid in Tomcat
```

# 解决方案

将 %CATALINA_HOME%/conf/server.xml 中的

```xml
<Context docBase="" path="/web" reloadable="false" />
```
删除掉

并在 %CATALINA_HOME%/conf/Catalina/localhost 中创建 ROOT.xml 文件 ，写入以下内容

```xml
<Context docBase="<yourApp>" path="/web" reloadable="false" />
```

我本机是成功解决了报上述错的问题。

参考：
[How to solve common problems when using Tomcat](https://ducmanhphan.github.io/2020-01-09-How-to-solve-common-problems-when-using-Tomcat/)