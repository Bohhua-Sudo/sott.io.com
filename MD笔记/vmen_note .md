#### POM工程
- POM工程是逻辑工程，
- Maven并不会对该类型工程做打包处理，这些工程往往不包含具体的业务，而是用来整合其他工程的。
#### war工程
- JAVA Web工程，在打包时会将项目打成war包。
#### ear工程
- 企业应用工程，在打包时会将项目打成ear包。
#### pom.xml文件
- pom.xml文件是Maven工程的核心配置文件，它包含了工程的基本信息、依赖管理、插件管理等。
- pom.xml文件位于工程根目录下，其内容如下：

#### 1.Linux中设置环境变量
- export PATH= 变更PATH环境变量 /bin:$PATH

#### command
- `mvn clean`	<span style="color:green">_清除编译的class文件，即删除target目录_
- `mvn validate`	<span style="color:green">_验证项目是否正确_
- `mvn compile`	<span style="color:green">_编译maven项目_
- `mvn test`	<span style="color:green">_编译maven项目及运行测试文件_
- `mvn package`	<span style="color:green">_编译maven项目及运行测试文件，并打包_
- `mvn install`	<span style="color:green">_编译maven项目及运行测试文件并打包，并发布到本地仓库_
- `mvn deploy`	<span style="color:green">_部署项目到远程仓库_
- `mvn tomcat7:run`	<span style="color:green">_使用tomcat运行项目_

 #### 2.pom.xml文件配置
- 依赖管理：

<span style="color:purple">阿里云镜像配置</span>
```xml
  <mirror>
      <id>aliyun</id>
      <mirrorOf>central</mirrorOf>
      <name>aliyun maven</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    </mirror>
``` 
<span style="color:purple">本地仓库配置</span>
```xml
 <localRepository>/home/deepin/IdeaProjects/vmen</localRepository>
```
<span style="color:purple">配置JDK版本</span>
```xml
<profile>  
  <id>jdk11</id>  
  <activation>  
    <activeByDefault>true</activeByDefault>  
    <jdk>11</jdk>  
  </activation>  
  <properties>  
    <maven.compiler.source>11</maven.compiler.source>  
    <maven.compiler.target>11</maven.compiler.target>  
    <maven.compiler.compilerVersion>11</maven.compiler.compilerVersion>  
  </properties>  
</profile>
```
#### Pom文件配置
<!-- <scope>范围</scope> -->
- complile：默认范围。表示该依赖在编译和运行时生效，项目打包时也会将该依赖打包进去。。
- test：项目的测试配置，可以配置测试的配置。
- provided：使用此依赖范围的Maven依赖，编译和测试时有效，但在运行时无效。典型的例子是servlet-api，在运行时Web容器已经提供依赖，就不需要Maven重复地引入一遍。
- runtime：runtime范围表明编译时不需要生效，而只在运行时生效。典型的例子是JDBC驱动包，编译时只需要JDK的JDBC接口即可，只有运行项目时才需要具体的JDBC驱动。
- system：system如果有些你依赖的jar包没有Maven坐标的，它完全不在Maven体系中，这时候你可以把它下载到本地硬盘，然后通过system来引用。（不推荐使用）
<!-- 项目结构 -->
- version：项目的版本号，通常是时间戳或日期。
- groupId：依赖的groupId，可以是${project.groupId}、${project.parent.groupId}、${env.JAVA_HOME}等。
- name：项目的名称。
- url：项目的URL地址。
- packaging：项目的打包类型，如jar、war、ear等。
- artifactId：项目的名称，通常是工程名。
- artifactId //移除不想要得依赖版本号 

- description：项目的描述。
- inceptionYear：项目的创建年份。
- dependencies：项目的依赖列表，依赖可以是其他项目的groupId和artifactId，也可以是本地项目的groupId和artifactId。
- parent：项目的父工程，可以继承其他工程的配置。
- build：项目的构建配置，如插件配置、资源过滤配置等。
- properties：项目的属性配置，可以定义一些常量。
- repositories：项目的仓库列表，可以配置Maven私有仓库、Nexus私有仓库等。
- pluginRepositories：项目的插件仓库列表，可以配置Maven私有仓库、Nexus私有仓库等。
- distributionManagement：项目的分发配置，可以配置Maven私有仓库、Nexus私有仓库等。
- modules：项目的模块列表，可以配置子模块。
- dependencyManagement：项目的依赖管理配置，可以配置依赖版本号。
- profiles：项目的环境配置，可以配置不同环境的配置。
- reports：项目的报告配置，可以配置生成报告的配置。
- reporting：项目的报告配置，可以配置生成报告的配置。
- repositories：项目的仓库列表，可以配置Maven私有仓库、Nexus私有仓库等。
- pluginRepositories：项目的插件仓库列表，可以配置Maven私有仓库、Nexus私有仓库等。
- distributionManagement：项目的分发配置，可以配置Maven私有仓库、Nexus私有仓库等。
- import：import范围表明导入其他的POM文件，可以将公共的依赖配置放在父POM文件中，然后在子POM文件中导入。
- dependency：依赖配置，可以配置依赖的groupId、artifactId、version、scope、exclusions等。
- plugin：插件配置，可以配置插件的groupId、artifactId、version、configuration等。
-  scope：依赖范围，可以是compile、test、provided、runtime、system、import。
- optional：是否可选依赖，可选依赖不会强制依赖，默认false。
- exclusions：依赖排除，排除依赖后，该依赖不会被传递给依赖树。
- systemPath：系统路径，指定本地系统路径，仅在system范围有效。
- type：依赖类型，可以是jar、war、ear、pom、rar、ear、zip、tar、tar.gz、tar.bz2、zip、tar.xz等。
- classifier：依赖的附加信息，如sources、javadoc等。
- artifactId：依赖的artifactId，可以是${project.artifactId}、${project.parent.artifactId}、${env.JAVA_HOME}等。
- parent：依赖的父工程，可以是${project.parent.groupId}:${project.parent.artifactId}:${project.parent.version}。
### 结构示例
 - ###### <span style="color:red">锁定项目
```xml
<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-aop</artifactId>
      <version>4.2.4.RELEASE</version>
    </dependency>
  </dependencies>
</dependencyManagement>

```
  - ###### <span style="color:red">排除项目
```angular2html
<dependency>
  <groupId>org.springframework</groupId>
  <artifactId>spring-webmvc</artifactId>
  <version>4.2.4.RELEASE</version>
</dependency>
<dependency>
  <groupId>org.springframework</groupId>
  <artifactId>spring-context</artifactId>
  <version>5.2.12.RELEASE</version>
  <exclusions>
    <exclusion>
      <groupId>org.springframework</groupId>
      <artifactId>spring-aop</artifactId>
    </exclusion>
  </exclusions>
</dependency>

```
- ###### <span style="color:red"> 继承关系
```xml
<dependencyManagement>
<dependencies>
<!--父项目a-->
<dependency>
<groupId>com.itbaizhan</groupId>
<artifactId>parent_a</artifactId>
<version>1.0-SNAPSHOT</version*>
<type>pom</type>
<!-- 引入父项目，scope的值为import -->
<scope>import</scope>
</dependency>


    <!--父项目b-->
    <dependency>
      <groupId>com.itbaizhan</groupId>
      <artifactId>parent_b</artifactId>
      <version>1.0-SNAPSHOT</version>
      <type>pom</type>
      <scope>import</scope>
    </dependency>
  </dependencies>
</dependencyManagement>

```


##### 查找链接
- [Maven依赖查找链接](https://mvnrepository.com/)

#### Maven工程开发_构建Maven工程
- 打开 idea，选择创建一个新工程
<img src="/home/deepin/IdeaProjects/untitled2/MD笔记/Image/Maven/1.png">
- 选择Maven工程，并使用maven的web工程模板
<img src="/home/deepin/IdeaProjects/untitled2/MD笔记/Image/Maven/2.png">
- 点击 Next 填写项目信息
<img src="/home/deepin/IdeaProjects/untitled2/MD笔记/Image/Maven/3.png">
- 点击 Next，此处不做改动，点击Finish构建项目
<img src="/home/deepin/IdeaProjects/untitled2/MD笔记/Image/Maven/4.png">
- 手动添加src/main/java目录，此时该目录还不能写Java代码
- 将src/main/java目录设置为Java代码目录。
<img src="/home/deepin/IdeaProjects/untitled2/MD笔记/Image/Maven/5.png">

#### 测试方法注意事项
- 测试方法必须以test开头，并且必须有@Test注解，这样会单独运行
- 测试方法不能有返回值，只能有void类型。
- 测试方法不能有参数。
- @org.junit.Test注解可以添加在方法上，也可以添加在类上，可以独立运行测试方法不能有static修饰符。
##### operation.test()
  - import org.junit.Assert; // 导入断言类。
     - Assert.assertEquals(4, add); // 断言方法，判断结果是否正确。