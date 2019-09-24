# Java

- <a href="https://howtodoinjava.com/" target="_blank">Spring Framework and others. <b><== !IMPORTANT</b></a>
- <a href="http://www.java2s.com/" target="_blank">Java how to .. <b><== !IMPORTANT</b></a>
- <a href="https://blog.oio.de/2018/03/22/java-ee-wurde-in-jakarta-ee-umbenannt/" target="_blank">Java EE wurde in Jakarta EE umbenannt</a>
- <a href="https://docs.oracle.com/javase/8/docs/technotes/guides/language/enhancements.html" target="_blank">Java 8 Programming Language Enhancements</a>
- <a href="https://www.oio.de/public/java/java9/java-9-neuerungen-im-ueberblick.htm?TVD" target="_blank">Java 9 - Die Neuerungen im Überblick</a>
- <a href="https://jaxenter.de/java-11-features-news-75411" target="_blank">Java 11 ist da! Die neuen Features auf einen Blick</a>
- <a href="https://blog.oio.de/2019/03/06/java-12-uberblick/" target="_blank">Java 12 Überblick</a>
- <a href="https://blog.oio.de/2019/09/23/java-13-uberblick/" target="_blank">Java 13 Überblick</a>
- <a href="" target="_blank"></a>

## Best Practices

- <a href="./java-servlet.md" target="_blank">Java Servlet</a>

### Trivadis Training

Kontakte: Thorsten Maier, Thomas Bröll

- <a href="file:///C:/workspace/projects/tvd/markdowns/tvdTraining/ad-java-b.md" target="_blank">Java for Developers - Additionals</a>
- <a href="../tvdTraining/fspring.md" target="_blank">Einführung in das Spring Framework (FSPRING)</a>

#### Install jdbc driver in local maven repository

```sh
mvn install:install-file -Dfile=C:\Users\rohnerp\Downloads\jdbc\ojdbc7.jar -DgroupId=com.oracle -DartifactId=ojdbc7 -Dversion=12.1.0 -Dpackaging=jar
```

```sh
mvn install:install-file -Dfile=C:\tools\sqldeveloper\jdbc\lib\ojdbc8.jar -DgroupId=com.oracle -DartifactId=ojdbc8 -Dversion=12.2.0 -Dpackaging=jar
```

## Web Applications

- <a href="https://docs.oracle.com/cd/E14571_01/web.1111/e13712/web_xml.htm#WBAPP502" target="_blank">Oracle - web.xml Deployment Descriptor Elements</a>
- <a href="https://cloud.google.com/appengine/docs/standard/java/config/webxml" target="_blank">Google - Bereitstellungsdeskriptor: web.xml</a>

### Web Server

### Application Server

### Spring Boot - Micro Services

- <a href="./spring-boot-micro-services.md" target="_blank">Spring Boot - Micro Services</a>
- <a href="https://dzone.com/articles/microservices-with-cqrs-and-event-sourcing" target="_blank">Microservices With CQRS and Event Sourcing</a>
- <a href="https://microservices.io/patterns/microservices.html" target="_blank">Pattern: Microservice Architecture</a>
- <a href="https://microservices.io/patterns/data/cqrs.html" target="_blank">Pattern: Command Query Responsibility Segregation (CQRS)</a>
- <a href="https://microservices.io/patterns/data/database-per-service.html" target="_blank">Pattern: Database per service</a>

### Spring Boot - Swagger

- <a href="./spring-boot-swagger.md" target="_blank">Spring Boot - Swagger</a>

### Application Server: Servlet Container

- <a href="https://www.eclipse.org/jetty/documentation/9.4.x/jetty-admin-guide.html" target="_blank">Jetty - Jetty Administration Guide</a>

#### The Jetty Maven plugin

- Jetty: maven plugin with some configuration

```xml
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.eclipse.jetty</groupId>
        <artifactId>jetty-maven-plugin</artifactId>
        <version>9.2.11.v20150529</version>
        <configuration>
          <scanIntervalSeconds>10</scanIntervalSeconds>
          <webApp>
            <contextPath>/your-prefered-app-path</contextPath>
          </webApp>
          <httpConnector>
            <port>8888</port>
          </httpConnector>
        </configuration>
      </plugin>
    </plugins>
  </build>
```

Then start Jetty via maven:

```sh
mvn jetty:run
```

#### The Tomcat Maven plugin

- Tomcat: maven plugin with some configuration

```xml
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.2</version>
        <configuration>
          <scanIntervalSeconds>10</scanIntervalSeconds>
          <webApp>
            <contextPath>/your-prefered-app-path</contextPath>
          </webApp>
          <httpConnector>
            <port>8888</port>
          </httpConnector>
        </configuration>
      </plugin>
    </plugins>
  </build>
```

Then start Tomcat via maven:

```sh
mvn clean install tomcat7:run
```

#### The Webapp Runner Maven plugin

<a href="https://github.com/jsimone/webapp-runner" target="_blank">Webapp Runner</a>

Webapp Runner: maven plugin with some configuration

```xml
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-dependency-plugin</artifactId>
        <version>2.3</version>
        <executions>
          <execution>
            <phase>package</phase>
            <goals><goal>copy</goal></goals>
            <configuration>
              <artifactItems>
                <artifactItem>
                  <groupId>com.github.jsimone</groupId>
                  <artifactId>webapp-runner</artifactId>
                  <version>${webapp-runner.version</version>
                  <destFileName>webapp-runner.jar</destFileName>
                </artifactItem>
              </artifactItems>
            </configuration>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
```

Then package app via maven:

```sh
mvn package
```

Then launch app via java:

```sh
java -jar target/dependency/webapp-runner.jar target/<appname>.war
```

Then launch app via java. In versions 7.0.29.1 and newer support for a session manager that stores sessions in memcache is built in.

```sh
java -jar target/dependency/webapp-runner.jar --session-store memcache target/<appname>.war
```

### Maven

<a href="http://maven.apache.org/" target="_blank">Apache Maven Project</a>

#### Maven Repositories

- <a href="https://mvnrepository.com/" target="_blank">Maven Repository</a>
- <a href="https://search.maven.org/" target="_blank">The Central Repository</a>

#### Maven Archetypes

- Simple Web Application

```sh
mvn archetype:generate -DarchetypeArtifactId=maven-archetype-webapp
```

## Tools, Tipps and Tricks

### Lambdas

- <a href="https://www.baeldung.com/java-8-lambda-expressions-tips" target="_blank">Lambda Expressions and Functional Interfaces: Tips and Best Practices</a>
- <a href="https://medium.freecodecamp.org/learn-these-4-things-and-working-with-lambda-expressions-b0ab36e0fffc" target="_blank">How to start working with Lambda Expressions in Java</a>

### Spring Boot

- <a href="http://spring.io/projects/spring-boot" target="_blank">Spring Boot: Documention</a>
- <a href="http://www.mkyong.com/tutorials/spring-boot-tutorials/" target="_blank">Mkyong: Spring Boot Tutorials</a>

### Building web apps

- <a href="https://vaadin.com/" target="_blank">vaadin (UI)</a>

## Architecture

### Servers

- <a href="https://kafka.apache.org/" target="_blank">Apache Kafka</a>

### Domain Driven Design (DDD)

Domain Driven Design ist eine Herangehensweise an die Modellierung komplexer Software. Die Modellierung der Software wird dabei massgeblich von den umzusetzenden Fachlichkeiten der Anwendungsdomäne beeinflusst. Der Begriff „Domain-driven Design“ wurde 2003 von Eric Evans in seinem gleichnamigen Buch geprägt.

- <a href="https://jqassistant.org/" target="_blank">jQAssistant: check rules and project architecture</a>

#### Youtube

- <a href="https://www.youtube.com/watch?v=XOyyLwyrBQU" target="_blank">Onion architecture with stereotypes by Alain Sahli (inclusive **jQAssistant**)</a>
- <a href="https://www.youtube.com/watch?v=pL9XeNjy_z4" target="_blank">Domain Driven Design Through Onion Architecture</a>

### GraphQL

GraphQL ist eine Open-Source-Datenabfrage- und -manipulationssprache und eine Laufzeitumgebung zum Ausführen von Abfragen mit vorhandenen Daten. GraphQL wurde 2012 intern von Facebook entwickelt, bevor es 2015 veröffentlicht wurde.

#### Youtube

- <a href="https://www.youtube.com/watch?v=PEcJxkylcRM" target="_blank">Building a GraphQL Server [Part 1] - What Is GraphQL? (Serie of 5)</a>

## Security

- <a href="https://blog.oio.de/2018/08/20/eine-einfuhrung-in-oauth-2/" target="_blank">Eine Einführung in OAuth 2</a>

## Struts

- <a href="https://www.mkyong.com/struts2/struts-2-hello-world-example/" target="_blank">Mkyong - Struts 2 Hello World Example</a>
