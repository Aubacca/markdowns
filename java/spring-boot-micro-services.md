# Spring Boot - Micro Services

* [Service Discovery: Eureka Clients](https://cloud.spring.io/spring-cloud-netflix/multi/multi__service_discovery_eureka_clients.html)
* [Service Registration and Discovery](https://spring.io/guides/gs/service-registration-and-discovery/)
* [Spring Cloud Sample](https://github.com/spring-cloud-samples)
* [Eureka interop Release Train at github](https://github.com/spring-cloud-samples/eureka-release-train-interop)

## Eureka Discovery Server Settings

* [Eureka Server Sample at github](https://github.com/spring-cloud-samples/eureka)
* [Hystrix Dashboard at github](https://github.com/spring-cloud-samples/hystrix-dashboard)
* [feign-eureka at github](https://github.com/spring-cloud-samples/feign-eureka)

pom.xml
```xml
...
	<properties>
		<java.version>1.8</java.version>
		<spring-cloud.version>Greenwich.SR1</spring-cloud.version>
	</properties>

...
	<dependendies>
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
		</dependency>
...
	</dependencies>

...
	<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>org.springframework.cloud</groupId>
				<artifactId>spring-cloud-dependencies</artifactId>
				<version>${spring-cloud.version}</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
		</dependencies>
	</dependencyManagement>
...
```

Example main Spring Boot class: DiscoveryServerApplication
```java
package ch.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.server.EnableEurekaServer;

@SpringBootApplication
@EnableEurekaServer
public class DiscoveryServerApplication {
	public static void main(String[] args) {
		SpringApplication.run(DiscoveryServerApplication.class, args);
	}
}
```

application.properties
```xml
# Eureka Server Settings
eureka.client.registerWithEureka = false
eureka.client.fetchRegistry = false
server.port = 8761
```

## Eureka Client Micro Service Settings.

pom.xml
```xml
...
	<properties>
		<java.version>1.8</java.version>
		<spring-cloud.version>Greenwich.SR1</spring-cloud.version>
	</properties>

...
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
		</dependency>
...
	</dependencies>

...
	<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>org.springframework.cloud</groupId>
				<artifactId>spring-cloud-dependencies</artifactId>
				<version>${spring-cloud.version}</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
		</dependencies>
	</dependencyManagement>
...
```

Example main Spring Boot class: MSClientApplication
```java
package ch.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.netflix.eureka.EnableEurekaClient;

@SpringBootApplication
@EnableEurekaClient
public class MSClientApplication {
	public static void main(String[] args) {
		SpringApplication.run(MSClientApplication.class, args);
	}
}
```

application.properties
```xml
spring.application.name=ms-demo
```