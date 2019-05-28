---
layout:     post
title:      "springboot单元测试-报错解决"
date:       2019-05-27 12:00:01 +0800
categories:	问题解决
tags:	springboot
---


* content
{:toc}




### 1.报错日志

![](https://github.com/bigdatajava/blogtest/raw/master/styles/images/springboot-error1.png)

### 2.解决方法

如异常所译，你需要在注解上加上

@SpringBootTest(classes = Application.class)
或者使用

> @RunWith(SpringJUnit4ClassRunner.class)
> @ContextConfiguration(classes = {JPAConfig.class})
> or
>
> @RunWith(SpringRunner.class)
> @ContextConfiguration(classes = {JPAConfig.class})
> or
>
> @RunWith(SpringJUnit4ClassRunner.class)
> @ContextConfiguration(value={"myJPAConfig.xml"})
> or
>
> @RunWith(SpringRunner.class)
>
> @ContextConfiguration(value={"myJPAConfig.xml"})



著作权声明：本文首次发布于 [other](<https://blog.csdn.net/csdn_am/article/details/79757097>)，转载请保留以上链接