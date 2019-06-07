# Einführung in das Spring Framework (FSPRING)

## Motivation und Einführung

Für OOP benötigt es für diese Qualität drei Schritte:

- Modularisierung (Teile und Herrsche) --> Umsetzung: Programmierung gegen Interfaces!

      - Single Reponsible
      - Don't Repeat yourself (DRY)
      - Separation of Concerns

- Entkopplung

      - Inversion of Control (IoC): Don't do it yourself let somebody else do it for you.
      - Dependency Inversion

         - High-level modules should not depend on low-level modules. Both should depend on abstractions.
         - Abstractions should not depend on details. Details should depend on abstractions.

- Kompatibilität fördern

      - Minimum Assumption --> use only interfaces
      - Open Close Principle --> open for new features but closed for changes.

### Internet

- <a href="https://de.wikipedia.org/wiki/Softwarequalit%C3%A4t" target="_blank">Wikipedia - Softwarequalität</a>
- <a href="https://de.wikipedia.org/wiki/ISO/IEC_9126" target="_blank">Wikipedia - Qualitätskriterien für Software - ISO/IEC 9126</a>
- <a href="https://www.wildfly.org/" target="_blank">EJB Container - WildFly</a>
- <a href="https://github.com/eclipse-ee4j/glassfish" target="_blank">EJB Container - GlassFish</a>
- <a href="http://geronimo.apache.org/" target="_blank">EJB Container - Apache Geronimo</a>
- <a href="https://en.wikipedia.org/wiki/Web_container" target="_blank">Wikipedia - Servlet Container (aka Web Container)</a>

### Samples

Dependency Inversion: Wrong

```java
public class BackEndDeveloper {
    public void writeJava() {
    }
}

public class FrontEndDeveloper {
    public void writeJavascript() {
    }
}

public class Project {
    private BackEndDeveloper backEndDeveloper = new BackEndDeveloper();
    private FrontEndDeveloper frontEndDeveloper = new FrontEndDeveloper();
    public void implement() {
        backEndDeveloper.writeJava();
        frontEndDeveloper.writeJavascript();
    }
}
```

Dependency Inversion: Correct

```java
public interface Developer {
    void develop();
}

public class BackEndDeveloper implements Developer {
    @Override
    public void develop() {
        writeJava();
    }
    private void writeJava() {
    }
}

public class FrontEndDeveloper implements Developer {
    @Override
    public void develop() {
        writeJavascript();
    }
    public void writeJavascript() {
    }
}

public class Project {
    private List<Developer> developers;
    public Project(List<Developer> developers) {
        this.developers = developers;
    }
    public void implement() {
        developers.forEach(d->d.develop());
    }
}
```

## Spring Grundlagen

### Internet

- <a href="https://howtodoinjava.com/spring-5-tutorial/" target="_blank">Spring 5 Tutorial</a>
- <a href="http://www.java2s.com/Tutorials/Java/Spring/index.htm" target="_blank">Spring Tutorial - Spring Introduction</a>

### Samples

spring-configuration.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns:context="http://www.springframework.org/schema/context"
	xmlns:util="http://www.springframework.org/schema/util"
	xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
    http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd
    http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util.xsd"
	default-init-method="initBean" default-destroy-method="destroyBean">

    <!-- Sample bean definition with Spring XML configuration. -->
	<bean id="personSpring" class="ch.rohner.spring.beans.Person" >
		<description>XML configuration is not in the class path but in the project root directory.</description>
		<property name="name" value="With ApplicationContext and property in spring.xml created!"></property>
	</bean>

	<!-- Following definition can replace all other org.springframework.. bean definitions. -->
	<context:annotation-config />
</beans>
```

```java
...
ApplicationContext context = new ClassPathXmlApplicationContext("spring-configuration.xml");
Person person = (Person) context.getBean("personSpring");
...
```

## Testen mit Spring

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Spring AOP

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Datenzugriffsschicht

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Spring Remoting

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Spring Web-Integration

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```

## Spring Security

### Internet

- <a href="" target="_blank"></a>

### Samples

```java

```
