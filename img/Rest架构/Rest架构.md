---
title: Rest架构风格
translate_title: rest-architecture-style
---

## Rest是什么?

``` bash
REST(Representational State Transfe),是一种软件架构风格，它结构清晰、符合标准、易于理解、扩展方便，并且规范了URI的风格；规范了HTTP请求动作的使用，具有对应的语义。Spring支持并推荐使用这种风格的URL地址。他可以处理除POST或GET的其他请求.
rest可以把普通的请求转化(如:GET.POST)为规定形式的请求(DELETE等等),使URL请求地址状态化.
```

<!-- more -->

## Rest实现

### 配置web.xml文件,添加一个Filter过滤器
  
``` bash
<filter>
    <!--HiddenHttpMethodFilter继承HttpServletRequest类-->
    <filter-name>HiddenHttpMethodFilter</filter-name>
    <filter-class>org.springframework.web.filter.HiddenHttpMethodFilter</filter-class>
  </filter>
  <filter-mapping>
    <filter-name>HiddenHttpMethodFilter</filter-name>
    <url-pattern>/*</url-pattern>
  </filter-mapping>

  
   <!--要想获取其他类型的请求,要先创建一个form表单-->
<form action="pojo/1" method="post">
    <!--添加一个_method参数,它的值就是请求的类型-->
    <input name="_method" value="delete">
    <input type="submit" value="删除请求">
  </form>
```

## 注意

### ≥8.0版本的Tomcat服务器Filter会拦截JSP页面,这种情况需要在index.jsp页面加上这个约定.isErrorPage="true"

``` bash
<%@ page language="java" contentType="text/html; charset=UTF-8"
  pageEncoding="UTF-8"% isErrorPage="true">
  ```

## 没有HiddenHttpMethodFilter的提示话,需要绑定源码jar包.

微信公众号:每日学习干货