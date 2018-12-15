---
layout:     post
title:      SpringMVC工作原理
author:     钱梦良
tags: 		SpringMVC  
subtitle:   浅谈SpringMVC工作原理
category:  Java框架
---
## SpringMVC的工作原理

&emsp;&emsp;1、用户向服务器发送请求，请求被 springMVC 前端控制器 DispatchServlet 捕获；

&emsp;&emsp;2、DispatcherServle 对请求 URL 进行解析，得到请求资源标识符（URL），然后根据该 URL 调用 HandlerMapping将请求映射到处理器 HandlerExcutionChain； 

&emsp;&emsp;3、DispatchServlet 根据获得 Handler 选择一个合适的 HandlerAdapter 适配器处理； 

&emsp;&emsp;4、Handler 对数据处理完成以后将返回一个 ModelAndView（）对象给 DisPatchServlet; 

&emsp;&emsp;5、Handler 返回的 ModelAndView()只是一个逻辑视图并不是一个正式的视图，DispatcherSevlet 通过ViewResolver 试图解析器将逻辑视图转化为真正的视图 View; 

&emsp;&emsp;6、DispatcherServle 通过 model 解析出 ModelAndView()中的参数进行解析最终展现出完整的 view 并返回给客户端; 



