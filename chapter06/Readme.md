## Spring Microservices in Action - Second Edition. Chapter 6

# Introduction
Welcome to Spring Microservices in Action, Chapter 6.  Chapter 6 introduces the concept of service registration and discovery patterns using Spring Cloud and Netflix's Eureka server. Using service discovery, you will be able to add and remove service instances without the clients having to know the physical locations of the service. 

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system/ classpath or GitHub-based repository.
2. A Eureka server running as a Spring-Cloud based service. This service will allow multiple service instances to register with it. Clients that need to call a service will use Eureka to lookup the physical location of the target service.
3.  A organization service that will manage organization data used within Ostock.
4.  A licensing service that will manage licensing data used within Ostock.
5.  A Postgres SQL database used to hold the data.

## Initial Configuration
1.	Apache Maven (http://maven.apache.org)  All of the code examples in this book have been compiled with Java version 11.
2.	Git Client (http://git-scm.com)
3.  Docker(https://www.docker.com/products/docker-desktop)

**Important:** In this chapter we will be introducing a new service called Organization Service. You can donwload the organization and licensing service from the initial folder. That will contain all the source code required to start chapter 6.

## How To Use

To clone and run this application, you'll need [Git](https://git-scm.com), [Maven](https://maven.apache.org/), [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html). From your command line:

```bash
# Clone this repository
$ git clone https://github.com/ihuaylupo/manning-smia

# Go into the repository, by changing to the directory where you have downloaded the 
# chapter 6 source code and select whether you want the initial or final configuration
$ cd apps/chapter06

# To build the code examples for Chapter 6 as a docker image, open a command-line 
# window and execute the following command:
$ mvn clean package dockerfile:build

# Now we are going to use docker-compose to start the actual image.  To start the docker image, stay in the directory containing  your chapter 6 source code and  Run the following command: 
$ docker-compose -f docker/docker-compose.yml up
```

# The build command

Will execute the [Spotify dockerfile plugin](https://github.com/spotify/dockerfile-maven) defined in the pom.xml file.  

Running the above command at the root of the project directory will build all of the projects.  If everything builds successfully you should see a message indicating that the build was successful.

# The Run command

This command will run our services using the docker-compose.yml file located in the /docker directory. 

If everything starts correctly you should see a bunch of Spring Boot information fly by on standard out.  At this point all of the services needed for the chapter code examples will be running.

# Database
You can find the database script as well in the docker directory.



<br/>

```
// Started working after recreate
$ docker-compose -f docker/docker-compose.yml rm
$ docker-compose -f docker/docker-compose.yml up
```

<br/>


```
// CHECK configserver
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8071/licensing-service/dev \
    | jq
```

<br/>


```
$ docker-compose restart eurekaserver
$ docker-compose logs eurekaserver
```



<br/>


http://localhost:8070/


<br/>

![Application](/img/ch06-pic01.png?raw=true)



<br/>

http://localhost:8070/eureka/apps/

<br/>


```
// CHECK eureka
// GET
$ curl \
    --header "Content-Type: application/json" \
    --header "Accept: application/json" \
    --request GET \
    --url http://localhost:8070/eureka/apps/organization-service \
    | jq
```

<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
