# JSP

## 1.什么是JSP

JSP（Java Server Page）是一种用于开发动态Web应用的技术。它允许将Java代码嵌入到HTML中，用于在服务器端生成动态页面内容。JSP可以与Servlet，JavaBean等技术实现复杂的WEB应用

JSP拥有自己的标签库，称之为JSTL（JavaServerPages Standard Tag Liberary）。

## 2.JSP的基本语法

JSP是一种动态的网页技术，它允许在HTML中嵌入Java代码，从而实现动态的内容展示和交互。

### 2.1 脚本

JSP的脚本用于执行任意有效的Java代码，并允许将结果输出在HTML网页上。脚本以<%%>或<%!  %>标记包围，分别表示脚本和声明

```jsp
<%
	int a = 1;
	int b = 2;
	out.print(a + "+" + b + "=" + (a+b));
%>

<%! 
	int c = 3;
%>

<%= "c=" + c %>
```

### 2.2 表达式

JSP表达式用于将Java表达式的结果输出到HTML页面中。表达式以 <%= %>标记包围

```jsp
Hello <%= "World" %>
```

### 2.3 注释

JSP中支持HTML注释和Java注释。

```jsp
<!-- HTML注释 -->
<%-- JSP注释 --%>
<% //单行注释 %>
<%/*多行注释*/%>
```

### 2.4 指令

JSP指令用于设置页面全局属性或引入外部资源。有三种类型：page，include，taglib

指令都是由<%@ %>作为开始

```jsp
<%@ page language="java" contentType="text/html;charset=utf-8"
	pageEncoding="UTF-8"
	import="java.util.*"
	errorPage="/error.jsp"
	isErrorPage="false"
%>

<%@ include file="header.jsp"%>

<%@ taglib prefix="c" uri="http://java.sum.com/jsp/jstl/core" %>
```

