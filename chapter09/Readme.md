# Spring Microservices in Action - Second Edition. Chapter 9

<br/>

### Introduction

Chapter 9 demonstrates how to build security with your services using Spring Cloud Security and KeyCloak.  In this chapter we build an Authentication and authorization server using KeyCloak. 

1. A KeyCloak Authentication and Authorization server.
2. A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system or GitHub-based repository.
3. A Eureka server running as a Spring-Cloud based service. This service will allow multiple service instances to register with it. Clients that need to call a service will use Eureka to lookup the physical location of the target service.
4. A API Gateway. All of our microservices can be routed through the gateway and have pre, response and post policies enforced on the calls.
5. A organization service that will manage organization data used within Ostock.
6. A licensing service that will manage licensing data used within Ostock.
7. A Postgres SQL database used to hold the data.



<br/>

### How To Use

To clone and run this application, you'll need [Git](https://git-scm.com), [Maven](https://maven.apache.org/), [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html). From your command line:

```bash
$ mvn clean package dockerfile:build
$ docker-compose -f docker/docker-compose.yml up
```

<br/>

```
// Restart
$ docker-compose -f docker/docker-compose.yml rm -f
$ docker-compose -f docker/docker-compose.yml up
```

<br/>

```
$ docker-compose -f docker/docker-compose.yml logs 
```

<br/>

http://localhost:8070/

<br/>

```
localhost:8080/auth/

admin/admin
```


<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
