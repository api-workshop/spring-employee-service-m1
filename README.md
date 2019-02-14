# Session 1 - Hello World

## Goal

Create a barebone Spring Boot App and push it to Pivotal Platform.

## Create a Spring Boot App

1. Use [https://start.spring.io](https://start.spring.io)
to create a baseline project with some required dependencies:

* JPA
* Rest Repositories (data-rest)
* H2
* MySQL
* Lombok

(see image below)

![Local Image](/assets/spring-io.JPG)

2. Click on `Generate Project` to download the zip file
3. Copy the zip file to your workspace and unzip it

Or use this curl command to generate the project:

```
curl https://start.spring.io/starter.tgz \
-d dependencies=jpa,data-rest,h2,mysql,lombok \
-d language=java \
-d type=maven-project \
-d bootVersion=1.5.19.RELEASE \
-d groupId=com.example.api \
-d artifactId=employee \
-d baseDir=employee | tar -xzvf -
```

Note: In Windows, you may have to run the following,

```
curl https://start.spring.io/starter.tgz -d dependencies=jpa,data-rest,h2,mysql,lombok -d language=java -d type=maven-project -d bootVersion=1.5.19.RELEASE -d groupId=com.example.api -d artifactId=employee -d baseDir=employee | tar -xzvf -
```

Now you have a spring boot app that is ready to run:

```
cd employee
./mvnw spring-boot:run
```

**Note:** On Windows, use `mvnw.cmd` instead of `./mvnw`

It will startup with an embeded Tomcat Server on
[http://localhost:8080/](http://localhost:8080)

## Deploy to PCF

Package the app into a jar file
```
./mvnw clean package
```

Push that jar file to your space on PCF
```
cf push spring-employees -p target/employee-0.0.1-SNAPSHOT.jar --random-route
```

Get some information about the application you pushed
```
cf app spring-employees
```

You just pushed an app out to the world! (Hello world!)

## Add some Swagger to this app

[Java w/ Spring Data JPA](https://github.com/cts-workshop-02-2019/spring-employee-service-m2)
