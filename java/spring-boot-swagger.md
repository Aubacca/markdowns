# Spring Boot - Micro Services

pom.xml
```xml
...
    <properties>
        <springfox-swagger2.version>2.7.0</springfox-swagger2.version>
...
    </properties>
    
...

    <dependencies>
        <!-- Swager Settings. -->
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger2</artifactId>
            <version>${springfox-swagger2.version}</version>
        </dependency>
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger-ui</artifactId>
            <version>${springfox-swagger2.version}</version>
        </dependency>
...
    </dependencies>
...
```

Example main Spring Boot class: MsChuckApplication
```java
package ch.rohner.microservices.mschuck;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Lazy;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

@SpringBootApplication
@EnableEurekaClient
@EnableSwagger2
public class MsChuckApplication {

    public static void main(String[] args) {
        SpringApplication.run(MsChuckApplication.class, args);
    }

    @Bean
    public Docket productApi() {
        return new Docket(DocumentationType.SWAGGER_2).select()
                .apis(RequestHandlerSelectors.basePackage("ch.rohner.microservices.mschuck.api")).build();
    }
}
```