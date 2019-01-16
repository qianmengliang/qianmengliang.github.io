---
layout:     post
title:      注解@Controller和@RestController的区别
author:     钱梦良
tags: 		SpringMVC  
subtitle:   浅谈@Controller和@RestController的区别
category:  Java框架
---
## @Controller

&nbsp;&nbsp;&nbsp;&nbsp;@Controller是最普通的Spring MVC中的Controller标注形式。
&nbsp;&nbsp;&emsp;在一个类上标注@Controller后，该方法将被当作一个Controller装配到Spring的web上下文中。
&nbsp;&nbsp;&emsp;该类中的处理方法可以使用@RequestMapping标注。并且这些方法通常返回一个String，或者ModelAndView对象，用于与InternalResourceViewResolver配合来定位到具体的视图。这是前后端不分离的视图渲染做法。
&nbsp;&nbsp;&emsp;若该方法要返回一个String类型的JSON对象，则该方法上需要标注@ResponseBody。

```java
@Controller 
public class MyController { } 
```



## @RestController

&emsp;&emsp;@RestController可以理解成@Controller与@ResponseBody结合。

&emsp;&emsp;它只用来标注Restful风格的Controller。这些Controller类会直接返回JSON，XML等。这样做法是前后端分离的常用做法。另外在Restful风格中，我们还经常使用到@PathVariable注解，用来获取路径中的关于资源的信息。

```java
@Controller  
@ResponseBody  
public class MyController { }  
  
@RestController  
public class MyRestController { }
```

## 总结

&emsp;&emsp;如果只是使用@RestController注解Controller，则Controller中的方法无法返回jsp页面，配置的视图解析器InternalResourceViewResolver不起作用，返回的内容就是Return 里的内容。

&emsp;&emsp;例如：本来应该到success.jsp页面的，则其显示success。

&emsp;如果需要返回到指定页面，则需要用 @Controller配合视图解析器InternalResourceViewResolver才行。

&emsp;&emsp;如果需要返回JSON，XML或自定义mediaType内容到页面，则需要在对应的方法上加上@ResponseBody注解。



