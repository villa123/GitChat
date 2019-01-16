### 第01课：Spring IoC 初识

**(1) IoC 属于哪种设计模式？**

A. 单例模式  
B. 原型模式  
C. 工厂模式  
D. 适配器模式  

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：C</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>



**(2) 谈谈你对 Spring IoC 和 DI 的理解，它们有什么区别？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

IoC：Inverse of Control，反转控制的概念，就是将原本在程序中手动创建 UserService 对象的控制权，交由 Spring 框架管理，简单说，就是创建 UserService 对象控制权被反转到了 Spring 框架。

DI：Dependency Injection，依赖注入，在 Spring 框架负责创建 bean 对象时，动态地将依赖对象注入到 bean 组件。

</details>



**(3) 简单谈谈 IoC 容器的原理。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：IoC 容器在加载时对 XML 配置文件进行解析，获取所有的 bean 配置，结合 bean 中的信息（实体类、属性），通过反射机制来创建实例化对象并完成成员变量的赋值操作。最后以键值对的形式将创建好的实例化对象存入容器。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>



**(4) 实例化对象的 name 值为 <张三>，配置文件中 property 的 value 属性应该配置为\_\_\_\_\_\_ ？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：`<![CDATA[<张三>]]>`</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 通过 Student 的运行时的类来获取 IoC 容器中的对象，配置文件中可以配置两个 Student 的实例，这句话正确吗？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：错误。</p>
    <dl>
        <dt>解析：此方法有一个弊端，当 spring.xml 中配置两个 Student 的 bean 时程序报错，因为此时两个 bean 都是由 Student 类生成的，IoC 容器无法将两个 bean 都返回，必须指定一个唯一的 bean，否则会抛出异常。</dt>
        <dd></dd>
    </dl>
</details>


### 第02课：Spring IoC 依赖注入与 p 命名空间

**(1) bean 的 scope 有几种类型？请详细列举。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：共有 4 种。</p>

- singleton：单例，表示通过 Spring 容器获取的该对象是唯一的。
- prototype：原型，表示通过 Spring 容器获取的对象都是不同的。
- reqeust：请求，表示在一次 HTTP 请求内有效。
- session：会话，表示在一个用户会话内有效。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>



**(2) BeanFactory 接口和 ApplicationContext 接口有什么区别 ？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：ApplicationContext 接口继承 BeanFactory 接口，Spring 核心工厂是 BeanFactory，BeanFactory 采取延迟加载，第一次 getBean 时才会初始化 bean，ApplicationContext 会在加载配置文件时初始化 bean。</p>

ApplicationContext 是对 BeanFactory 扩展，它可以进行国际化处理、事件传递和 bean 自动装配，以及各种不同应用层的 Context 实现，开发中基本都在使用 ApplicationContext。Web 项目使用 WebApplicationContext，很少用到 BeanFactory。

</details>



**(3) 说说 IoC 中的继承和 Java 继承的区别。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：IoC 中继承是对象层面的，指继承对象可以获取被继承对象的所有成员变量值，并赋给其对应的成员变量。Java 中的继承是类层面的，指子类可以获取父类的非私有成员变量和方法，不需要再次定义。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) IoC 中对象继承来的属性值不能进行覆盖，这句话正确吗？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：错误，可以进行覆盖。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) IoC 中 car 对象的配置如下，现在要添加 user 对象，并且将 car 注入到 user 中，正确的配置是（）**

```
<bean id="car" class="com.southwind.entity.Car"></bean>
```

A.   
```
<bean id="user" class="com.southwind.entity.User">
    ​	<property name="car" value="car"></property>
</bean>
```

B.   
```
<bean id="user" class="com.southwind.entity.User">
    ​	<property name="car" ref="car"></property>
</bean>
```

C.   
```
<bean id="user" class="com.southwind.entity.User" p:car-ref="car"></bean>
```

D.   
```
<bean id="user" class="com.southwind.entity.User" p:car="car"></bean>
```


<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：BC</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


### 第03课：Spring IoC 工厂方法+自动装载

**(1) IoC 静态工厂方法至少需要配置一个 bean，实例工厂方法至少需要配置两个 bean，这句话对吗？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：正确。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 请写出静态工厂方法的配置。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```
<!-- 配置静态工厂创建 car 对象 -->

    <bean id="car1" class="com.southwind.entity.StaticCarFactory" factory-method="getCar">
    <constructor-arg value="1"></constructor-arg>
    </bean>
```
    
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>

**(3) 请写出实例工厂的配置。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

```
<!-- 配置实例工厂对象 -->

    <bean id="carFactory" class="com.southwind.entity.InstanceCarFactory"></bean>
    <!-- 通过实例工厂对象创建 car 对象 -->
    <bean id="car2" factory-bean="carFactory" factory-method="getCar">
    <constructor-arg value="2"></constructor-arg>
    </bean> 
```

<dl>
        <dt></dt>
        <dd></dd>
</dl>
</details>

**(4) IoC 自动装载有几种方式？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：两种。</p>

- byName：通过属性名自动装载。
- byType：通过属性对应的数据类型自动装载。
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




**(5) 如果通过 byType 进行自动装载，IoC 容器中只能有一个实例化对象，这句话对吗？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：正确。</p>
    <dl>
        <dt>解析：如果配置了两个实例化对象，IoC 容器不知道应该选择哪一个，所以会抛出异常。</dt>
        <dd></dd>
    </dl>
</details>



### 第04课：Spring ioC 基于注解的开发

**(1) bean 注入属性有哪几种方式？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
- spring 支持构造器注入和 setter 方法注入。
- 构造器注入，通过 `<constructor-arg>` 元素完成注入。
- setter 方法注入， 通过 `<property>` 元素完成注入。
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 介绍一下 Spring 框架中 bean 的生命周期。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
1.bean 定义：在配置文件里面用 `<bean></bean>` 来进行定义。

2.bean 初始化，有两种方式：

  - 在配置文件中通过指定 init-method 属性来完成。
  - 实现 org.springframwork.beans.factory.InitializingBean 接口。

3.bean 调用。

4.bean 销毁，销毁有两种方式：

  - 使用配置文件指定的 destroy-method 属性。
  - 实现 org.springframwork.bean.factory.DisposeableBean 接口。    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 基于注解的具体步骤是什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
- 第一步：将目标类自动扫描到 IoC 容器中。
- 第二步：在类中设置注解完成依赖注入。    
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 自动扫描的代码是什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

```
<!-- 将类扫描到 IoC 容器中 -->
<context:component-scan base-package="com.southwind"></context:component-scan>
```

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>



**(5) IoC 容器自动完成装载，默认是\_\_\_\_\_\_的方式。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：byType</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第05课：Spring MVC 快速入门

**(1) 简单谈谈你对 MVC 的理解。**
<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：MVC 设计模式是一种常用的软件架构方式，以Controller（控制层）、Model（模型层）、View（视图层）三个模块分离的形式来组织代码。</p>
    
MVC 工作流程：控制层接受到客户端请求，调用模型层生成业务数据，传递给视图层，将最终的业务数据和视图响应给客户端做展示。
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 什么是 Spring MVC ？简单介绍下你对 Spring MVC 的理解？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：Spring MVC 是一个基于 MVC 架构的、用来简化 Web 应用程序开发的应用开发框架。它是 Spring 的一个模块，无需中间整合层来整合，它和 Struts2 一样都属于表现层的框架。在 Web 模型中，MVC 是一种很流行的框架，通过把 Model、View、Controller 分离，把较为复杂的 Web 应用分成逻辑清晰的几部分，简化开发，减少出错，方便组内开发人员之间的配合。</p>
    

    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) Spring MVC 的优点有哪些？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- 基于组件技术，全部的应用对象，无论控制器和视图还是业务对象，都是 Java 组件，并且和 Spring 提供的其他基础结构紧密集成。
- 不依赖于 Servlet API（目标虽是如此，但是在实现的时候确实是依赖于 Servlet 的）。
- 可以任意使用各种视图技术，而不仅仅局限于 JSP。
- 支持各种请求资源的映射策略。
- 易于扩展。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) Spring MVC 和 Struts 2 的区别有哪些？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- Spring MVC 的入口是一个 Servlet 即前端控制器（DispatchServlet），而 Struts 2 入口是一个 filter 过虑器（StrutsPrepareAndExecuteFilter）。
- Spring MVC 是基于方法开发 (一个 URL 对应一个方法)，请求参数传递到方法的形参，可以设计为单例或多例 (建议单例)，Struts 2 是基于类开发，传递参数是通过类的属性，只能设计为多例。
- Struts 2 采用值栈存储请求和响应的数据，通过 OGNL 存取数据，Spring MVC 通过参数解析器是将 request 请求内容解析，并给方法形参赋值，将数据和视图封装成 ModelAndView 对象，最后又将 ModelAndView 中的模型数据通过 request 域传输到页面。JSP 视图解析器默认使用 JSTL。 

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) Spring MVC 的核心入口类是\_\_\_\_\_\_。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：DispatchServlet</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


### 第06课：Spring MVC 底层实现

**(1) Spring MVC 的核心组件有哪些？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

*   DispatcherServlet：前端控制器，是整个流程控制的核心，控制其他组件的执行，统一调度，降低组件之间的耦合性，相当于总指挥。
*   Handler：处理器，完成具体业务逻辑，相当于 Servlet 或 Action。
*   HandlerMapping：DispatcherServlet 接收到请求之后，通过 HandlerMapping 将不同的请求分发到不同的 Handler。
*   HandlerInterceptor：处理器拦截器，是一个接口，如果我们需要做一些拦截处理，可以来实现这个接口。
*   HandlerExecutionChain：处理器执行链，包括两部分内容，Handler 和 HandlerInterceptor（系统会有一个默认的 HandlerInterceptor，如果需要额外拦截处理，可以添加拦截器设置）。
*   HandlerAdapter：处理器适配器，Handler 执行业务方法之前，需要进行一系列的操作，包括表单数据的验证、数据类型的转换、将表单数据封装到 JavaBean 等，这一系列的操作，都是由 HandlerAdapter 来完成，DispatcherServlet 通过 HandlerAdapter 执行不同的 Handler。
*   ModelAndView：装载了模型数据和视图信息，作为 Handler 的处理结果，返回给 DispatcherServlet。
*   ViewResolver：视图解析器，DispatcherServlet 通过它将逻辑视图解析成物理视图，最终将渲染结果响应给客户端。

    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>

**(2) Spring MVC 的实现流程是什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

1.  客户端请求被 DispatcherServlet（前端控制器）接收。
2.  根据 HandlerMapping 映射到 Handler。
3.  生成 Handler 和 HandlerInterceptor（如果有则生成）。
4.  Handler 和 HandlerInterceptor 以 HandlerExecutionChain 的形式一并返回给 DispatcherServlet。
5.  DispatcherServlet 通过 HandlerAdapter 调用 Handler 的方法做业务逻辑处理。
6.  返回一个 ModelAndView 对象给 DispatcherServlet。
7.  DispatcherServlet 将获取的 ModelAndView 对象传给 ViewResolver 视图解析器，将逻辑视图解析成物理视图 View。
8.  ViewResolver 返回一个 View 给 DispatcherServlet。
9.  DispatcherServlet 根据 View 进行视图渲染（将模型数据填充到视图中）。
10.  DispatcherServlet 将渲染后的视图响应给客户端。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) XML 是什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：XML 即可扩展标记语言（Extensible Markup Language），你可以根据自己的需要扩展 XML。XML 中可以轻松定义 `<books>`、`<orders>` 等自定义标签，而在 HTML 等其他标记语言中必须使用预定义的标签，比如 `<p>`，而不能使用用户定义的标签。使用 DTD 和 XML Schema 标准化 XML 结构。XML 主要用于从一个系统到另一系统的数据传输，比如企业级应用的客户端与服务端。</p>

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 分别说说反射的优缺点。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- 优点：反射提高了程序的灵活性和扩展性，在底层框架中使用较多，业务层开发尽量少用。
- 缺点：性能不高，反射是一种解释操作，用于属性和方法接入时大大慢于直接代码。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 反射机制的作用。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- 在运行时判断任意一个对象所属的类。
- 在运行时构造任意一个类的对象。
- 在运行时判断任意一个类所具有的成员变量和方法。
- 在运行时调用任意一个对象的方法。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第07课：Spring MVC 注解

**(1) @requestMapping 只能修饰方法，不能修饰类，这句话是否正确？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：错误。</p>
    <dl>
        <dt>解析：@requestMapping 既可以修饰方法，也可以修饰类。</dt>
        <dd></dd>
    </dl>
</details>


**(2) @requestMapping 的默认属性是\_\_\_\_\_\_。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：value</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) @requestMapping(value="paramsTest",params={"name","id=10"}) 此注解表示什么意思？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：表示要调用 paramsTest 方法，HTTP 请求中必须包含 name 和 id 两个参数，并且 id 参数的值必须是 10，name 参数的值没有要求。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) Spring MVC 的参数绑定是由\_\_\_\_\_\_来完成的。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：HandlerAdapter</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) Spring MVC 怎么设定重定向和转发？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
  - 在返回值前面加 "forward:" 就可以让结果转发，譬如 "forward:user.do?name=zhangsan"。
  - 在返回值前面加 "redirect:" 就可以让返回值重定向，譬如 "redirect:index.jsp"。    
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


### 第08课：Spring MVC 数据绑定

**(1) @ResponseBody 注解的作用？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：@ResponseBody 注解直接返回字符串到前端，不需要返回 JSP 页面。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 如何解决 POST 请求中文乱码问题，GET 的又如何处理呢？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

解决 POST 请求乱码问题，在 web.xml 中加入：

```xml
    <filter>
        <filter-name>CharacterEncodingFilter</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>utf-8</param-value>
        </init-param>
    </filter>
    
    <filter-mapping>
        <filter-name>CharacterEncodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```

GET 请求中文参数出现乱码解决方法有两个。

- 修改 Tomcat 配置文件添加编码与工程编码一致，如下：

```
<ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
```

- 另外一种方法对参数进行重新编码：
    
```
String userName = new String(request.getParamter("userName").getBytes("ISO8859-1"),"utf-8");
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 如果在拦截请求中，我想拦截 GET 方式提交的方法，怎么配置？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：可以在 @requestMapping 注解里面加上 `method=requestMethod.GET`。</p>
    

    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) @requestBody 注解的作用？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：读取 HTTP 请求参数，通过 Spring MVC 提供的 HttpMessageConverter 接口将读取的参数转为 JSON、XML 格式的数据，绑定到业务方法的形参。 </p>
    
   
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 如何在方法里面得到 request 对象？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：直接在方法的形参中声明 request，Spring MVC 就自动把 request 对象传入。</p>
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


### 第09课：Spring MVC 模型数据解析

**(1) 下列哪个选项不属于JSP作用域？（）**

A. pageScope  
B. requestScope  
C. sessionScope  
D. responseScope  

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：D</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) Sping MVC 中的控制器的注解一般用什么，有没有别的注解可以替代？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：一般用 @Conntroller 注解，可以用 @Service、@Repository、@Component 替代。</p>
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 说说 ModelAndView 的作用。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：ModelAndView 包含模型数据和视图信息，业务方法将 ModelAndView 返回给 DispatcherServlet，然后由 DispatcherServlet 交给 ViewResolver 来解析。</p>
    

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) @ModelAttribute如何使用？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- 定义一个方法，该方法用来返回要填充到模型数据中的对象。
- 给该方法添加 @ModelAttribute 注解。
- 添加 @ModelAttribute 注解的方法，会在 Spring MVC 在调用任何一个业务方法之前被自动调用。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 使用 @ModelAttribute 将模型数据保存到域对象中，此时的 key 值是什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：默认取模型数据对应类的类名首字母小写，即 User 类首字母小写 "user"。</p>

    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


### 第10课：Spring MVC 自定义数据转换器

**(1) 说说你对自定义数据类型转换器的理解。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：通过自定义数据类型转换器可以根据需求对 HTTP 请求中的参数进行解析，转换成需要的数据类型。具体操作是创建一个 Java 类，实现 org.springframework.core.convert.converter.Converter 接口，这样自定义的 Java 类就具备了转换数据的功能，然后在 convert 方法中完成转换的具体业务流程。</p>
    
当服务器接收到一个请求之后，Spring MVC 首先将请求分发到数据类型转换器进行格式转换，然后再进入相应的业务方法。
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 自定义转换器在实现 Converter 接口时，是否必须指定泛型呢？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：不是必须的，指定泛型之后，数据安全性更高且不需要手动进行强制类型转换；不指定泛型也可以完成转换，但需要手动进行强制类型转换。</p>
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 日期类型数据转换在 springmvc.xml 中如何配置？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```xml
    <bean id="conversionService" class="org.springframework.context.support.ConversionServiceFactoryBean">
            <property name="converters">
                <bean class="com.southwind.utils.DateConverter">
                    <!-- 调用有参构造函数创建 bean -->
                    <constructor-arg type="java.lang.String" value="yyyy-MM-dd"/>
                </bean>
            </property>
    </bean>
    <mvc:annotation-driven conversion-service="conversionService"/>
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 上题中的 `<constructor-arg type="java.lang.String" value="yyyy-MM-dd"/>` 是否为必须要设置的？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：是必须要设置的，用来限制 HTTP 请求中的参数格式。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 如何在 springmvc.xml 中配置多个转换器？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

```xml
<bean id="conversionService" class="org.springframework.context.support.ConversionServiceFactoryBean">
      <property name="converters">
          <list>
              <!-- 日期转换器 -->
              <bean class="com.southwind.utils.DateConverter">
                  <constructor-arg type="java.lang.String" value="yyyy-MM-dd"/>
              </bean>
              <!-- Student 转换器 -->
              <bean class="com.southwind.utils.StudentConverter"></bean>
          </list>
      </property>
</bean>
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>

### 第11课：Spring MVC RESTful 架构

**(1) REST 代表什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：REST 代表 REpresentational State Transfer，它使用 HTTP 协议将数据从客户端发送到服务器。但是，如果你不熟悉 REST，我建议你首先查看 REST API 设计和开发，以便更好地理解它。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 什么是资源？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：网络上的一个实体，或者说是网络上的一个具体信息。它可以是一段文本、一张图片、一首歌曲、一种服务，总之就是一个具体的存在。可以用一个 URI（统一资源定位符）指向它，每种资源对应一个特定的 URI。要获取这个资源，访问它的 URI 就可以，因此 URI 即为每一个资源的独一无二的识别符。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) REST 使用哪些 HTTP 方法？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：REST 可以使用任何 HTTP 方法，但最常用的方法是 GET 用于检索资源，POST 用于创建资源，PUT 用于更新资源，DELETE 用于从服务器中删除资源。
</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>

**(4) 什么是 Spring REST 中的 HttpMessageConverter？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：HttpMessageConverter 是一个策略接口，它指定可以从 HTTP 请求和响应转换的转换器。Spring REST 使用此接口将 HTTP 响应转换为各种格式，例如 JSON 或 XML。</p>
    
每个 HttpMessageConverter 实现都有一个或多个与之关联的 MIME 类型。Spring 使用 “Accept” 标头来确定客户端期望的内容类型。

然后，它将尝试查找已注册的 HTTPMessageConverter，该 HTTPMessageConverter 能够处理该特定内容类型，并在将响应发送到客户端之前将其用于将响应转换为该格式。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) Spring MVC 业务方法中如何绑定 RESTful 参数？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：`@GetMapping(value = "/getById/{id}")`，{} 中的值为参数名称，再结合 `@PathVariable(value = "id")` 注解，将参数与业务方法的形参进行绑定。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


### 第12课：Spring MVC 文件上传下载

**(1) 文件上传时 form 表单的 method 可以设置为 GET，这句话是否正确？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：错误。</p>
    <dl>
        <dt>解析：form 表单的 method 必须是 POST，如果设置为 GET，传给服务的参数只是文件名，而非文件本身。</dt>
        <dd></dd>
    </dl>
</details>


**(2) Spring MVC 业务方法中如何绑定 HTTP 请求中的二进制文件数据？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：通过 @requestParam() 注解，将 HTTP 请求中的二进制文件数据与 MultipartFile 对象进行映射，从而在业务方法中可以通过操作 MultipartFile 对象来完成文件上传。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 如何限制上传文件的大小？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```xml
<bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
      <!-- 设置每个上传文件的大小上限 -->
      <property name="maxUploadSizePerFile" value="1048576"/>
</bean>
```
同时需要注意，value 属性的值以 byte 为单位，所以设置上限为 1MB，value 的值应该为 1024*1024=1048576。
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


  

**(4) 文件下载时如何设置下载之后的文件名？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
```
response.setHeader("Content-Disposition", "attachment;filename="+fileName);
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 文件下载时出现文件名中文乱码应该如何解决？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：通过 URLEncoder.encode 来解决，`name = URLEncoder.encode(name,"UTF-8");`。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第13课：Spring MVC 数据校验

**(1) 谈谈你对数据校验的理解。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：用来验证客户输入的数据是否合法，比如客户登录时，用户名不能为空，或者不能超出指定长度等要求，这就叫做数据校验。</p>
    
数据校验分为客户端校验和服务端校验：

- 客户端校验：JS 校验。
- 服务端校验：Spring MVC 使用 validation 校验，Struts 2 使用 validation 校验。都有自己的一套校验规则。
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) Spring MVC 提供了哪些数据校验的方式？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- 基于 Validator 接口。
- 使用 Annotaion JSR-303 标准进行校验。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 使用 Hibernate Validator 注解方式，以下哪个选项表示校验数据不能为空？（）**

A. @Null  
B. @NotNull  
C. @Past  
D. @Pattern  

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：B</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 使用 Hibernate Validator 注解方式校验 Email 数据格式应该怎么写？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```java
  @Email(regexp = "^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\\.[a-zA-Z0-9-]+)*\\.[a-zA-Z0-9]{2,6}$", message = "请输入正确的邮箱格式")
      private String email;
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 数据校验的错误信息保存在哪里？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：保存在 BindingResult 对象中，在业务方法的形参列表中添加 BindingResult 对象即可。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>



### 第14课：Spring MVC 表单标签库

**(1) 如何使用 SpringMVC 的标签库？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：JSP 文件的顶部加入以下指令</p>

```jsp
<%@taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
```
通过 form 表单的 modelAttribute 属性值与 key 值的映射，找到加载到域对象中的绑定对象。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) form:input 标签，是通过 name 属性与绑定对象的成员变量进行映射吗？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：错误。是通过 path 属性进行映射的。</p>

```jsp
<form:input path="id"/>
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) form:input 标签是否支持绑定对象的及联操作？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：支持。</p>
如代码：
```jsp
学生住址：<form:input path="address.name" />
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) form:checkboxes 标签中，items 属性和 path 属性分别表示什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- items 表示全部选项集合，不能直接映射到集合名，需要通过 EL 表达式映射到域对象的 key 值。
- path 表示选中的选项集合，直接映射到集合名即可。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) form:options 和 form:option 的区别？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
form:options 可以直接映射到目标集合，如代码：

```jsp
    <form:select path="selectCity">
        <form:options items="${student.citys }"></form:options>
    </form:select>
```

form:option 不能直接映射到集合，需要手动写出每个选项，如代码：

```jsp
    <form:select path="selectCity">
        <form:option value="5">杭州</form:option>
        <form:option value="6">成都</form:option>
        <form:option value="7">南京</form:option>
    </form:select>
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第15课：Spring MVC 国际化

**(1) 什么是国际化？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：所谓国际化就是指 Web 应用在不同的浏览环境中显示不同的语言，如汉语、英语等。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 使用国际化，应该在 springmvc.xml 中进行哪些配置？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```xml
  <!-- 国际化资源文件 -->
  <bean id="messageSource" class="org.springframework.context.support.ReloadableResourceBundleMessageSource">
      <!-- 表示多语言配置文件在根路径下，以 language 开头的文件-->
      <property name="basename" value="classpath:language"/>
      <property name="useCodeAsDefaultMessage" value="true"/>
  </bean>
  
  <!-- 拦截器 -->
  <mvc:interceptors>
      <bean id="localeChangeInterceptor" class="org.springframework.web.servlet.i18n.LocaleChangeInterceptor">
          <property name="paramName" value="lang"/>
      </bean>
  </mvc:interceptors>
  
  <!-- 配置 SessionLocaleResolver，动态的获取 Locale 对象存入Session -->
  <bean id="localeResolver" class="org.springframework.web.servlet.i18n.SessionLocaleResolver"></bean>
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 谈谈你对国际化工作流程的理解。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：请求被服务端接收后首先被拦截器所拦截，取出 HTTP 请求中表示语言的参数，通过此参数找到对应语言的资源文件，再结合 Spring MVC 标签将资源文件中的相关内容传给 JSP，最后展示出结果。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 写出 JSP 页面中通过 Spring MVC 标签展示资源数据的代码。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```jsp
<spring:message code="username"/>
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) HTTP 请求中的参数如何与资源文件进行映射？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- 首先通过配置获取到资源文件的开头：`<property name="basename" value="classpath:language"/>`，此配置表示资源文件以 language 开头。
- 将 HTTP 请求中的参数与 language 进行拼接，并用 `_` 进行连接，如 language\_zh\_CN，这样就找到了资源文件名。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第16课：EL 表达式

**(1) 什么是 EL 表达式，为什么要使用 EL 表达式？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：EL 全名为 Expression Language。EL 表达式一般操作的是作用域（application、session、request、pageContext）中的属性，EL 变量指某一个作用域中的属性。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 下列哪个选项是 EL 表达式的基本语法？（）**

A. `${表达式}`  
B. `#{表达式}`  
C. `$[表达式]`  
D. `#[表达式]`  

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：A</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) JSP 的作用域有哪些？分别对应哪些内置对象？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- page 作用域，对应 pageContext。
- request 作用域，对应 request。
- session 作用域，对应 session。
- application 作用域，对应 application。
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) JSP 作用域的范围从小到大依次是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：page 作用域 < request 作用域 < session 作用域 < application 作用域。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>
  

**(5) request 对象中保存了一个 key 为 "user" 的对象，使用 EL 表达式取出该对象 name 值的代码是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```jsp
${requestScope.user.name}
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第17课：JSTL

**(1) 什么是 JSTL？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：JSP 标准标签库 JSP Standard Tag Library，简称 JSTL，提供了一系列的标签供开发者在 JSP 页面中使用，编写各种动态功能。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 如何在 JSP 页面导入 JSTL？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions" %>
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 以下哪个选项是函数标签库截取字符串的操作？（）**

A. `<fn:split(info,",") />`  
B. `${fn:split(info,",") }`  
C. `${fn:substring(info,2,3) }`  
D. `<fn:substring(info,2,3) />`  

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：C</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 列举几个你常用的 JSTL。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- 核心标签库
- 格式化标签库
- 函数标签库

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 谈谈 EL 表达式和 JSTL 的关系。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：一般在实际开发中 EL 表达式和 JSTL 是结合起来使用的，JSTL 主要负责逻辑处理，如遍历集合；EL 表达式主要负责将域对象中的数据进行展示，二者各司其职，配合完成开发需求。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第18课：MongoDB 安装及使用

**(1) 什么是 MongoDB？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：非关系型数据库（NoSQL），MongoDB 很好地实现了面向对象的思想（OO 思想），在 MongoDB 中每一条记录都是一个 Document 对象。MongoDB 最大的优势在于，所有的数据持久操作都无需开发人员手动编写 SQL 语句，直接调用方法就可以轻松地实现 CRUD 操作。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) MongoDB 的特点是什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：高性能、易部署、易使用、存储数据非常方便。</p>

主要功能特性有： 

  - 面向集合存储，易存储对象类型的数据。 
  - 模式自由。 
  - 支持动态查询。 
  - 支持完全索引，包含内部对象。 
  - 支持查询。 
  - 支持复制和故障恢复。 
  - 使用高效的二进制数据存储，包括大型对象（如视频等）。 
  - 自动处理碎片，以支持云计算层次的扩展性。
  - 支持 Python、PHP、Ruby、Java、C、C#、JavaScript、Perl 及 C++ 语言的驱动程序，社区中也提供了对 Erlang 及 .NET 等平台的驱动程序。 
  - 文件存储格式为 BSON（一种 JSON 的扩展）。 
  - 可通过网络访问。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) MongoDB 的功能有哪些？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
  - 面向集合的存储：适合存储对象及 JSON 形式的数据。 
  - 动态查询：Mongo 支持丰富的查询表达式。查询指令使用 JSON 形式的标记，可轻易查询文档中内嵌的对象及数组。 
  - 完整的索引支持：包括文档内嵌对象及数组。Mongo 的查询优化器会分析查询表达式，并生成一个高效的查询计划。 
  - 查询监视：Mongo 包含一个监视工具用于分析数据库操作的性能。 
  - 复制及自动故障转移：Mongo 数据库支持服务器之间的数据复制，支持主—从模式及服务器之间的相互复制。复制的主要目标是提供冗余及自动故障转移。 
  - 高效的传统存储方式：支持二进制数据及大型对象（如照片或图片） 
  - 自动分片以支持云级别的伸缩性：自动分片功能支持水平的数据库集群，可动态添加额外的机器。
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>

**(4) 说说 MongoDB 的适用场景。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
  - 网站数据：Mongo 非常适合实时的插入、更新与查询，并具备网站实时数据存储所需的复制及高度伸缩性。 
  - 缓存：由于性能很高，Mongo 也适合作为信息基础设施的缓存层。在系统重启之后，由 Mongo 搭建的持久化缓存层可以避免下层的数据源过载。 
  - 大尺寸、低价值的数据：使用传统的关系型数据库存储一些数据时可能会比较昂贵，在此之前，很多时候程序员往往会选择传统的文件进行存储。 
  - 高伸缩性的场景：Mongo 非常适合由数十或数百台服务器组成的数据库。Mongo 的路线图中已经包含对 MapReduce 引擎的内置支持。 
  - 用于对象及 JSON 数据的存储：Mongo 的 BSON 数据格式非常适合文档化格式的存储及查询。
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>

**(5) 关闭 MongoDB 服务的命令是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```
use admin
db.shutdownServer()
```
    
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第19课：MongoDB 常用命令

**(1) 下列哪个选项是 MongoDB 创建数据库的命令？（）**

A. use testdb  
B. create testdb  
C. use database testdb  
D. create database testdb  

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：A</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>

**(2) 删除数据库的命令是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```
  use testdb
  db.dropDatabase()
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 查询全部数据的命令是 `db.my_student.find()` 吗？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：正确。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 条件查询的命令是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```
db.my_student.find({x:1})//查找 x=1 的数据
```

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 将 x=11 的数据 name 修改为 Tom 的命令是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```
db.my_student.update({x:11},{x:11,name:"Tom"})
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第20课：Spring Data 集成 MongoDB：MongoTemplate

**(1) 什么是 Spring Data JPA？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    

  - JPA（Java Persistence API）是 Sun 官方提出的 Java 持久化规范。它为 Java 开发人员提供了一种对象/关联映射工具来管理 Java 应用中的关系数据。它的出现主要是为了简化现有的持久化开发工作和整合 ORM 技术，结束现在 Hibernate、TopLink、JDO 等 ORM 框架各自为营的局面。JPA 是在充分吸收了现有的 Hibernate、TopLink、JDO 等 ORM 框架的基础上发展而来的，具有易于使用、伸缩性强等优点。
  - Spring Data JPA 是 Spring 基于 ORM 框架、JPA 规范的基础上封装的一套 JPA 应用框架，可以让开发者用极简的代码即可实现对数据的访问和操作。它提供了包括增、删、改、查等在内的常用功能，且易于扩展，学习并使用 Spring Data JPA 可以极大提高开发效率。Spring Data JPA 其实就是 Spring 基于 Hibernate 之上构建的 JPA 使用解决方案，方便在 Spring Boot 项目中使用 JPA 技术。
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) 使用 Maven 管理 Spring Data MongoDB 依赖的配置是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```xml
  <dependency>
      <groupId>org.springframework.data</groupId>
      <artifactId>spring-data-mongodb</artifactId>
      <version>2.0.8.RELEASE</version>
  </dependency>
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) spring.xml 中如何配置 MongoTemplate 的相关配置？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```xml
  <!-- Spring连接MongoDB客户端配置 -->
  <mongo:mongo-client host="127.0.0.1" port="12345" id="mongo"/>
  
  <!-- 配置MongoDB目标数据库 -->
  <mongo:db-factory dbname="testdb" mongo-ref="mongo" />
  
  <!-- 配置MongoTemplate -->
  <bean id="mongoTemplate" class="org.springframework.data.mongodb.core.MongoTemplate">
    <constructor-arg name="mongoDbFactory" ref="mongoDbFactory"/>
  </bean>
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>

**(4) @Document 注解的作用是什么？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：实体类与集合的映射，value 可以指定集合名，若省略，默认取首字母小写之后的类名作为集合名。</p>
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 删除多条记录并返回的代码是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
```java
  List<Student> students =  mongoTemplate.findAllAndRemove(
              Query.query(new Criteria("age").is(19)), 
              Student.class);
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


### 第21课：Spring Data 集成 MongoDB：Reposity

**(1) spring.xml 中如何配置 Reposity？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```xml
<!-- 扫描 Reposity 接口 -->
<mongo:repositories base-package="com.southwind.repository"></mongo:repositories>
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) `boolean flag = studentReposity.existsById("5b62c6f55a41f60d93ffe6c2");` 执行什么操作？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：根据 id="5b62c6f55a41f60d93ffe6c2" 查询数据是否存在。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 删除一组数据的代码是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```java
  Student Student = studentReposity.findById("5b62c6f55a41f60d93ffe6c1").get();
  Student Student2 = studentReposity.findById("5b62c6f55a41f60d93ffe6c3").get();
  Student Student3 = studentReposity.findById("5b62c6f55a41f60d93ffe6c4").get();
  List<Student> list = new ArrayList<Student>();
  list.add(Student);
  list.add(Student2);
  list.add(Student3);
  studentReposity.deleteAll(list);
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 写出一个自定义方法。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```java
  @Repository
  public interface StudentReposity extends CrudRepository<Student, String>{
      public List<Student> findAll(Sort sort);
  }
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 以下哪个选项是查询总记录数？（）**

A. long count = studentReposity.getCount();  
B. long count = studentReposity.count();  
C. long count = studentReposity.size();  
D. long count = studentReposity.length;  

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：B</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>




### 第22课：Nginx 搭建 Tomcat 集群

**(1) 列举几个 Nginx 常用命令。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

  - 启动 Nginx：./sbin/nginx
  - 停止 Nginx：./sbin/nginx -s stop 或 ./sbin/nginx -s quit
  - 重载配置：./sbin/nginx -s reload（平滑重启）或 service nginx reload 
  - 重载指定配置文件：./sbin/nginx -c /usr/local/nginx/conf/nginx.conf
  - 查看 Nginx 版本：./sbin/nginx -v
  - 检查配置文件是否正确：./sbin/nginx -t
  - 显示帮助信息：./sbin/nginx -h

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) Nginx 是如何实现高并发的？**
<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

  - 一个主进程，多个工作进程，每个工作进程可以处理多个请求
    每进来一个 request，会有一个 worker 进程去处理。但不是全程的处理，处理到可能发生阻塞的地方，比如向上游（后端）服务器转发 request，并等待请求返回。那么，这个处理的 worker 继续处理其他请求，而一旦上游服务器返回了，就会触发这个事件，worker 才会来接手，这个 request 才会接着往下走。
  - 由于 Web Server 的工作性质决定了每个 request 的大部份生命都是在网络传输中，实际上花费在 Server 机器上的时间片不多。这是几个进程就解决高并发的秘密所在。即 @skoo 所说的 Web Server 刚好属于网络 IO 密集型应用，不算是计算密集型。
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 说说 Nginx 和 Apache 的区别。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

- 轻量级，同样是 Web 服务，比 Apache 占用更少的内存及资源；
- 抗并发，Nginx 处理请求是异步非阻塞的，而 Apache 则是阻塞型的，在高并发下 Nginx 能保持低资源低消耗高性能；
- 高度模块化的设计，编写模块相对简单；
- 最核心的区别在于 Apache 是同步多进程模型，一个连接对应一个进程，Nginx 是异步的，多个连接（万级别）可以对应一个进程。
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) Nginx 搭建 Tomcat 集群的配置是？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```
  #tomcat 集群
  upstream  myapp {   #tomcat 集群名称 
      server    localhost:8080;   #tomcat1 配置
      server    localhost:8181;   #tomcat2 配置
  }
  
  server {
      listen       9090;
      server_name  localhost;
  
      #charset koi8-r;
  
      #access_log  logs/host.access.log  main;
  
      location / {
          #root   html;
          #index  index.html index.htm;
          proxy_pass http://myapp;
          proxy_redirect default;
      }
   }
```
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) Nginx 负载均衡策略有哪些？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
  - 轮询（默认）：每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器 down 掉，能自动剔除。 
  - 指定权重：指定轮询几率、weight 和访问比率成正比，用于后端服务器性能不均的情况。 
  - IP 绑定 ip_hash：每个请求按访问 IP 的 Hash 结果分配，这样每个访客固定访问一个后端服务器，可以解决 session 的问题。 
  - fair（第三方）：按后端服务器的响应时间来分配请求，响应时间短的优先分配。 
  - url_hash（第三方）：按访问 URL 的 hash 结果来分配请求，使每个 URL 定向到同一个后端服务器，后端服务器为缓存时比较有效。
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>
 

### 第23课：Spring MVC + layui + Spring Data + MongoDB 项目实战

**(1) 使用 layui，后台实体类应该如何定义？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```java
  public class AuthorityVO {
      private int code;
      private String mess;
      private long count;
      private List<Authority> data;
  }
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(2) Spring MVC 中 JSON 格式转换器如何配置？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>
    
```
  <mvc:annotation-driven >
      <!-- 消息转换器 -->
      <mvc:message-converters register-defaults="true">
         <!-- fastjson -->
         <bean class="com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter4"/>
      </mvc:message-converters>
  </mvc:annotation-driven>
```
<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(3) 权限管理系统一般有哪些需求？**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：</p>

  - 权限管理：查询、创建、修改、删除。
  - 角色管理：查询、创建、修改、删除、添加权限。
  - 用户管理：查询、创建、修改、删除、添加角色。
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(4) 谈谈 Spring Data JPA 的底层实现。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：Spring Data JPA 底层默认实现是使用 Hibernate，Spring Data JPA 的首个接口就是 Repository，它是一个标记接口。只要我们的接口实现这个接口，那么我们就相当于在使用 Spring Data JPA 了，就可以使用“按照方法命名规则”来进行查询。</p>
    <dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>


**(5) 谈谈 Spring 中 AOP 的应用场景、原理及优点。**

<details stylecolor=red>
    <summary><b><font color=207f06>点击查看答案</font></b></summary>
    <p>答案：Aspect Oriented Programming 面向切面编程，用来封装横切关注点，具体可以在下面的场景中使用。</p>
    
- Authentication 权限
- Caching 缓存
- Context passing 内容传递
- Error handling 错误处理
- Lazy loading 懒加载
- Debugging 调试
- logging, tracing, profiling and monitoring 记录跟踪优化校准
- Performance optimization 性能优化
- Persistence 持久化
- Resource pooling 资源池
- Synchronization 同步
- Transactions 事务

原理：AOP 是面向切面编程，是通过动态代理的方式为程序添加统一功能，集中解决一些公共问题。

优点：

1. 各个步骤之间的良好隔离性耦合性大大降低。
2. 源代码无关性，在扩展功能的同时不对源码进行修改操作。

<dl>
        <dt></dt>
        <dd></dd>
    </dl>
</details>
