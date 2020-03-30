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

### Examples

Authorservice:

```sh
authorservice>java -jar .\target\authorservice-1.0-SNAPSHOT.jar server authorservice.yml
```

Application Admin/Monitoring:

```sh
http://localhost:8081/
```

### Lösungsvorschlag für die Aufgaben

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
- [MicroProfile unter der Lupe, Teil 1: Config API](https://www.heise.de/developer/artikel/MicroProfile-unter-der-Lupe-Teil-1-Config-API-3928886.html)
- [CDI - Introduction to Contexts and Dependency Injection for Java EE](https://javaee.github.io/tutorial/cdi-basic.html)
- [CDI - Java EE 7 Annotations](http://www.sws.bfh.ch/~fischli/courses/info/javaee/doc/JavaEE7AnnotationsCheatSheet.pdf)
- [JAX-RS - Building RESTful Web Services with JAX-RS](https://docs.oracle.com/javaee/7/tutorial/jaxrs.htm)
- [JAX-RS - Package javax.ws.rs](https://javaee.github.io/javaee-spec/javadocs/javax/ws/rs/package-summary.html)

## Spring Boot

- [Spring](https://spring.io/)
- [Spring Boot](https://spring.io/projects/spring-boot)
  - [Spring Initializr](https://start.spring.io/)
- [Spring Annotations Cheat Sheet](https://www.jrebel.com/blog/spring-annotations-cheat-sheet)

### Lösungsvorschlag für die Aufgaben - Microservice: Bücherverwaltung

1. Start with class **de.oio.jmicro.LibraryServiceApplication**.
   - do not use class **de.oio.jmicro.libraryservice.LibraryServiceApplication** for this exercise.
2. Create rest controller **de.oio.jmicro.libraryservice.controller.LibraryRestController** in package **de.oio.jmicro.libraryservice.controller** so it can be used with path "/library". Add the following two methods to it.
   - implement **public LibraryBook borrow(@PathVariable("username") String username, @PathVariable("bookId") Long bookId)**
     - must create a new row with username and bookId which was borrowed. Return a list of borrowed books by a username.
   - implement **public List&lt;LibraryBook> list(@PathVariable("username") String username)**
     - must return a list of borrowed books by a username.

## Spring Data

- [Spring Data](https://spring.io/projects/spring-data)
  - [Spring Data - JPA](https://spring.io/projects/spring-data-jpa)
    - [Spring Data - CRUD Repository](https://docs.spring.io/spring-data/data-commons/docs/current/api/org/springframework/data/repository/CrudRepository.html)
    - [Spring Data - PagingAndSortingRepository](https://docs.spring.io/spring-data/data-commons/docs/current/api/org/springframework/data/repository/PagingAndSortingRepository.html)
    - [Spring Data - JPA Repository](https://docs.spring.io/spring-data/data-jpa/docs/current/api/org/springframework/data/jpa/repository/JpaRepository.html)
      - JpaRepository contains the full API of CrudRepository and PagingAndSortingRepository

### Lösungsvorschlag für die Aufgaben - Persistieren mit Spring Data

1. Start with class **de.oio.jmicro.libraryservice.LibraryServiceApplication**.
   - do not use class **de.oio.jmicro.LibraryServiceApplication** for this exercise.
2. Create **de.oio.jmicro.libraryservice.repository.LibraryBookRepository**.
   - implement **List&lt;LibraryBook> findByBorrower(String borrower);**
3. Refactore **de.oio.jmicro.libraryservice.controller.LibraryRestController** by using the new created repository.

#### Access the database - h2 Console

- application.properties:
    - spring.h2.console.enabled=true
- http://localhost:8050/h2-console
- JDBC URL: jdbc:h2:mem:testdb

## Kommunikation Microservice to Microservice

- Fowler, Martin: [Steps toward REST](http://martinfowler.com/articles/richardsonMaturityModel.html)
- [HATEOAS Driven REST APIs](https://restfulapi.net/hateoas/)
- [Jakarta EE - Jersey](https://eclipse-ee4j.github.io/jersey/)
- [github - JAX-RS API](https://github.com/jax-rs)
- [github - OpenFeign/feign](https://github.com/OpenFeign/feign)
- [Spring Cloud Stream](https://spring.io/projects/spring-cloud-stream)
  - [AcitveMQ](https://activemq.apache.org/)
  - [Apache Kafka](https://kafka.apache.org/)
  - [RabbitMQ](https://www.rabbitmq.com/)
- [Spring Cloud Config](https://cloud.spring.io/spring-cloud-config/reference/html/)
- [Circuit Breaker - Hystrix](https://spring.io/guides/gs/circuit-breaker/)
- [Circuit Breaker: Hystrix Clients](https://cloud.spring.io/spring-cloud-netflix/multi/multi__circuit_breaker_hystrix_clients.html)
- [Spring Session](https://spring.io/projects/spring-session)
- Intelligent Routing
  - [Routing and Filtering](https://spring.io/guides/gs/routing-and-filtering/)
  - [Router and Filter: Zuul](https://cloud.spring.io/spring-cloud-netflix/multi/multi__router_and_filter_zuul.html)
- API-Gateway
  - [Spring Cloud Gateway](https://spring.io/projects/spring-cloud-gateway)
  - [Building a Gateway](https://spring.io/guides/gs/gateway/)
- Client Side Load Balancing
  - [Client Side Load Balancing with Ribbon and Spring Cloud](https://spring.io/guides/gs/client-side-load-balancing/)
  - [Client Side Load Balancer: Ribbon](https://cloud.spring.io/spring-cloud-netflix/multi/multi_spring-cloud-ribbon.html)
- [Spring Retry](https://docs.spring.io/spring-batch/docs/current/reference/html/retry.html)

### Lösungsvorschlag für die Aufgaben - Rest-Client mit RestTemplate

1. Preparation of depending micro service **bookcatalog**:
   1. Go into directory "./Loesungen/bookmanagement/bookcatalog"
   1. Create micro service bookcatalog with: <code>mvn package</code>
   1. Start micro service bookcatalog with: <code>java -jar target/bookcatalog-swarm.jar</code>
1. Create service **de.oio.jmicro.libraryservice.search.SearchService**
   - implement **public List&lt;Book> search(String query)**. Do use RestTemplate.
     - use api url: _http://localhost:8070/books/search?query={query}_
1. Create rest controller **de.oio.jmicro.libraryservice.search.SearchRestController**
   - implement **public List&lt;Book> search(@RequestParam(value = "query") String query)** and use SearchService.search.
     - mapping: /search

### Lösungsvorschlag für die Aufgaben - Service Discovery mit Eureka

1. Define **servcie-discovery** as an Eureka Server and start it up.
    - [Start a Eureka Service Registry](https://spring.io/guides/gs/service-registration-and-discovery/#initial)
2. In module **libraryservice** define **de.oio.jmicro.libraryservice.LibraryServiceApplication** as an Eureka Client and start it up.
    - [Talking to the Registry](https://spring.io/guides/gs/service-registration-and-discovery/#talking_to_the_registry)

Demo: DiscoveryClient - see module **bookmanagement.discovery-client**.

### Lösungsvorschlag für die Aufgaben - Resilience mit Hystrix

1. Start the **service-discovery** incase you are still using the discovery service (Eureka Server).
2. Use **@HystrixCommand(..)** to implement the fallback method when calling the **bookcatalog** module.
3. Run the **LibraryServiceApplication**.
4. Start and stop the **bookcatalog** module to test the cicuit breaker.

Demo: [Hystrix Dashboard](http://localhost:8050/hystrix)

## Testing

- [Asciidoctor](https://asciidoctor.org/)
- [JQAssistant](https://jqassistant.org/)
- [Spring Cloud Contract](https://spring.io/projects/spring-cloud-contract)

## Security

- [Spring Security](http://projects.spring.io/spring-security/)
- [Spring - OAuth2RestTemplate](https://docs.spring.io/spring-security/oauth/apidocs/org/springframework/security/oauth2/client/OAuth2RestTemplate.html)
