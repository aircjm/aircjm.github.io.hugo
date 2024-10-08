---
cards-deck: Default
createAt: 2022-04-27 09:56:26
draft: false
publish: true
title: "Spring logback-spring.xml logback.xml\u533A\u522B"
updateAt: 2022-04-27 09:56:26
---

tags:  #spring  #日志 #todo 


logback.xml，logback-spring.xml的区别
如果在xml中要使用 spring的配置，例如这样 获取对应的appName
```xml
<springProperty scope="context" name="springAppName" source="spring.application.name"/>
```
则必须使用文件名为：logback-spring.xml
不然就会出现 获取不到的情况
例如：
![Pasted_image_20220427095921.png](/images/Pasted_image_20220427095921.png)

这个就会出现APP_NAME_IS_UNDEFINED的情况 如果改成 logback-spring.xml


- [ ] [[2022-04-28]] 学习下[[spring加载各个配置文件的顺序]] 例如yml,properties, xml





