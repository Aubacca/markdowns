# Java - Servlet

- <a href="https://www.youtube.com/watch?v=WxeY-LxMIbE&list=PLE0F6C1917A427E96&index=22" target="_blank">YouTube - JSPs and Servlets Tutorial</a>
- <a href="https://www.javatpoint.com/jsp-tutorial" target="_blank">java T point - JSP Tutorial</a>
- <a href="https://www.tutorialspoint.com/jsp/index.htm" target="_blank">tutorialspoint - JSP Tutorial</a>

## Servlets

- Application Object: **javax.servlet.ServletContext**
- Sesson Object: **javax.servlet.http.HttpSession**
- Request Object: **javax.servlet.http.HttpServletRequest**

## Maven Dependency in pom.xml

```xml
  ...
  <dependencies>
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <version>4.0.1</version>
      <scope>provided</scope>
    </dependency>
  </dependencies>
```

## Project web.xml

```xml
<!DOCTYPE web-app PUBLIC
 "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
 "http://java.sun.com/dtd/web-app_2_3.dtd" >

<web-app xmlns="http://java.sun.com/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
	      http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
         version="3.0">

  <display-name>Archetype Created Web Application</display-name>

  <welcome-file-list>
    <welcome-file>index.html</welcome-file>
  </welcome-file-list>

  <servlet>
    <servlet-name>watermelon</servlet-name>
    <servlet-class>ch.renhor.servlets.SimpleServlet</servlet-class>
    <init-param>
      <param-name>version-from-xml</param-name>
      <param-value>2.2.2</param-value>
    </init-param>
    <init-param>
      <param-name>tool-from-xml</param-name>
      <param-value>6.6.6</param-value>
    </init-param>
  </servlet>

  <servlet-mapping>
    <servlet-name>watermelon</servlet-name>
    <url-pattern>/simple/*</url-pattern>
  </servlet-mapping>

  ...

</web-app>
```

## Java Servlet 

### Workflow

- init(ServletConfig) resp. init() {..}: *Once per application* implemented in **GenericServlet**
- service() {..}: *for each servlet call* implemented in **GenericServlet** and extended in **HTTPServlet**
- doGet(), doPost, doPut, ... overwritten in concret servlet implementation

### RequestDispatcher

```java
package ch.renhor.servlets.user;

import ch.renhor.models.User;
import ch.renhor.services.UserService;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebInitParam;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet(urlPatterns = "/user-overview/users",
        initParams = {@WebInitParam(name = "servletVersion", value = "1.0.0"),
                @WebInitParam(name = "servletTool", value = "1.0.0")})
public class UserServlet extends HttpServlet {
    private UserService userService = new UserService();

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        log("doPost>begin");
        final User newUser = new User();
        boolean isValidUser = false;
        String errorMessage = "";
        try {
            newUser.setMail(req.getParameter("mail"));
            newUser.setLastName(req.getParameter("lastName"));
            newUser.setFirstName(req.getParameter("firstName"));
            newUser.setAge(Integer.valueOf(req.getParameter("age")).byteValue());
            newUser.setId(userService.getNextUserId());
            log("doPost>newUser: " + newUser);
            isValidUser = userService.validateUser(newUser);
            userService.addUser(newUser);
        } catch (NumberFormatException e) {
            e.printStackTrace();
        } catch (Exception e) {
            e.printStackTrace();
            errorMessage = e.getMessage();
            log("*** ERROR doPost>" + errorMessage);
        }
        //
        if (isValidUser) {
            log("doPost>correct user data entered.");
            resp.sendRedirect("user-overview.jsp");
        } else {
            log("doPost>invalid user data entered");
            //
/*
            req.getSession().setAttribute("newUser", newUser);
            req.getSession().setAttribute("errorMessage", errorMessage);
            resp.sendRedirect("user-add.jsp");
*/
            //
            req.setAttribute("newUser", newUser);
            req.setAttribute("errorMessage", errorMessage);
            final RequestDispatcher requestDispatcher = req.getRequestDispatcher("user-add.jsp");
            requestDispatcher.forward(req, resp);
        }
        log("doPost>end");
        return;
    }
}
```

### Example - doGet

```java
package ch.renhor.servlets;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

@WebServlet(description = "A simple servlet", urlPatterns = "/SimpleServlet",
        initParams = {@WebInitParam(name = "servletVersion", value = "1.1.1"),
                @WebInitParam(name = "tool", value = "5.5.5")})
public class SimpleServlet extends HttpServlet {
    private final String SERVLET_VERSION = "servletVersion";
    private final String SERVLET_TOOL = "servletTool";
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        PrintWriter writer = resp.getWriter();
        resp.setContentType("text/html");
        writer.println("<h2>This is the SimpleServlet of this app</h2>");
        writer.println("<hr>");
        writer.println("<p>Servlet Version via Annotation: <b>" + getServletConfig().getInitParameter(SERVLET_VERSION) + "</b></p>");
        writer.println("<p>Servlet Tool via Annotation: <b>" + getServletConfig().getInitParameter(SERVLET_TOOL) + "</b></p>");
    }
}
```

### JSP - Java Servlet Page

- <a href="http://cs.roosevelt.edu/eric/books/JSP/JSPquickref.pdf" target="_blank">JSP Quick Reference Card</a>
- <a href="https://www.javatpoint.com/jsp-tutorial" target="_blank">Java T Point- JSP Tutorial</a>
- <a href="http://pdf.coreservlets.com/first-edition/CSAJSP-Appendix.pdf" target="_blank">Servlet and JSP Quick Reference</a>
- <a href="https://www.tutorialspoint.com/jsp/pdf/jsp_directives.pdf" target="_blank">JSP - DIRECTIVES</a>

## JSP - Standard Tag Library (JSTL)

- JSTL - Core Tags

```xml
  <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

- JSTL - Formatting Tags

```xml
  <%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
```

- JSTL - SQL Tags

```xml
  <%@ taglib prefix="sql" uri="http://java.sun.com/jsp/jstl/sql" %>
```

- JSTL - XML tags

```xml
  <%@ taglib prefix="x" uri="http://java.sun.com/jsp/jstl/xml" %>
```

- JSTL - JSTL Functions

```xml
  <%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions" %>
```
