# Core Fundamentals & Features

In this section you are going to learn about a few of the core fundamentals of Spring. It doesn't make sense to take a
deep dive into these topics now because it might be a little confusing and overwhelming. Understanding what some of these
terms mean is enough to get you going. Once you have a foundation for building Spring applications you can go back to
the documentation and revisit them for a bit of a deeper dive.

## Structuring you code

There is no requirement for structuring your code in a specific way. However, there are some best practices that you should follow.

    - Try to avoid creating a class that does not include a package declearation (default package).
    - Main Application in root package above other classes.
    - If you're on a team create a plan that makes sense for your team (and not just you).
    - Architecture (Layered/Hexigonal/).

Creat the following class in /src/main/java - default package: 

```java
import org.springframework.stereotype.Component;

@Component
public class Message {

    public String getDefaultMessage() {
        return "Hello, Runnerz!";
    }

}
```

Start the application, this class 'bean' is nowhere to be found. If you move it into a package that is above where your 
main application class is you will have the same problem. 

`/src/main/java/dev/danvega/Message.java`

## Spring IoC Container / Application Context

The `org.springframework.context.ApplicationContext` interface represents the Spring IoC container and is responsible for instantiating, configuring, and assembling the beans.

- Open `org.springframework.context.ApplicationContext`
- View the classes it inherits from (superclasses)`
- The configuration metadata is represented in XML, Java annotations, or Java code.

## Spring Beans

A Spring IoC container manages one or more beans. These beans are created with the configuration metadata that you supply to the container.

- Please raise your had if you ever created an instance of class 🙋🏼‍♂️
- We need to tell Spring about the classes we want it to manage for us
- Your Class + Configuration Metadata = Spring Bean
  - [Class](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-class)
  - [Name](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-beanname)
  - [Scopes](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-scopes)
  - more ...
- @Bean
  - Create a `@Configuration` class
- @Component / @Controller / @RestController / @Service / @Repository

Now that you understand what a bean is and the container that manages them we can revisit the problem we took a look at
earlier. 

- `@ComponentScan(basePackages = {"dev.danvega"})`
- `@SpringBootApplication(scanBasePackages = {"dev.danvega"})`
- `Arrays.stream(context.getBeanDefinitionNames()).forEach(System.out::println);`
- IntelliJ Beans

## Dependency Injection & IoC

Now that you understand what Beans and the container are we can talk about Dependency Injection (DI) and Inversion of
Control (IoC). 

Dependency injection (DI) is a process whereby objects define their dependencies (that is, the other objects with which they work) only through constructor arguments, arguments to a factory method, or properties that are set on the object instance after it is constructed or returned from a factory method. The container then injects those dependencies when it creates the bean.

- Demo 
- Write a test

[Spring Constructor Injection: Why is it the recommended approach to Dependency Injection?](https://youtu.be/aX-bgylmprA)

## Configuration

- application.properties / application.yml
- Externalized Configuration (Property Sources)

## Profiles

- What are profiles
- Why would you want to use them? 

## Actuator

- What is the Spring Boot Actuator?
- How to add it to your application 
- How to configure it

## Logging

Default configurations are provided for Java Util Logging, Log4j2, and Logback. In each case, loggers are pre-configured to use console output with optional file output also available.

- spring-boot-starter-web -> spring-boot-starter -> spring-boot-starter-logging

```xml
  <dependencies>
    <dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
      <version>1.4.5</version>
      <scope>compile</scope>
    </dependency>
    <dependency>
      <groupId>org.apache.logging.log4j</groupId>
      <artifactId>log4j-to-slf4j</artifactId>
      <version>2.19.0</version>
      <scope>compile</scope>
    </dependency>
    <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>jul-to-slf4j</artifactId>
      <version>2.0.4</version>
      <scope>compile</scope>
    </dependency>
  </dependencies>
```

The following items are output:

- Date and Time: Millisecond precision and easily sortable.
- Log Level: ERROR, WARN, INFO, DEBUG, or TRACE.
- Process ID.
- A --- separator to distinguish the start of actual log messages.
- Thread name: Enclosed in square brackets (may be truncated for console output).
- Logger name: This is usually the source class name (often abbreviated).
- The log message.

The default log configuration echoes messages to the console as they are written. By default, ERROR-level, WARN-level, and INFO-level messages are logged. You can also enable a “debug” mode by starting your application with a --debug flag.

- program arguemnts --debug
- debug=true

When the debug mode is enabled, a selection of core loggers (embedded container, Hibernate, and Spring Boot) are configured to output more information. Enabling the debug mode does not configure your application to log all messages with DEBUG level.

Alternatively, you can enable a “trace” mode by starting your application with a --trace flag (or trace=true in your application.properties). Doing so enables trace logging for a selection of core loggers (embedded container, Hibernate schema generation, and the whole Spring portfolio).

logging.file.name=runnerz.log

### Log Levels

All the supported logging systems can have the logger levels set in the Spring Environment (for example, in application.properties) by using logging.level.<logger-name>=<level> where level is one of TRACE, DEBUG, INFO, WARN, ERROR, FATAL, or OFF. The root logger can be configured by using logging.level.root.

```properties
logging.level.root=warn
logging.level.org.springframework.web=debug
logging.level.org.hibernate=error
```

```properties
logging.level.org.codemash.runnerz.Application=trace
```

```java
@SpringBootApplication
public class Application {

	private static final Logger log = LoggerFactory.getLogger(Application.class);

	public static void main(String[] args) {
		SpringApplication.run(Application.class, args);
		log.trace("TRACE log message.");
		log.debug("DEBUG log message.");
		log.info("INFO log message.");
		log.warn("WARN log message.");
		log.error("ERROR log message.");
	}
}
```

this is important - when we get to configuration and profiles
different levels for different environments


open up the console and show the logger name

changing the logging level at runtime

http://localhost:8080/actuator/loggers
http://localhost:8080/actuator/loggers/org.codemash.runnerz.Application

http :8080/actuator/loggers/org.codemash.runnerz.Application configuredLevel=TRACE

actuator
management.endpoints.web.exposure.include=*


```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <include resource="org/springframework/boot/logging/logback/base.xml"/>
    <logger name="org.codemash.controllers" level="WARN" additivity="false">
        <appender-ref ref="CONSOLE"/>
        <appender-ref ref="FILE"/>
    </logger>
</configuration>
```

## DevTools

- What are the Spring Boot DevTools? 
- How to enable automatic builds in IntelliJ