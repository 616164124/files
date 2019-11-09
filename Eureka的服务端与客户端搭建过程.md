**1、服务端搭建**

​	（1）选择新建模块，建立springboot lnitial 选择

​	（2）pom.xml

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.6.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.example</groupId>
    <artifactId>service</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>service</name>
    <description>Demo project for Spring Boot</description>

​    <properties>
​        <java.version>1.8</java.version>
​        <spring-cloud.version>Greenwich.SR1</spring-cloud.version>
​    </properties>

​    <dependencies>
​        <dependency>
​            <groupId>org.springframework.cloud</groupId>
​            <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
​        </dependency>

​        <dependency>
​            <groupId>org.springframework.boot</groupId>
​            <artifactId>spring-boot-starter-test</artifactId>
​            <scope>test</scope>
​        </dependency>
​	
​		
​        <dependency>
​            <groupId>com.sun.xml.bind</groupId>
​            <artifactId>jaxb-impl</artifactId>
​            <version>2.4.0-b180830.0438</version>
​        </dependency>
​        <dependency>
​            <groupId>org.glassfish.jaxb</groupId>
​            <artifactId>jaxb-runtime</artifactId>
​            <version>2.3.0</version>
​        </dependency>
​        <dependency>
​            <groupId>javax.activation</groupId>
​            <artifactId>activation</artifactId>
​            <version>1.1.1</version>
​        </dependency>



​    </dependencies>



​    <dependencyManagement>
​        <dependencies>
​            <dependency>
​                <groupId>org.springframework.cloud</groupId>
​                <artifactId>spring-cloud-dependencies</artifactId>
​                <version>${spring-cloud.version}</version>
​                <type>pom</type>
​                <scope>import</scope>
​            </dependency>
​        </dependencies>
​    </dependencyManagement>

​    <build>
​        <plugins>
​            <plugin>
​                <groupId>org.springframework.boot</groupId>
​                <artifactId>spring-boot-maven-plugin</artifactId>
​            </plugin>
​        </plugins>
​    </build>

</project>

(3)yml

```
server:
  port: 8761
eureka:
  instance:
    hostname: localhost
  client:
    registerWithEureka: 'false'
    fetchRegistry: 'false'
    serviceUrl:
      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/

```

(4)启动类

```
package com.example.service;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

@SpringBootApplication
@EnableEurekaServer
public class ServiceApplication {

​    public static void main(String[] args) {
​        SpringApplication.run(ServiceApplication.class, args);
​    }

}
```

2、客户端搭建

（1）跟服务端一样

（2）pom.xml

<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.1.6.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.example</groupId>
    <artifactId>client</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>client</name>
    <description>Demo project for Spring Boot</description>

​    <properties>
​        <java.version>1.8</java.version>
​        <spring-cloud.version>Greenwich.SR1</spring-cloud.version>
​    </properties>

​    <dependencies>
​        <dependency>
​            <groupId>org.springframework.cloud</groupId>
​            <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
​        </dependency>

​        <dependency>
​            <groupId>org.springframework.boot</groupId>
​            <artifactId>spring-boot-starter-test</artifactId>
​            <scope>test</scope>
​        </dependency>

​        <dependency>
​            <groupId>org.springframework.boot</groupId>
​            <artifactId>spring-boot-starter-web</artifactId>
​        </dependency>

​        <dependency>
​            <groupId>org.springframework.boot</groupId>
​            <artifactId>spring-boot-starter-actuator</artifactId>
​        </dependency>


​    </dependencies>

​    <dependencyManagement>
​        <dependencies>
​            <dependency>
​                <groupId>org.springframework.cloud</groupId>
​                <artifactId>spring-cloud-dependencies</artifactId>
​                <version>${spring-cloud.version}</version>
​                <type>pom</type>
​                <scope>import</scope>
​            </dependency>

​        </dependencies>
​    </dependencyManagement>

​    <build>
​        <plugins>
​            <plugin>
​                <groupId>org.springframework.boot</groupId>
​                <artifactId>spring-boot-maven-plugin</artifactId>
​            </plugin>
​        </plugins>
​    </build>

</project>

（3）yml

server:
  port: 8762
eureka:
  instance:
    instanceId: producer-server
    preferIpAddress: true
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/
spring:
   application:
     name: producer-server
#info代表的是当使用者点击这个服务的链接是会展示下面这些信息.
info:
   app-name: stjh
   company.name: www.baidu.com
   build.artifactId: producer-server
   build.version: '1.0'

(4)启动类

package com.example.client;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;

@SpringBootApplication
@EnableEurekaClient
public class ClientApplication {

​    public static void main(String[] args) {
​        SpringApplication.run(ClientApplication.class, args);
​    }

}



**注意：** <1>springboot中版本的问题，pom文件不一定一模一样的！！！

​	    <2>yml文件中，注释最好不要在行尾





