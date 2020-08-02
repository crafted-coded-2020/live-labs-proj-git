:beginner: **Spring Boot Introduction**  

`Why Spring Boot?`

1. create stand alone applications
2. production-grade applications that can easily run
3. provides opinionated starter dependencies that simplify build configuration
4. embed tomcat, jetty or Undertow
5. configures 3rd party libraries automatically (ex.hibernate)
6. no requirement for xml configuration

:beginner: **RESTful Web Services**  

- REpresentational State Transfer
- building web Services
- web services are the building blocks of Service Oriented Architecture (SOA)
- light weight, maintainable, scalable web services
- web servies are services on the web which can be consumed by any cleint application.
- ex : springboot (backend)can create the product restful services & angular or react (front) can consume these web servies.

`What are we building : RESTful Web Services`

:beginner: **Dependencies** 

Provides fast application restarts, LiveReload, and configurations for enhanced development experience.

```xml
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<scope>runtime</scope>
			<optional>true</optional>
		</dependency>
```


Build web, including RESTful, applications using Spring MVC. Uses Apache Tomcat as the default embedded container.

```xml
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
```

Persist data in SQL stores with Java Persistence API using Spring Data and Hibernate.

```xml
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
```