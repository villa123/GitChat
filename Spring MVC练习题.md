####1.Spring IoC 初识

- IoC 属于哪种设计模式？

  A、单例模式

  B、原型模式

  C、工厂模式

  D、适配器模式

  - C

- 谈谈你对 spring IoC 和 DI 的理解，它们有什么区别？

  - IoC Inverse of Control 反转控制的概念，就是将原本在程序中手动创建UserService对象的控制权，交由Spring框架管理，简单说，就是创建UserService对象控制权被反转到了Spring框架。
  - DI：Dependency Injection 依赖注入，在Spring框架负责创建Bean对象时，动态的将依赖对象注入到Bean组件。

- 简单谈谈IoC容器的原理。

  - IoC容器在加载时对xml配置文件进行解析，获取所有的bean配置，结合bean中的信息（实体类，属性），通过反射机制来创建实例化对象并完成成员变量的赋值操作。最后以键值对的形式将创建好的实例化对象存入容器。

- 实例化对象的name值为<张三>，配置文件中property的value属性应该配置为___？

  - <![CDATA[<张三>]]>

- 通过Student的运行时类来获取IoC容器中的对象，配置文件中可以配置两个Student的实例，这句话正确吗？

  - 错误，此方法有一个弊端，当spring.xml中配置两个Student的bean时程序报错，因为此时两个bean都是由Student类生成的，ioC容器无法将两个bean都返回，必须指定一个唯一的bean，否则会抛出异常。

####2.Spring ioC DI+p命名空间

- bean的scope有几种类型？请详细列举。

  - 共有4种。

  - singleton：单例，表示通过Spring容器获取的该对象是唯一的。
  - prototype：原型，表示通过Spring容器获取的对象都是不同的。
  - reqeust：请求，表示在一次http请求内有效。
  - session：会话，表示在一个用户会话内有效。

- BeanFactory 接口和 ApplicationContext 接口有什么区别 ？

  - ApplicationContext 接口继承BeanFactory接口，Spring核心工厂是BeanFactory ,BeanFactory采取延迟加载，第一次getBean时才会初始化Bean, ApplicationContext是会在加载配置文件时初始化Bean
  - ApplicationContext是对BeanFactory扩展，它可以进行国际化处理、事件传递和bean自动装配以及各种不同应用层的Context实现，开发中基本都在使用ApplicationContext, web项目使用WebApplicationContext ，很少用到BeanFactory。

- 说说IoC中的继承和Java继承的区别。

  - IoC中继承是对象层面的，指继承对象可以获取被继承对象的所有成员变量值，并赋给其对应的成员变量。Java中的继承是类层面的，指子类可以获取父类的非私有成员变量和方法，不需要再次定义。

- IoC中对象继承来的属性值不能进行覆盖，这句话正确吗？

  - 错误，可以进行覆盖。

- IoC中car对象的配置如下，现在要添加user对象，并且将car注入到user中，正确的配置是（）

  ```
  <bean id="car" class="com.southwind.entity.Car"></bean>
  ```

  - A、<bean id="user" class="com.southwind.entity.User">

    ​	<property name="car" value="car"></property>

    </bean>

  - B、<bean id="user" class="com.southwind.entity.User">

    ​	<property name="car" ref="car"></property>

    </bean>

  - C、<bean id="user" class="com.southwind.entity.User" p:car-ref="car"></bean>

  - D、<bean id="user" class="com.southwind.entity.User" p:car="car"></bean>

  - BC



#### 3.Spring ioC 工厂方法+自动装载

- IoC静态工厂方法至少需要配置一个bean，实例工厂方法至少需要配置两个bean，这句话对吗？

  - 正确。

- 请写出静态工厂方法的配置。

  - <!-- 配置静态工厂创建car对象 -->

    <bean id="car1" class="com.southwind.entity.StaticCarFactory" factory-method="getCar">
    <constructor-arg value="1"></constructor-arg>
    </bean>

- 请写出实例工厂的配置。

  - <!-- 配置实例工厂对象 -->

    <bean id="carFactory" class="com.southwind.entity.InstanceCarFactory"></bean>
    <!-- 通过实例工厂对象创建car对象 -->
    <bean id="car2" factory-bean="carFactory" factory-method="getCar">
    <constructor-arg value="2"></constructor-arg>
    </bean> 

- IoC自动装载有几种方式？

  - 两种：

  - byName：通过属性名自动装载。
  - byType：通过属性对应的数据类型自动装载。

- 如果通过byType进行自动装载，IoC容器中只能有一个实例化对象，这句话对吗？

  - 正确，如果配置了两个实例化对象，IoC容器不知道应该选择哪一个，所以会抛出异常。



#### 4.Spring ioC 基于注解的开发

- bean注入属性有哪几种方式？

  - spring支持构造器注入和setter方法注入。
  - 构造器注入，通过 <constructor-arg> 元素完成注入。
  - setter方法注入， 通过<property> 元素完成注入。

- 介绍一下Spring框架中Bean的生命周期。

  - bean定义

    在配置文件里面用<bean></bean>来进行定义。

  - bean初始化，有两种方式初始化:

    A.在配置文件中通过指定init-method属性来完成。

    B.实现org.springframwork.beans.factory.InitializingBean接口。

  - bean调用。

  - bean销毁，销毁有两种方式：

    A.使用配置文件指定的destroy-method属性。

    B.实现org.springframwork.bean.factory.DisposeableBean接口。

- 基于注解的具体步骤是什么？

  - 第一步：将目标类自动扫描到IoC容器中。
  - 第二步：在类中设置注解完成依赖注入。

- 自动扫描的代码是什么？

  - 

  ```
  <!-- 将类扫描到IoC容器中 -->
  <context:component-scan base-package="com.southwind"></context:component-scan>
  ```

- IoC容器自动完成装载，默认是 ___的方式

  - byType



#### 5.Spring MVC 快速入门

- 简单谈谈你对MVC的理解。

  - MVC设计模式是一种常用的软件架构方式：以Controller（控制层），Model（模型层），View（视图层）三个模块分离的形式来组织代码。

    MVC工作流程：控制层接受到客户端请求，调用模型层生成业务数据，传递给视图层，将最终的业务数据和视图响应给客户端做展示。

- 什么是Spring MVC ？简单介绍下你对springMVC的理解?

  - Spring MVC是一个基于MVC架构的用来简化web应用程序开发的应用开发框架，它是Spring的一个模块,无需中间整合层来整合 ，它和Struts2一样都属于表现层的框架。在web模型中，MVC是一种很流行的框架，通过把Model，View，Controller分离，把较为复杂的web应用分成逻辑清晰的几部分，简化开发，减少出错，方便组内开发人员之间的配合。

- Springmvc的优点有哪些？

  - 它是基于组件技术的。全部的应用对象,无论控制器和视图,还是业务对象之类的都是 java组件.并且和Spring提供的其他基础结构紧密集成。
  - 不依赖于Servlet API(目标虽是如此,但是在实现的时候确实是依赖于Servlet的)。
  - 可以任意使用各种视图技术,而不仅仅局限于JSP。
  -  支持各种请求资源的映射策略。
  - 它是易于扩展的。

- springMVC和struts2的区别有哪些?

  - springmvc的入口是一个servlet即前端控制器（DispatchServlet），而struts2入口是一个filter过虑器（StrutsPrepareAndExecuteFilter）。
  - springmvc是基于方法开发(一个url对应一个方法)，请求参数传递到方法的形参，可以设计为单例或多例(建议单例)，struts2是基于类开发，传递参数是通过类的属性，只能设计为多例。
  - struts2采用值栈存储请求和响应的数据，通过OGNL存取数据，springmvc通过参数解析器是将request请求内容解析，并给方法形参赋值，将数据和视图封装成ModelAndView对象，最后又将ModelAndView中的模型数据通过reques域传输到页面。Jsp视图解析器默认使用jstl。

- Spring MVC的核心入口类是___。

  - DispatchServlet

#### 6.Spring MVC 底层实现

- Spring MVC的核心组件有哪些？
  - DispatcherServlet：前端控制器，是整个流程控制的核心，控制其他组件的执行，统一调度，降低组件之间的耦合性，相当于总指挥。
  - 2.Handler：处理器，完成具体业务逻辑，相当于Servlet或Action。
  - 3.HandlerMapping： DispatcherServlet接收到请求之后，通过HandlerMapping将不同的请求分发到不同的Handler。
  - 4.HandlerInterceptor：处理器拦截器，是一个接口，如果我们需要做一些拦截处理，可以来实现这个接口。
  - 5.HandlerExecutionChain：处理器执行链，包括两部分内容：Handler和HandlerInterceptor（系统会有一个默认的HandlerInterceptor，如果需要额外拦截处理，可以添加拦截器设置）。
  - 6.HandlerAdapter：处理器适配器，Handler执行业务方法之前，需要进行一系列的操作包括表单数据的验证，数据类型的转换，将表单数据封装到JavaBean等等，这一系列的操作，都是由HandlerAdapter来完成，DispatcherServlet通过HandlerAdapter执行不同的Handler。
  - 7.ModelAndView：装载了模型数据和视图信息，作为Handler的处理结果，返回给DispatcherServlet。
  - 8.ViewResolver：视图解析器，DispatcherServlet通过它将逻辑视图解析成物理视图，最终将渲染结果响应给客户端。

- SpringMVC的实现流程是什么？
  - 1.客户端请求被DispatcherServlet（前端控制器）接收。
  - 2.根据HandlerMapping映射到Handler。
  - 3.生成Handler和HandlerInterceptor（如果有则生成）。
  - 4.Handler和HandlerInterceptor以HandlerExecutionChain的形式一并返回给DispatcherServlet。
  - 5.DispatcherServlet通过HandlerAdapter调用Handler的方法做业务逻辑处理。
  - 6.返回一个ModelAndView对象给DispatcherServlet。
  - 7.DispatcherServlet将获取的ModelAndView对象传给ViewResolver视图解析器，将逻辑视图解析成物理视图View。
  - 8.ViewResolver返回一个View给DispatcherServlet。
  - 9.DispatcherServlet根据View进行视图渲染（将模型数据填充到视图中）。
  - 10.DispatcherServlet将渲染后的视图响应给客户端。
- XML是什么？
  - XML即可扩展标记语言（Extensible Markup language），你可以根据自己的需要扩展XML。XML中可以轻松定义`<books>, <orders>`等自定义标签，而在HTML等其他标记语言中必须使用预定义的标签，比如`<p>`，而不能使用用户定义的标签。使用DTD和XML Schema标准化XML结构。XML主要用于从一个系统到另一系统的数据传输，比如企业级应用的客户端与服务端。
- 分别说说反射的优缺点。
  - 优点：反射提高了程序的灵活性和扩展性，在底层框架中使用较多，业务层开发尽量少用。
  - 缺点：性能不高，反射是一种解释操作，用于属性和方法接入时要远慢于直接代码。
- 反射机制的作用。
  - 在运行时判断任意一个对象所属的类。
  - 在运行时构造任意一个类的对象。
  - 在运行时判断任意一个类所具有的成员变量和方法。
  - 在运行时调用任意一个对象的方法。



#### 7.Spring MVC 注解

- @RequestMapping只能修饰方法，不能修饰类，这句话是否正确？
  - 错误，@RequestMapping既可以修饰方法，也可以修饰类。
- @RequestMapping的默认属性是___。
  - value
- @RequestMapping(value="paramsTest",params={"name","id=10"})此注解表示什么意思？
  - 表示要调用paramsTest方法，HTTP请求中必须包含name和id两个参数，并且id参数的值必须是10，name参数的值没有要求。
- Spring MVC的参数绑定是由___来完成的。
  - HandlerAdapter
- SpringMVC怎么样设定重定向和转发的？
  - 在返回值前面加"forward:"就可以让结果转发,譬如"forward:user.do?name=zhangsan"。
  - 在返回值前面加"redirect:"就可以让返回值重定向,譬如"redirect:index.jsp"。

#### 8.Spring MVC 数据绑定

- @ResponseBody注解的作用？

  - @ResponseBody注解直接返回字符串到前端，不需要返回jsp页面。

- 如何解决POST请求中文乱码问题，GET的又如何处理呢？

  - 解决post请求乱码问题：

    在web.xml中加入：

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

  - get请求中文参数出现乱码解决方法有两个：

    - 修改tomcat配置文件添加编码与工程编码一致，如下：

      ```
      <ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
      ```


    - 另外一种方法对参数进行重新编码：
    
      ```
      String userName = new String(request.getParamter("userName").getBytes("ISO8859-1"),"utf-8");
      ```

- 如果在拦截请求中,我想拦截get方式提交的方法,怎么配置？
  - 可以在@RequestMapping注解里面加上method=RequestMethod.GET。
- @RequestBody注解的作用？
  - 读取http请求参数，通过SpringMVC提供的HttpMessageConverter接口将读取的参数转为json，xml格式的数据，绑定到业务方法的形参。
- 如何在方法里面得到request对象？
  - 直接在方法的形参中声明request，Spring MVC就自动把request对象传入。

#### 9.Spring MVC 模型数据解析

- 下列哪个选项不属于JSP作用域？（）

  A、pageScope

  B、requestScope

  C、sessionScope

  D、responseScope

  - D

- Sping MVC中的控制器的注解一般用那个,有没有别的注解可以替代？

  - 一般用@Conntroller注解，可以用@Service，@Repository，@Component替代。

- 说说ModelAndView的作用。

  - ModelAndView包含模型数据和视图信息，业务方法将ModelAndView返回给DispatcherServlet，然后由DispatcherServlet交给ViewResolver来解析。

- @ModelAttribute如何使用？

  - 定义一个方法，该方法用来返回要填充到模型数据中的对象。
  - 给该方法添加@ModelAttribute注解。
  - 添加@ModelAttribute注解的方法，会在SpringMVC在调用任何一个业务方法之前被自动调用。

- 使用@ModelAttribute将模型数据保存到域对象中，此时的key值是什么？

  - 默认取模型数据对应类的类名首字母小写，即User类首字母小写"user"。

#### 10.Spring MVC 自定义数据转换器

- 说说你对自定义数据类型转换器的理解。

  - 通过自定义数据类型转换器可以根据需求对HTTP请求中的参数进行解析，转换成需要的数据类型。具体操作是创建一个Java类，实现org.springframework.core.convert.converter.Converter接口，这样自定义的Java类就具备了转换数据的功能，然后在convert方法中完成转换的具体业务流程。

    当服务器接收到一个请求之后，Spring MVC首先将请求分发到数据类型转换器进行格式转换，然后再进入相应的业务方法。

- 自定义转换器在实现Converter接口时，是否必须指定泛型呢？

  - 不是必须的，指定泛型之后，数据安全性更高且不需要手动进行强制类型转换；不指定泛型也可以完成转换，但需要手动进行强制类型转换。

- 日期类型数据转换在springmvc.xml中如何配置？

  - ```xml
    <bean id="conversionService" class="org.springframework.context.support.ConversionServiceFactoryBean">
            <property name="converters">
                <bean class="com.southwind.utils.DateConverter">
                    <!-- 调用有参构造函数创建bean -->
                    <constructor-arg type="java.lang.String" value="yyyy-MM-dd"/>
                </bean>
            </property>
    </bean>
    <mvc:annotation-driven conversion-service="conversionService"/>
    ```

- 上题中的<constructor-arg type="java.lang.String" value="yyyy-MM-dd"/>是否为必须要设置的？

  - 是必须要设置的，用来限制HTTP请求中的参数格式。

- 如何在springmvc.xml中配置多个转换器？

  ```xml
  <bean id="conversionService" class="org.springframework.context.support.ConversionServiceFactoryBean">
      <property name="converters">
          <list>
              <!-- 日期转换器 -->
              <bean class="com.southwind.utils.DateConverter">
                  <constructor-arg type="java.lang.String" value="yyyy-MM-dd"/>
              </bean>
              <!-- Student转换器 -->
              <bean class="com.southwind.utils.StudentConverter"></bean>
          </list>
      </property>
  </bean>
  ```

#### 11.Spring MVC RESTful架构

- REST代表什么？

  - REST代表REpresentational State Transfer，它使用HTTP协议将数据从客户端发送到服务器。但是，如果你不熟悉REST，我建议你首先查看REST API设计和开发，以便更好地理解它。

- 什么是资源？

  - 网络上的一个实体,或者说是网络上的一个具体信息。它可以是一段文本、一张图片、一首歌曲、一种服务,总之就是一个具体的存在。可以用一个URI(统一资源定位符)指向它,每种资源对应一个特定的 URI 。要获取这个资源,访问它的URI就可以,因此 URI 即为每一个资源的独一无二的识别符。

- REST使用哪些HTTP方法？

  - REST可以使用任何HTTP方法，但最常用的方法是GET用于检索资源，POST用于创建资源，PUT用于更新资源，DELETE用于从服务器中删除资源。

- 什么是Spring REST中的HttpMessageConverter？

  - HttpMessageConverter是一个策略接口，它指定可以从HTTP请求和响应转换的转换器。Spring REST使用此接口将HTTP响应转换为各种格式，例如JSON或XML。

    每个HttpMessageConverter实现都有一个或多个与之关联的MIME类型。Spring使用“Accept”标头来确定客户端期望的内容类型。

    然后，它将尝试查找已注册的HTTPMessageConverter，该HTTPMessageConverter能够处理该特定内容类型，并在将响应发送到客户端之前将其用于将响应转换为该格式。

- Spring MVC业务方法中如何绑定RESTful参数？

  - @GetMapping(value = "/getById/{id}")，{}中的值为参数名称，再结合@PathVariable(value = "id")注解，将参数与业务方法的形参进行绑定。

#### 12.Spring MVC 文件上传下载

- 文件上传时form表单的method可以设置为get，这句话是否正确？

  - 错误，form表单的method必须时post，如果设置为get，传给服务的参数只是文件名，而非文件本身。

- Spring MVC业务方法中如何绑定HTTP请求中的二进制文件数据？

  - 通过@RequestParam()注解，将HTTP请求中的二进制文件数据与MultipartFile对象进行映射，从而在业务方法中可以通过操作MultipartFile对象来完成文件上传。

- 如何限制上传文件的大小？

  ```xml
  <bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
      <!-- 设置每个上传文件的大小上限 -->
      <property name="maxUploadSizePerFile" value="1048576"/>
  </bean>
  
  ```

  同时需要注意，value属性的值以byte为单位，所以设置上限为1MB，value的值应该为1024*1024=1048576。

- 文件下载时如何设置下载之后的文件名？

  - response.setHeader("Content-Disposition", "attachment;filename="+fileName);

- 文件下载时出现文件名中文乱码应该如何解决？

  - 通过URLEncoder.encode来解决：name = URLEncoder.encode(name,"UTF-8");



#### 13.Spring MVC 数据校验

- 谈谈你对数据校验的理解。

  - 就是用来验证客户输入的数据是否合法，比如客户登录时，用户名不能为空，或者不能超出指定长度等要求，这就叫做数据校验。

  - 数据校验分为客户端校验和服务端校验

    - 客户端校验：js校验。

    - 服务端校验：springmvc使用validation校验，struts2使用validation校验。都有自己的一套校验规则。

- Spring MVC提供了哪些数据校验的方式？

  - 基于Validator接口。
  - 使用Annotaion JSR-303标准进行校验。

- 使用Hibernate Validator注解方式，以下哪个选项表示校验数据不能为空？（）

  A、@Null

  B、@NotNull

  C、@Past

  D、@Pattern

  - B

- 使用Hibernate Validator注解方式校验email数据格式应该怎么写？

  ```java
  @Email(regexp = "^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\\.[a-zA-Z0-9-]+)*\\.[a-zA-Z0-9]{2,6}$", message = "请输入正确的邮箱格式")
      private String email;
  ```

- 数据校验的错误信息保存在哪里？

  - 保存在BindingResult对象中，在业务方法的形参列表中添加BindingResult对象即可。



#### 14.Spring MVC 表单标签库

- 如何使用SpringMVC的标签库？

  - JSP文件的顶部加入以下指令：

    ```jsp
    <%@taglib prefix="form" uri="http://www.springframework.org/tags/form" %>
    ```

  - 通过form表单的modelAttribute属性值与key值的映射，找到加载到域对象中的绑定对象。

- form:input标签，是通过name属性与绑定对象的成员变量进行映射吗？

  - ```jsp
    <form:input name="id"/>
    ```

  - 错误，是通过path属性进行映射的：

    ```jsp
    <form:input path="id"/>
    ```

- form:input标签是否支持绑定对象的及联操作？

  - 支持，如代码：

    ```jsp
    学生住址：<form:input path="address.name" />
    ```

- form:checkboxes标签中，items属性和path属性分别表示什么？

  - items表示全部选项集合，不能直接映射到集合名，需要通过EL表达式映射到域对象的key值。
  - path表示选中的选项集合，直接映射到集合名即可。

- form:options和form:option的区别？

  - form:options可以直接映射到目标集合，如代码：

    ```jsp
    <form:select path="selectCity">
        <form:options items="${student.citys }"></form:options>
    </form:select>
    ```

  - form:option不能直接映射到集合，需要手动写出每个选项，如代码：

    ```jsp
    <form:select path="selectCity">
        <form:option value="5">杭州</form:option>
        <form:option value="6">成都</form:option>
        <form:option value="7">南京</form:option>
    </form:select>
    ```



#### 15.Spring MVC 国际化

- 什么是国际化？

  - 所谓国际化就是指WEB应用在不同的浏览环境中显示不同的语言，如汉语、英语等。

- 使用国际化，应该在springmvc.xml中进行哪些配置？

  ```xml
  <!-- 国际化资源文件 -->
  <bean id="messageSource" class="org.springframework.context.support.ReloadableResourceBundleMessageSource">
      <!-- 表示多语言配置文件在根路径下，以language开头的文件-->
      <property name="basename" value="classpath:language"/>
      <property name="useCodeAsDefaultMessage" value="true"/>
  </bean>
  
  <!-- 拦截器 -->
  <mvc:interceptors>
      <bean id="localeChangeInterceptor" class="org.springframework.web.servlet.i18n.LocaleChangeInterceptor">
          <property name="paramName" value="lang"/>
      </bean>
  </mvc:interceptors>
  
  <!-- 配置SessionLocaleResolver，动态的获取Locale对象存入Session -->
  <bean id="localeResolver" class="org.springframework.web.servlet.i18n.SessionLocaleResolver"></bean>
  ```

- 谈谈你对国际化工作流程的理解。

  - 请求被服务端接收后首先被拦截器所拦截，取出HTTP请求中表示语言的参数，通过此参数找到对应语言的资源文件，再结合Spring MVC标签将资源文件中的相关内容传给JSP，最后展示出结果。

- 写出JSP页面中通过Spring MVC标签展示资源数据的代码。

  ```jsp
  <spring:message code="username"/>
  ```

- HTTP请求中的参数如何与资源文件进行映射？

  - 首先通过配置获取到资源文件的开头：<property name="basename" value="classpath:language"/>，此配置表示资源文件以language开头。
  - 将HTTP请求中的参数与language进行拼接，并用_进行连接，如language_zh_CN，这样就找到了资源文件名。



#### 16.EL表达式

- 什么是EL表达式，为什么要使用EL表达式？

  - EL 全名为Expression Language。EL表达式一般操作的是作用域(application、session、request、pageContext)中的属性，EL变量指某一个作用域中的属性。

- 下列哪个选项是EL表达式的基本语法？（）

  A、${表达式}

  B、#{表达式}

  C、$[表达式]

  D、#[表达式]

  - A

- JSP的作用域有哪些？分别对应哪些内置对象？

  - page作用域，对应pageContext。
  - request作用域，对应request。
  - session作用域，对应session。
  - application作用域，对应application。

- JSP作用域的范围从小到大依次是？

  page作用域 < request作用域 < session作用域 < application作用域。

- request对象中保存了一个key为"user"的对象，使用EL表达式取出该对象name值的代码是？

  ```jsp
  ${requestScope.user.name}
  ```



#### 17.JSTL

- 什么是JSTL？

  - JSP Standard Tag Library，简称JSTL，JSP标准标签库，提供了一系列的标签供开发者在JSP页面中使用，编写各种动态功能。

- 如何在JSP页面导入JSTL？

  ```jsp
  <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
  <%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
  <%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions" %>
  ```

- 以下哪个选项是函数标签库截取字符串的操作？（）

  A、<fn:split(info,",") />

  B、${fn:split(info,",") }

  C、${fn:substring(info,2,3) }

  D、<fn:substring(info,2,3) />

  - C

- 列举几个你常用的JSTL。

  - 核心标签库。
  - 格式化标签库。
  - 函数标签库。

- 谈谈EL表达式和JSTL的关系。
  - 一般在实际开发中EL表达式和JSTL是结合起来使用的，JSTL主要负责逻辑处理，如遍历集合，EL表达式主要负责将域对象中的数据进行展示，二者各司其职，配合完成开发需求。



#### 18.MongoDB安装及使用

- 什么是MongoDB？
  - 非关系型数据库(NoSql),Mongo DB很好的实现了面向对象的思想(OO思想),在Mongo DB中 每一条记录都是一个Document对象。Mongo DB最大的优势在于所有的数据持久操作都无需开发人员手动编写SQL语句,直接调用方法就可以轻松的实现CRUD操作。

- MongoDB的特点是什么？
  - 高性能、易部署、易使用，存储数据非常方便。主要功能特性有： 
  - 面向集合存储，易存储对象类型的数据。 
  - 模式自由。 
  - 支持动态查询。 
  - 支持完全索引，包含内部对象。 
  - 支持查询。 
  - 支持复制和故障恢复。 
  - 使用高效的二进制数据存储，包括大型对象（如视频等）。 
  - 自动处理碎片，以支持云计算层次的扩展性。
  - 支持Python，PHP，Ruby，Java，C，C#，Javascript，Perl及C++语言的驱动程序，社区中也提供了对Erlang及.NET等平台的驱动程序。 
  - 文件存储格式为BSON（一种JSON的扩展）。 
  - 可通过网络访问。
- MongoDB的功能有哪些？
  - 面向集合的存储：适合存储对象及JSON形式的数据。 
  - 动态查询：Mongo支持丰富的查询表达式。查询指令使用JSON形式的标记，可轻易查询文档中内嵌的对象及数组。 
  - 完整的索引支持：包括文档内嵌对象及数组。Mongo的查询优化器会分析查询表达式，并生成一个高效的查询计划。 
  - 查询监视：Mongo包含一个监视工具用于分析数据库操作的性能。 
  - 复制及自动故障转移：Mongo数据库支持服务器之间的数据复制，支持主-从模式及服务器之间的相互复制。复制的主要目标是提供冗余及自动故障转移。 
  - 高效的传统存储方式：支持二进制数据及大型对象（如照片或图片） 
  - 自动分片以支持云级别的伸缩性：自动分片功能支持水平的数据库集群，可动态添加额外的机器。
- 说说MongoDB的适用场景。
  - 网站数据：Mongo非常适合实时的插入，更新与查询，并具备网站实时数据存储所需的复制及高度伸缩性。 
  - 缓存：由于性能很高，Mongo也适合作为信息基础设施的缓存层。在系统重启之后，由Mongo搭建的持久化缓存层可以避免下层的数据源 过载。 
  - 大尺寸，低价值的数据：使用传统的关系型数据库存储一些数据时可能会比较昂贵，在此之前，很多时候程序员往往会选择传统的文件进行存储。 
  - 高伸缩性的场景：Mongo非常适合由数十或数百台服务器组成的数据库。Mongo的路线图中已经包含对MapReduce引擎的内置支持。 
  - 用于对象及JSON数据的存储：Mongo的BSON数据格式非常适合文档化格式的存储及查询。

- 关闭MongoDB服务的命令是？

  ```
  use admin
  db.shutdownServer()
  ```



#### 19.MongoDB常用命令

- 下列哪个选项是MongoDB创建数据库的命令？（）

  A、use testdb

  B、create testdb

  C、use database testdb

  D、create database testdb

  - A

- 删除数据库的命令是？

  ```
  use testdb
  db.dropDatabase()
  ```

- 查询全部数据的命令是db.my_student.find()吗？

  - 正确。

- 条件查询的命令是？

  ```
  db.my_student.find({x:1})//查找x=1的数据
  ```

- 将x=11的数据name修改为Tom的命令是？

  ```
  db.my_student.update({x:11},{x:11,name:"Tom"})
  ```



#### 20.Spring Data集成MongoDB：MongoTemplate

- 什么是Spring Data JPA？

  - JPA（Java Persistence API）是 Sun 官方提出的 Java 持久化规范。它为 Java 开发人员提供了一种对象 / 关联映射工具来管理 Java 应用中的关系数据。它的出现主要是为了简化现有的持久化开发工作和整合 ORM 技术，结束现在 Hibernate、TopLink、JDO 等 ORM 框架各自为营的局面。JPA 是在充分吸收了现有的 Hibernate、TopLink、JDO 等 ORM 框架的基础上发展而来的，具有易于使用、伸缩性强等优点。
  - Spring Data JPA 是 Spring 基于 ORM 框架、JPA 规范的基础上封装的一套 JPA 应用框架，可以让开发者用极简的代码即可实现对数据的访问和操作。它提供了包括增、删、改、查等在内的常用功能，且易于扩展，学习并使用 Spring Data JPA 可以极大提高开发效率。Spring Data JPA 其实就是 Spring 基于 Hibernate 之上构建的 JPA 使用解决方案，方便在 Spring Boot 项目中使用 JPA 技术。

- 使用Maven管理Spring Data MongoDB依赖的配置是？

  ```xml
  <dependency>
      <groupId>org.springframework.data</groupId>
      <artifactId>spring-data-mongodb</artifactId>
      <version>2.0.8.RELEASE</version>
  </dependency>
  ```

- spring.xml中如何配置MongoTemplate的相关配置？

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

- @Document注解的作用是什么？

  - 实体类与集合的映射，value可以指定集合名，若省略，默认取首字母小写之后的类名作为集合名。

- 删除多条记录并返回的代码是？

  ```java
  List<Student> students =  mongoTemplate.findAllAndRemove(
              Query.query(new Criteria("age").is(19)), 
              Student.class);
  ```



#### 21.Spring Data 集成 MongoDB：Reposity

- spring.xml中如何配置Reposity？

  ```xml
  <!-- 扫描Reposity接口 -->
  <mongo:repositories base-package="com.southwind.repository"></mongo:repositories>
  ```

- boolean flag = studentReposity.existsById("5b62c6f55a41f60d93ffe6c2");执行什么操作？

  - 根据id="5b62c6f55a41f60d93ffe6c2"查询数据是否存在。

- 删除一组数据的代码是？

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

- 写出一个自定义方法。

  ```java
  @Repository
  public interface StudentReposity extends CrudRepository<Student, String>{
      public List<Student> findAll(Sort sort);
  }
  ```

- 以下哪个选项是查询总记录数？（）

  A、long count = studentReposity.getCount();

  B、long count = studentReposity.count();

  C、long count = studentReposity.size();

  D、long count = studentReposity.length;

  - B



#### 22.nginx搭建tomcat集群

- 列举几个nginx常用命令。
  - 启动nginx  ./sbin/nginx
  - 停止nginx ./sbin/nginx -s stop    ./sbin/nginx -s quit
  - 重载配置  ./sbin/nginx -s reload(平滑重启)  service nginx reload 
  - 重载指定配置文件 ./sbin/nginx -c /usr/local/nginx/conf/nginx.conf
  - 查看nginx版本 ./sbin/nginx -v
  - 检查配置文件是否正确 ./sbin/nginx -t
  - 显示帮助信息 ./sbin/nginx -h
- nginx是如何实现高并发的？
  - 一个主进程，多个工作进程，每个工作进程可以处理多个请求
    每进来一个request，会有一个worker进程去处理。但不是全程的处理，处理到可能发生阻塞的地方，比如向上游（后端）服务器转发request，并等待请求返回。那么，这个处理的worker继续处理其他请求，而一旦上游服务器返回了，就会触发这个事件，worker才会来接手，这个request才会接着往下走。
  - 由于web server的工作性质决定了每个request的大部份生命都是在网络传输中，实际上花费在server机器上的时间片不多。这是几个进程就解决高并发的秘密所在。即@skoo所说的webserver刚好属于网络io密集型应用，不算是计算密集型。

- 说说nginx和apache的区别。

  - 轻量级，同样起web 服务，比apache 占用更少的内存及资源；抗并发，nginx 处理请求是异步非阻塞的，而apache 则是阻塞型的，在高并发下nginx 能保持低资源低消耗高性能。高度模块化的设计，编写模块相对简单。最核心的区别在于apache是同步多进程模型，一个连接对应一个进程；nginx是异步的，多个连接（万级别）可以对应一个进程 。

- nginx搭建tomcat集群的配置是？

  ```
  #tomcat集群
  upstream  myapp {   #tomcat集群名称 
      server    localhost:8080;   #tomcat1配置
      server    localhost:8181;   #tomcat2配置
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

- nginx负载均衡策略有哪些？

  - 1、轮询（默认）。每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器down掉，能自动剔除。 
  - 2、指定权重。指定轮询几率，weight和访问比率成正比，用于后端服务器性能不均的情况。 
  - 3、IP绑定 ip_hash。每个请求按访问ip的hash结果分配，这样每个访客固定访问一个后端服务器，可以解决session的问题。 
  - 4、fair（第三方）。按后端服务器的响应时间来分配请求，响应时间短的优先分配。 
  - 5、url_hash（第三方）。按访问url的hash结果来分配请求，使每个url定向到同一个后端服务器，后端服务器为缓存时比较有效。 

#### 23.Spring MVC + layui + Spring Data + MongoDB 项目实战

- 使用layui，后台实体类应该如何定义？

  ```java
  public class AuthorityVO {
      private int code;
      private String mess;
      private long count;
      private List<Authority> data;
  }
  ```

- Spring MVC中json格式转换器如何配置？

  ```
  <mvc:annotation-driven >
      <!-- 消息转换器 -->
      <mvc:message-converters register-defaults="true">
         <!-- fastjson -->
         <bean class="com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter4"/>
      </mvc:message-converters>
  </mvc:annotation-driven>
  ```

- 权限管理系统一般有哪些需求？

  - 权限管理：查询，创建，修改，删除。
  - 角色管理：查询，创建，修改，删除，添加权限。
  - 用户管理：查询，创建，修改，删除，添加角色。

- 谈谈Spring Data JPA的底层实现。

  - SpringData JPA 底层默认实现是使用Hibernate，SpringDataJPA 的首个接口就是Repository，它是一个标记接口。只要我们的接口实现这个接口，那么我们就相当于在使用Spring Data JPA了，就可以使用"按照方法命名规则"来进行查询。

- 谈谈Spring中AOP的应用场景，原理及优点。

  - AOP--Aspect Oriented Programming面向切面编程；用来封装横切关注点，具体可以在下面的场景中使用:

    Authentication 权限、Caching 缓存、Context passing 内容传递、Error handling 错误处理Lazy loading懒加载、Debugging调试、logging, tracing, profiling and monitoring 记录跟踪优化　校准、Performance optimization　性能优化、Persistence 持久化、Resource pooling　资源池、Synchronization　同步、Transactions 事务。

  - 原理：AOP是面向切面编程，是通过动态代理的方式为程序添加统一功能，集中解决一些公共问题。

  - 优点：1.各个步骤之间的良好隔离性耦合性大大降低。
    ​           2.源代码无关性，再扩展功能的同时不对源码进行修改操作。
