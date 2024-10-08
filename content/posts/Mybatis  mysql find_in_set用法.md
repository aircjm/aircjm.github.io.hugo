---
cards-deck: Default
createAt: 2022-09-26 15:32:38
draft: false
publish: true
title: "Mybatis  mysql find_in_set\u7528\u6CD5"
updateAt: 2022-09-26 15:32:38
---
tags: #mybatis 


```xml
     <if test="requestVO.responsible != null">
        and find_in_set(#{requestVO.responsible}, t.responsible)
    </if>
```