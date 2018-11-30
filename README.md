# Session 1 - Hello World
    
## Create a Spring Boot App
    
Use [https://start.spring.io](https://start.spring.io) 
to create a baseline project with some required dependencies:

* JPA
* Rest Repositories (data-rest)
* H2
* MySQL

Or use this curl command to generate the project:

```
curl https://start.spring.io/starter.tgz \
-d dependencies=jpa,data-rest,h2,mysql \
-d language=java \
-d type=maven-project \
-d bootVersion=1.5.17.RELEASE \
-d groupId=com.example.api \
-d artifactId=employee \
-d baseDir=employee | tar -xzvf -
```

Note: In Windows, you may have to run the following,

```
curl https://start.spring.io/starter.tgz -d dependencies=jpa,data-rest,h2,mysql -d language=java -d type=maven-project -d bootVersion=1.5.17.RELEASE -d groupId=com.example.api -d artifactId=employee -d baseDir=employee | tar -xzvf -
```

Now you have a spring boot app that is ready to run:

```
cd employee
./mvnw spring-boot:run
```

It will startup with an embeded Tomcat Server on 
[http://localhost:8080/](http://localhost:8080)

## Deploy to PCF

Package the app into a jar file
```
./mvnw clean package
```

Push that jar file to your space on PCF
```
cf push spring-employee -p target/employee-0.0.1-SNAPSHOT.jar --random-route
```

Get some information about the application you pushed
```
cf app spring-employee
```

You just pushed an app out to the world! (Hello world!)

## Add some Swagger to this app

[Java w/ Spring Data JPA](https://github.com/cts-workshop-12-2018/spring-employee-service-m2)
