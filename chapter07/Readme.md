# Spring Microservices in Action - Second Edition. Chapter 7

<br/>

### Introduction

Welcome to Spring Microservices in Action, Chapter 7.  Chapter 7 does not introduce any new services. Instead it focuses on how to use Spring Cloud and Resilience4j project to help protect service clients from failing or poorly behaving services. This chapter will introduce you to the concepts of fail-fast service calls, bulkheads and fallbacks for when a client call fails. 

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system/ classpath or GitHub-based repository.
2. A Eureka server running as a Spring-Cloud based service. This service will allow multiple service instances to register with it. Clients that need to call a service will use Eureka to lookup the physical location of the target service.
3.  A organization service that will manage organization data used within Ostock.
4.  A licensing service that will manage licensing data used within Ostock.
5.  A Postgres SQL database used to hold the data.



<br/>

### Not Worked for me on update licensingservice to work with JDK17

And working version:

```
<spring-cloud.version>Hoxton.SR1</spring-cloud.version>
<resilience4j.version>1.7.1</resilience4j.version>
```


<br/>

### How To Use


```
$ cd chapter07

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

**Same as in the previous chapter**


![Application](/img/ch06-pic01.png?raw=true)


<br/>


```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --header "Accept: application/json" \
    --request GET \
    --url http://localhost:8080/v1/organization/e6a625cc-718b-48c2-ac76-1dfdff9a531e/license/ \
    | jq
```

<br/>

**Result of failback code:**

```
[
  {
    "licenseId": "0000000-00-00000",
    "organizationId": "e6a625cc-718b-48c2-ac76-1dfdff9a531e",
    "productName": "Sorry no licensing information currently available",
    "links": []
  }
]
```



<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
