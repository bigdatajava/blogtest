---
layout:     post
title:      "SpringBoot整合Mybatis打印SQL语句在控制台"
date:       2019-02-12 12:00:01 +0800
categories:	技术
tags:	SpringBoot
---


* content
{:toc}




#### 1.application.properties

格式：logging.level.接口dao类所在包=DEBUG

```
logging.level.com.chao.dao=DEBUG
```

#### 2.application.yml

格式：
logging:
​    level:
​      接口dao类所在包: DEBUG 

```
logging:
    level:
      com.threefivework.mymall.dao.mapper: DEBUG 
```

著作权声明：本文首次发布于 [刘自超](https://liuwc.xyz)，转载请保留以上链接