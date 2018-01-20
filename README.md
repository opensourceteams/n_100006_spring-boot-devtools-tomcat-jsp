###Spring boot tomcat jsp 项目 热部署

- spring boot web项目热部署
- 改后台方法内容，可以自动部署
- 增加后台方法，可以自动部署 
- jsp页面传值后台接收
- 后台返回值，前台显示
- 解决控制台中文乱码问题
- debug调试
- git 地址 : https://github.com/opensourceteams/n_100006_spring-boot-devtools-tomcat-jsp
- 启动命令 :  spring-boot:run
- url:http://localhost:8080/jsp/helloMessageParam?name=b&age=100
- http://localhost:8080/jsp/helloMessageParam2?name=b&age=100

## pom 修改，支持热部署

    	<dependency>
    		  <groupId>org.springframework.boot</groupId>
    		  <artifactId>spring-boot-devtools</artifactId>
    		  <optional>true</optional>
    		  <scope>true</scope>
    		</dependency>
    
      <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <dependencies>
              <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>springloaded</artifactId>
                <version>1.2.8.RELEASE</version>
              </dependency>
            </dependencies>
          </plugin>


## pom.xml 支持热部署和debug调试

        <!-- 热部署 第一步 -->
        <dependency>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-devtools</artifactId>
          <optional>true</optional>
          <scope>true</scope>
        </dependency>
    
    
    
      <build>
        <sourceDirectory>src/main/java </sourceDirectory>
        <resources>
            <resource>
              <directory>src/main/resources</directory>
            </resource>
        </resources>
    
        <plugins>
          <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <!--允许linux上注册服务-->
            <configuration>
              <jvmArguments>
                -Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=y,address=5005
              </jvmArguments>
              <executable>true</executable>
            </configuration>
            <dependencies>
              <dependency>
                <groupId>org.springframework</groupId>
                <artifactId>springloaded</artifactId>
                <version>1.2.8.RELEASE</version>
              </dependency>
            </dependencies>
          </plugin>
        </plugins>
      </build>
    

## 新建客户端远程连接
- 新建 remote 点确定
- 先启动 springboot:run,再启动　remote