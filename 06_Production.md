# Production

The path to production is paved with decisions

- Executables
  - JAR 
  - WAR
- Containers
- Native Image

## Package 

The spring-boot-loader modules lets Spring Boot support executable jar and war files. If you use the Maven plugin or the Gradle plugin, executable jars are automatically generated, and you generally do not need to know the details of how they work.

https://docs.spring.io/spring-boot/docs/current/reference/html/executable-jar.html#appendix.executable-jar

```xml
  <parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>3.0.1</version>
    <relativePath/> <!-- lookup parent from repository -->
  </parent>
  <groupId>com.example</groupId>
  <artifactId>demo</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <packaging>war</packaging>
  <name>demo</name>
  <description>Demo project for Spring Boot</description>
  <properties>
    <java.version>17</java.version>
  </properties>
```

`mvn clean package`
`mvn clean package -DskipTests`

`java -jar target/runnerz-0.0.1-SNAPSHOT.jar`

https://docs.spring.io/spring-boot/docs/current/reference/html/executable-jar.html#appendix.executable-jar

## Containers

https://docs.spring.io/spring-boot/docs/current/reference/html/container-images.html#container-images

## Native Images

Spring Boot 3

https://docs.spring.io/spring-boot/docs/current/reference/html/native-image.html#native-image