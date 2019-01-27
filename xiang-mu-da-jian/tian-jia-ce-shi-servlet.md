# 在Maven构建的项目中添加测试Servlet

首先建立文件夹

![](/assets/屏幕快照 2019-01-27 下午3.35.54.png)

同时，建立一个Servlet，在这个过程中，你会发现，你建立的Java文件夹的颜色是和cn.liupengstudy文件夹一个颜色的，而且无法建立Java类。不要着急，你只需要看下面的图片即可知道如何搞！

![](/assets/屏幕快照 2019-01-27 下午2.34.32.png)

按照上图的方法，即可完成对文件夹的分化。你就可以建立Java类了。

## 建立一个servlet

然后建立一个servlet

### 代码如下：


```
package cn.liupengstudy;

import java.io.IOException;

public class MavenServlet extends javax.servlet.http.HttpServlet {
    protected void doPost(javax.servlet.http.HttpServletRequest request, javax.servlet.http.HttpServletResponse response) throws javax.servlet.ServletException, IOException {
        response.getWriter().write("hello maven");
    }

    protected void doGet(javax.servlet.http.HttpServletRequest request, javax.servlet.http.HttpServletResponse response) throws javax.servlet.ServletException, IOException {
        doPost(request,response);
    }
}

```

### 同时配置xml



```
<servlet>
    <servlet-name>MavenServlet</servlet-name>
    <servlet-class>cn.liupengstudy.MavenServlet</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>MavenServlet</servlet-name>
    <url-pattern>/maven</url-pattern>
  </servlet-mapping>
```

但是，这里会报错的，因为你没有servlet的jar包

所以，你需要添加，我们使用Maven的机制添加Jar包。

## 使用Maven的机制添加Jar包

### 配置pom.xml文件

添加代码

```
<!-- 添加Servlet -->
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>servlet-api</artifactId>
      <version>2.5</version>
      <scope>provided</scope>
    </dependency>
```

然后，去这里解决问题：

![](/assets/屏幕快照 2019-01-27 下午3.24.15.png)

或者，如果没有解决问题，会出现这样的一个对话框

![](/assets/屏幕快照 2019-01-27 下午3.25.13.png)

点击“Improt Changes”即可完成对jar包的添加。

最后的效果：

![](/assets/屏幕快照 2019-01-27 下午3.25.32.png)


