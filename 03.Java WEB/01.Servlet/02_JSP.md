# JSP

## 1.什么是JSP

JSP（Java Server Page）是一种用于开发动态Web应用的技术。它允许将Java代码嵌入到HTML中，用于在服务器端生成动态页面内容。JSP可以与Servlet，JavaBean等技术实现复杂的WEB应用

JSP拥有自己的标签库，称之为JSTL（JavaServerPages Standard Tag Liberary）。

JSP的基本流程

![](Images\JSP\01.jpg) 

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

### 2.5 EL表达式

EL(Expression Language)是一款用于简化JSP页面开发的表达式语言，它可以在JSP页面中直接使用，更方便的对数据进行展示和处理。

EL表达式主要是获取作用域中的数据，按照pageScore,requestScore,sessionScope,applicationScore的顺序进行获取

1.值 表达式

​	${userName}

2.方法表达式

​	${user.getName()}

3.集合表达式

​	${list[0]}

4.对象属性表达式

​	${user.name}

5.空值表达式

​	${empty userList}

6.条件表达式

​	${isAllowed ? '同意','不同意'}

## 3.JSP内置对象

JSP内置对象指的是在JSP页面中可以不用声明直接使用的一些Java对象，它们的作用是提供了方便的快捷的方法来获取和处理请求，响应以及其他与JSP页面相关的信息。JSP内置对象主要包含下面9种。

1.request : 表示客户端发出的HTTP请求信息，并封装到一个对象中

2.response：表示服务器端对客户端的请求的响应信息，并封装到一个对象中

3.pageContext：表示页面上下文信息，并封装到一个对象中

4.session：表示客户端和服务器之间的会话信息并封装到一个对象中

5.application：表示Servlet上下文信息，并封装到一个对象中

6.out：表示页面的输出流

7.config：表示当前的servlet的配置信息，并封装到一个对象中

8.exception：表示页面抛出的异常信息

9.page：表示当前页面本身

## 4.JSTL

JSTL（JSP Standard Tag Liberary）是一套标准的JSP标签库，使得JSP页面变得更加简单和高效。

JSTL分类：

1.核心标签库

2.格式化标签库

3.SQL标签库

4.XML标签库

5.JSTL函数

注意：使用JSTL之前需要导入 standard.jar 以及 jstl.jar两个jar文件

在使用JSTL标签之前 ，在使用的页面上需要将对应的引用导入到jsp中

<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>

<%@ taglib uri="http://java.sun.com/jsp/jstl/fmt" prefix="fmt" %>

<%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn" %>

### 4.1 核心标签库

<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>

核心标签库中有13个标签，分为4类

1.表达式控制：out,set,remove,catch

2.流程控制：if,choose,when,otherwise

3.循环：forEach,forTokens

4.URL操作标签：url,import ,redirect



#### 4.1.1 表达式控制标签

##### 1.out标签

作用：

​	输出常量，可以在value属性中直接赋值输出。

​	输出变量，通过var属性来设置变量的值，如果变量不存在的话则可以通过default属性输出默认值。

​	可以通过escapeXml来控制转义字符。

```jsp
<%-- 输出常量的值 --%
<c:out value="我是out标签输出的值"></c:out>
<%-- 输出变量的值 --%>
<c:out value="${sessionScope.name}"></c:out>
```

##### 2.set标签

作用：

​	存数据到scope中，可以将数据以就是的形式存放在指定的范围。scope用于设定存放值的范围，value指定存放值的内容。var用于指定存放的变量。

```jsp
<c:set scope="session" var="name" value="test"></c:set>
```

​	存数据到JavaBean中，target用于指定javabean的对象。property用于指定赋值给javabean的哪个属性。value指定存放值的内容。

```jsp
<%-- 引入实体类实例化对象 --%>
<jsp:useBean id="user" class="com.zx.entity"></jsp:useBean>
<%-- 为实例化的name属性赋值 --%>
<c:set target="${user}" property="name" value="test" />
```

##### 3.remove标签

作用：移除指定scope作用域内的变量。var属性是必选的。scope属性是必选的。如果不同的scope中存在相同的就是而要指定移除哪个scope中的数据 。

```jsp
<c:remove scope="session" var="name"></c:remove>
```

##### 4.if标签

作用：用来实现分支条件的控制。test属性用来存放判断条件，一般用EL表达式来写。var属性用于存放判断结果类型为true还是false。scope属性用来存放var属性存放的范围。

```jsp
<c:if test="${param.score>=90}" var="result" scope="session"></c:if>
```

