title: Spring-Swagger2
date: 2016/05/31 08:02:30
categories:
 - tryghost

tags:
 - java 



---

基于 Java 注解的 RestFul API文档生成工具，注意这个工具的 Spring3.x 和 Spring4.x的依赖使用方法不一样，一下流程基于 Spring4.x

# 官网
http://swagger.io/

# 依赖
```language-xml
        <!--json-->
        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-core</artifactId>
        </dependency>
        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
        </dependency>
        <dependency>
            <groupId>org.codehaus.jackson</groupId>
            <artifactId>jackson-mapper-asl</artifactId>
            <version>1.9.13</version>
            <scope>runtime</scope>
        </dependency>

            <!--spring-fox-->
            <dependency>
                <groupId>io.springfox</groupId>
                <artifactId>springfox-swagger-ui</artifactId>
                <version>2.2.2</version>
            </dependency>
            <dependency>
                <groupId>io.springfox</groupId>
                <artifactId>springfox-petstore</artifactId>
                <version>2.2.2</version>
            </dependency>
            <dependency>
                <groupId>io.springfox</groupId>
                <artifactId>springfox-swagger2</artifactId>
                <version>2.2.2</version>
            </dependency>
            <dependency>
                <groupId>io.springfox</groupId>
                <artifactId>springfox-staticdocs</artifactId>
                <version>2.2.2</version>
                <scope>test</scope>
            </dependency>
```

# 配置
1.spring-servlet.xml
```language-xml

    <!-- 启用默认配置 -->
    <mvc:annotation-driven>
        <mvc:message-converters register-defaults="true">
            <bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
                <property name="supportedMediaTypes">
                    <list>
                        <value>text/html;charset=UTF-8</value>
                        <value>application/json</value>
                    </list>
                </property>
                <property name="objectMapper" ref="jacksonObjectMapper"/>
            </bean>
        </mvc:message-converters>
    </mvc:annotation-driven>
    <bean id="jacksonObjectMapper" class="com.gxb.config.MyJsonMapper"/>
    <bean id="mySwaggerConfig" class="com.gxb.config.MySwaggerConfig"/>


    <mvc:resources mapping="swagger-ui.html" location="classpath:/META-INF/resources/"/>
    <mvc:resources mapping="/webjars/**" location="classpath:/META-INF/resources/webjars/"/>

```

2.MyJsonMapper.java
```language-java
public class MyJsonMapper extends ObjectMapper {

  public MyJsonMapper() {
    this.configure(SerializationFeature.FAIL_ON_EMPTY_BEANS, false);
  }
}

```
3.MySwaggerConfig.java
```language-java
@Configuration
@EnableWebMvc //NOTE: Only needed in a non-springboot application
@EnableSwagger2 //Enable swagger 2.0 spec
@ComponentScan(basePackages = {
    "com.gxb.controller"
})

public class MySwaggerConfig implements InitializingBean {

  @Bean
  public Docket appApi() {
    return new Docket(DocumentationType.SWAGGER_2)
        .groupName("app")
        .apiInfo(apiInfo())
        .forCodeGeneration(true)
        .select()
        .paths(appPaths())
        .build();
  }

  private Predicate<String> appPaths() {
    return or(
        regex("/.*"));
  }

  private ApiInfo apiInfo() {
    return new ApiInfoBuilder()
        .title("文档显示标题 (REST API)")
        .description("文档显示说明")
        .termsOfServiceUrl("http://www.example.com")
        .contact("admin@example.com")
        .license("Apache License Version 2.0")
        .licenseUrl("https://github.com/springfox/springfox/blob/master/LICENSE")
        .version("版本")
        .build();
  }

  @Bean
  public Docket configSpringfoxDocket_all() {
    return new Docket(DocumentationType.SWAGGER_2)
        .produces(Sets.newHashSet("application/json"))
        .consumes(Sets.newHashSet("application/json"))
        .protocols(Sets.newHashSet("http", "https"))
        .forCodeGeneration(true)
        .apiInfo(apiInfo())
        .select().paths(regex(".*"))
        .build();
  }

  public void afterPropertiesSet() throws Exception {

  }
}

```
# 访问地址
/v2/api-docs

# 常用注解
```language-java
@ApiClass

@ApiError

@ApiErrors

@ApiOperation

@ApiParam

@ApiParamImplicit

@ApiParamsImplicit

@ApiProperty

@ApiResponse

@ApiResponses

@ApiModel

```

# 静态文档生成

```language-java
/**
 * Created by ZuoYun on 5/17/16. Time: 9:03 AM Information:
 */
@WebAppConfiguration
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(value = {"classpath:spring-servlet.xml",
                               "classpath:spring/spring-*.xml"})

public class ApiDocs {

  @Autowired
  private WebApplicationContext context;


  private MockMvc mockMvc;

  @Before
  public void setUp() {
    this.mockMvc = MockMvcBuilders.webAppContextSetup(this.context).build();
  }

//  @Test
//  public void convertSwaggerToAsciiDoc() throws Exception {
//    this.mockMvc.perform(MockMvcRequestBuilders.get("/v2/api-docs")
//                             .accept(MediaType.APPLICATION_JSON))
//        .andDo(Swagger2MarkupResultHandler.outputDirectory("src/docs/asciidoc/generated").build())
//        .andExpect(MockMvcResultMatchers.status().isOk());
//  }

  @Test
  public void convertSwaggerToMarkdown() throws Exception {
    this.mockMvc.perform(MockMvcRequestBuilders.get("/v2/api-docs")
                             .accept(MediaType.APPLICATION_JSON))
        .andDo(Swagger2MarkupResultHandler.outputDirectory("src/docs/markdown/generated")
                   .withMarkupLanguage(MarkupLanguage.MARKDOWN).build())
        .andExpect(MockMvcResultMatchers.status().isOk());
  }


}
```
# 其他
 * spring-restful-doc 项目




