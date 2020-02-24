# Microservices mit Java (JMICRO)

## Dropwizard

- [Dropwizard - Home](https://www.dropwizard.io)
- [Dropwizard - Dropwizard Configuration Reference](https://www.dropwizard.io/en/stable/manual/configuration.html)
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
java -jar ./target/app-1.0-SNAPSHOT.jar server configuration.yml
```

Application Admin/Monitoring:

```sh
http://localhost:8081/
```

### Lösungvorschlag für die Aufgaben

1. AuthorStore via lifecycle verwalten lassen (see Managed Objects at https://www.dropwizard.io/en/latest/manual/core.html).
2. Danache AuthorStore mit Singleton AuthorList laden lassen (use storeBootstrapData at https://www.dropwizard.io/en/latest/manual/core.html).
3. Register AuthorResource bei Jersey (see Resources and Environments at https://www.dropwizard.io/en/latest/manual/core.html).
4. Erstelle AuthorStoreHealthCheck um den AuthorStore zu überwachen ob er leer ist (see Health Checks at https://www.dropwizard.io/en/latest/manual/core.html)
5. Erstelle und registriere ReloadAuthorTask um AuthorStore neu zu laden (see Tasks at https://www.dropwizard.io/en/latest/manual/core.html).

## Thorntail (Wildfly Swarm)

- [Thorntail - EVOLUTION OF ENTERPRISE JAVA](https://thorntail.io/)
- [Thorntail - Thorntail Documentation](https://docs.thorntail.io/2.6.0.Final/)
- <a href="" target="_blank"></a>

### Add Thorntail to project

1. Import the BOM (Bill of Materials) and fractions in pom.xml (**Java EE Application**)

```sh
<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>io.thorntail</groupId>
      <artifactId>bom</artifactId>
      <version>${version.thorntail}</version>
      <scope>import</scope>
      <type>pom</type>
    </dependency>
  </dependencies>
</dependencyManagement>

<dependencies>
    <dependency>
        <groupId>io.thorntail</groupId>
        <artifactId>jaxrs</artifactId>
    </dependency>
</dependencies>
```

2. Add Thorntail maven plugin into pom.xml (**Maven Plugin**)

```sh
<plugin>
  <groupId>io.thorntail</groupId>
  <artifactId>thorntail-maven-plugin</artifactId>
  <version>${version.thorntail}</version>
  <executions>
    <execution>
      <goals>
        <goal>package</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

3. Generate Uber-jar and execute it (**Build and Run**)

```sh
mvn package
java -jar <myapp>-thorntail.jar
```

### Examples

Bookcatalog:

```sh
bookcatalog>java -jar target/bookcatalog-swarm.jar
```

### Additional Documentation

- [Jakarta EE 9 - 2019 Outlook](https://www.eclipse.org/community/eclipse_newsletter/2019/february/Jakarta_EE_9.php)
- [Big Bang oder inkrementell: Die Zukunft von Jakarta EE liegt in den Händen der Community](https://jaxenter.de/javax-jakarta-ee-9-big-bang-84101)
- [Java EE Web Profile vs Java EE Full Platform](https://stackoverflow.com/questions/24239978/java-ee-web-profile-vs-java-ee-full-platform)
- [Eclipse MicroProfile Optimizing Enterprise Java for a Microservices Architecture](https://microprofile.io/)
    - [Apache TomEE](https://tomee.apache.org/)
    - [kumuluzEE](https://ee.kumuluz.com/)
    - [payara](https://www.payara.fish/)
    - [Websphere Liberty](https://www.ibm.com/cloud/websphere-liberty)
- [MicroProfile unter der Lupe, Teil 1: Config API ](https://www.heise.de/developer/artikel/MicroProfile-unter-der-Lupe-Teil-1-Config-API-3928886.html)

## Spring Boot

- <a href="" target="_blank"></a>

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
