## Spring Boot 学习大纲

### 阶段性学习总结

### 一 、 Spring-Boot是什么东西？

1. Spring Boot是一个集成Spring MVC的框架结构，基本上帮你配置好了所有的基本配置信息，可以让程序员更关注于业务逻辑代码。
2. 使用该框架可以轻松创建可以独立运行的，基于生产级别的Spring程序。方便程序员可以更少的开始，大多数Spring-Boot都只需要非常少的Spring配置。

### 二 、自己的一些想法

1. 主启动类。
   
1. 这是Spring-Boot程序的入口，使用@SpringApplication注解标注，表明程序的入口，调用SpringApplication的run方法，将主程序类传进去，即代表程序的程序开始了。
   
2.  Controller
   
1.  这个就相当于API，使用@RestController注解，表明这个是处理页面处理的请求@RequestMapping("/subtasks")注解表示处理界面的后面的链接请求。还有@GetMapping和@PostMapping、@PutMapping注解，同理，只是有细微的差别。
   
3. Service
   
1. 这一部分处理一些公共的请求，比如说数据库的调用以及结果的返回，将不同API公共的操作方法抽调出来，使用@service注解，将相应的类添加到Spring-Boot容器中。
   
4.  Entity

   1. 实体类，这个一般是定义项目中的实体对象，比如说是人，任务列表等。在项目中都可以使用。使用@Entity注解标注，同时使用@Data注解标注，可以不用写set和get方法。使用@Builder注解标注，可以使用相应的Builder方法来构造对象

      ```java
      //若使用@Builder（toBuilder=true）则可以使用toBuilder方式修改对象
      Student student = Student.builder().schoolName("清华附小").grade("二年级").build();
      userInfo = userInfo.toBuilder().name("OK").email("zgood@sina.com").build();
      ```

      

5.  Config

   1. 这个是配置类，用于读取配置文件中的一些配置内容，使用@Configuration注解标注，使用@Value或者@CongratulationPropertites注解标注，用于获取配置文件中的内容。

### 三、使用Service

1. 在Controller中使用Service中的服务，调用如下的代码

   ```java
   private final LabelSubtaskService labelSubtaskService;
   @Autowired
   public LabelSubtaskController(LabelSubtaskService labelSubtaskService) {
       this.labelSubtaskService = labelSubtaskService;
    }
   ```

   在Controller中首先定义一个类变量，其次使用类似构造方法的方法，初始化对象，然后就可以调用到Service中的内容，同时，要使用@Autowired注解标注，将其中的内容引入进来。

### 四 、使用@Transactional注解

1. 用该注解来完成对事务的操作管理。使用时只需要再pom文件中引入相应的包，然后添加到相应的方法中即可。另外事务的属性信息如下所示：

   | 属性名           | 说明                                                         |
   | :--------------- | :----------------------------------------------------------- |
   | name             | 当在配置文件中有多个 TransactionManager , 可以用该属性指定选择哪个事务管理器。 |
   | propagation      | 事务的传播行为，默认值为 REQUIRED。                          |
   | isolation        | 事务的隔离度，默认值采用 DEFAULT。                           |
   | timeout          | 事务的超时时间，默认值为-1。如果超过该时间限制但事务还没有完成，则自动回滚事务。 |
   | read-only        | 指定事务是否为只读事务，默认值为 false；为了忽略那些不需要事务的方法，比如读取数据，可以设置 read-only 为 true。 |
   | rollback-for     | 用于指定能够触发事务回滚的异常类型，如果有多个异常类型需要指定，各类型之间可以通过逗号分隔。 |
   | no-rollback- for | 抛出 no-rollback-for 指定的异常类型，不回滚事务。            |

2. 使用该注解只能添加到public的方法上，如果添加在类上面，则表示该类的所有public方法都是配置了同样的事务属性信息。
3. ***数据库中的事务***
   1. 原子性：对于其数据修改，要么是全部执行，要么全部不执行
   2. 一致性：事务在完成时，必须使所有的数据都保持一直状态，在相关数据库中，所有的规则都必须应用与事务的修改，以保持所有数据的完整性。事务结束时，所有的内部数据结构都必须是正确的。
   3. 隔离性：由于并发事务所做的修改必须与任何其他并发事务所做的修改隔离，事务查看数据时数据所处的状态，要么是另一个并发事务修改它之前的状态，要么是另一个事务修改它之后的状态，事务不会查看中间状态的数据。这称为可串行性，因为它能够重新装载起始数据，并且重播一系列事务，以使数据结束时的状态与原始事务执行的状态相同。
   4. 持久性：事务完成之后，他对于系统的影响是永久性的，该修改及时出现系统故障也将一直保持。

### 五、一些基本的注解

1. @Data
   - 这个是lombok的注解，自动生成Getter、Setter、toString、构造方法等
2. @Entity
   - 这个是表明这是一个实体类
3. @table
   - 注解表相关，如别名等
4. @Id
   - 注解主键，@GeneratedValue表示自动生成
5. @DynamicUpdate
   - @DynamicInsert注解可以自动动态的生成insert、update语句，默认会生成全部的update
6. @Column
   - 标示一些字段特性，字段别名，是否允许为空，是否唯一，是否进行插入和更新。
7. @JsonProperty
   - 定义SpringJSON的别名，@JsonIgnore定义JSON时忽略的字段，@JsonFromat定义JSON时进行格式化操作

