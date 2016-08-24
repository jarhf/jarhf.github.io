# ControllerAdvice
```
@ControllerAdvice  
public class ControllerAdviceTest {  
  
    @ModelAttribute  
    public User newUser() {  
        System.out.println("============应用到所有@RequestMapping注解方法，在其执行之前把返回值放入Model");  
        return new User();  
    }  
  
    @InitBinder  
    public void initBinder(WebDataBinder binder) {  
        System.out.println("============应用到所有@RequestMapping注解方法，在其执行之前初始化数据绑定器");  
    }  
  
    @ExceptionHandler(UnauthenticatedException.class)  
    @ResponseStatus(HttpStatus.UNAUTHORIZED)  
    public String processUnauthenticatedException(NativeWebRequest request, UnauthenticatedException e) {  
        System.out.println("===========应用到所有@RequestMapping注解的方法，在其抛出UnauthenticatedException异常时执行");  
        return "viewName"; //返回一个逻辑视图名  
    }  
}  
```
spring-mvc配置文件需要：
```
<context:component-scan base-package="com.sishuok.es" use-default-filters="false">  
       <context:include-filter type="annotation" expression="org.springframework.stereotype.Controller"/>  
       <context:include-filter type="annotation" expression="org.springframework.web.bind.annotation.ControllerAdvice"/>  
   </context:component-scan> 
```

# @ModelAttribute
1. 注解void方法  或 注解有返回值的方法
```
@ModelAttribute  
public void populateModel(@RequestParam String abc, Model model) {  
  model.addAttribute("attributeName", abc);  
}  

@ModelAttribute("attributeName")  
public String addAccount(@RequestParam String abc) {  
  return abc;  
}  
```
2. 注解方法参数
  * （1）从Model中获取
```
public class HelloWorldController {  
  
        @ModelAttribute("user")  
        public User addAccount() {  
           return new User("jz","123");  
        }  
  
        @RequestMapping(value = "/helloWorld")  
        public String helloWorld(@ModelAttribute("user") User user) {  
           user.setUserName("jizhou");  
           return "helloWorld";  
        }  
    }
```
在这个例子里，`@ModelAttribute("user") User user`注释方法参数，参数`user`的值来源于`addAccount()`方法中的model属性。
    此时如果方法体没有标注`@SessionAttributes("user")`，那么`scope`为`request`，如果标注了，那么`scope`为`session`
  * (2)从Form表单或URL参数中获取（实际上，不做此注释也能拿到user对象）
```
public class HelloWorldController {  
  
        @RequestMapping(value = "/helloWorld")  
        public String helloWorld(@ModelAttribute User user) {  
           return "helloWorld";  
        }  
    }  
```

# @Value注解,绑定SpEL表示式.
用于将一个SpEL表达式结果映射到功能处理方法的参数上  
`public String test(@Value("#{systemProperties['java.vm.version']}") String jvmVersion)  `