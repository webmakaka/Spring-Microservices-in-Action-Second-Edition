# Spring Microservices in Action - Second Edition. Chapter 6

<br/>

###  Introduction

Chapter 6 introduces the concept of service registration and discovery patterns using Spring Cloud and Netflix's Eureka server. Using service discovery, you will be able to add and remove service instances without the clients having to know the physical locations of the service. 

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system/ classpath or GitHub-based repository.
2. A Eureka server running as a Spring-Cloud based service. This service will allow multiple service instances to register with it. Clients that need to call a service will use Eureka to lookup the physical location of the target service.
3.  A organization service that will manage organization data used within Ostock.
4.  A licensing service that will manage licensing data used within Ostock.
5.  A Postgres SQL database used to hold the data.


<br/>

### How To Use


```bash
$ mvn clean package dockerfile:build
$ docker-compose -f docker/docker-compose.yml up
```


<br/>

```
// Started working after recreate
$ docker-compose -f docker/docker-compose.yml rm  -f
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
