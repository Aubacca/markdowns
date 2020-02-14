# Microservices mit Java (JMICRO)

## Dropwizard

- <a href="https://www.dropwizard.io" target="_blank">Dropwizard - Home</a>
- <a href="https://github.com/dropwizard" target="_blank">Dripwizard - Github</a>
- <a href="https://github.com/dropwizard/dropwizard/tree/master/dropwizard-archetypes" target="_blank">Dropwizard Archetypes (mvn)</a>
- <a href="" target="_blank"></a>
- <a href="" target="_blank"></a>
- <a href="" target="_blank"></a>

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
