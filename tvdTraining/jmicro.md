# Microservices mit Java (JMICRO)

## Dropwizard

- [Dropwizard - Home](https://www.dropwizard.io)
- [Dropwizard - Github](https://github.com/dropwizard)
- [Dropwizard Archetypes (mvn)](https://github.com/dropwizard/dropwizard/tree/master/dropwizard-archetypes)
- <a href="" target="_blank"></a>

### Examples

- [dropwizard/dropwizard-example/
](https://github.com/dropwizard/dropwizard/tree/master/dropwizard-example)
- [Dropwizard Tutorial – Hello World Example](https://howtodoinjava.com/dropwizard/tutorial-and-hello-world-example/)

### Minimum Dropwizard Example

```java
import io.dropwizard.Configuration;

public class AppConfiguration extends Configuration {
...
}
```

```java
import io.dropwizard.Application;

public class AppApplication extends Application<AppConfiguration> {
    public static void main(String[] args) throws Exception {
        new AppApplication().run(args);
    }
...
}
```

```sh
java -jar ./target/app--1.0-SNAPSHOT.jar server configuration.yml
```

Application healthcheck:

```sh
http://localhost:8081/healthcheck
```

## Spring Data

- <a href="" target="_blank"></a>

## Hibernate

- <a href="" target="_blank"></a>

## Kommunikation MS to MS

- <a href="" target="_blank"></a>

### Kafka

- <a href="" target="_blank"></a>

### Feign

- <a href="" target="_blank"></a>

### ActiveMQ

- <a href="" target="_blank"></a>

### RabbitMQ

- <a href="" target="_blank"></a>

## Spring Boot

- <a href="" target="_blank"></a>

## Wildfly Swarm / Thorntail

- <a href="" target="_blank"></a>
