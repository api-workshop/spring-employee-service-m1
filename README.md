# Session 1 - Hello World
    
## Create a Spring Boot App
    
Use [https://start.spring.io](https://start.spring.io) 
to create a baseline project with some required dependencies:

* JPA
* Actuator
* Lombok
* Rest Repositories (data-rest)
* H2
* MySQL

Or use this curl command to generate the project:

```
curl https://start.spring.io/starter.tgz \
-d dependencies=jpa,actuator,lombok,data-rest,h2,mysql \
-d language=java \
-d type=maven-project \
-d bootVersion=1.5.17.RELEASE \
-d groupId=com.example.api \
-d artifactId=employee \
-d baseDir=employee | tar -xzvf -
```

Now you have a spring boot app that is ready to run:

```
cd employee
./mvnw spring-boot:run
```

It will startup with an embeded Tomcat Server on 
[http://localhost:8080/](http://localhost:8080)

You have some additional endpoints available at this time as well:

[http://localhost:8080/actuator](http://localhost:8080/actuator)

[http://localhost:8080/health](http://localhost:8080/health)

## Deploy to PCF

Make sure you have the PCF CLI installed:
[https://docs.run.pivotal.io/cf-cli/install-go-cli.html](https://docs.run.pivotal.io/cf-cli/install-go-cli.html)

Verify you have a version greater than 6.37
```
cf --version
```

Instructions to login to the workshop PCF foundation:
```
cf login
```

Package the app into a jar file
```
./mvnw clean package
```

Push that jar file to your space on PCF
```
cf push employee -p target/employee-0.0.1-SNAPSHOT.jar --random-route
```

Get some information about the application you pushed
```
cf app employee
```

You just pushed an app out to the world! (Hello world!)