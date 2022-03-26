# Spring Microservices in Action - Second Edition. Chapter 8

<br/>

### Introduction

Chapter 8 introduces the concept of a API gateway. API gateways are using to enforce consistent policies and actions on all service calls. With this chapter we are going to introduce Spring Cloud Gateway.

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system/ classpath or GitHub-based repository.
2. A Eureka server running as a Spring-Cloud based service. This service will allow multiple service instances to register with it. Clients that need to call a service will use Eureka to lookup the physical location of the target service.
3. A API Gateway. All of our microservices can be routed through the gateway and have pre, response and post policies enforced on the calls.
4.  A organization service that will manage organization data used within Ostock.
5.  A licensing service that will manage licensing data used within Ostock.
6.  A Postgres SQL database used to hold the data.



<br/>

### How To Use

```
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

http://localhost:8080/auth


<br/>

![Application](/img/ch08-pic01.png?raw=true)


<br/>

```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8072/organization/v1/organization/e3f6a72b-7d6c-41da-ac12-fb30fcd1e547 \
    | jq
```

<br/>

**console output:**

<br/>

```
docker-gatewayserver-1        | 2022-03-25 01:54:37.333 DEBUG 1 --- [or-http-epoll-4] c.o.gateway.filters.TrackingFilter       : tmx-correlation-id generated in tracking filter: e8137332-2037-418a-9c5c-89af9d9ee12d.
docker-organizationservice-1  | Hibernate: select organizati0_.organization_id as organiza1_0_0_, organizati0_.contact_email as contact_2_0_0_, organizati0_.contact_name as contact_3_0_0_, organizati0_.contact_phone as contact_4_0_0_, organizati0_.name as name5_0_0_ from organizations organizati0_ where organizati0_.organization_id=?
docker-gatewayserver-1        | 2022-03-25 01:54:37.343 DEBUG 1 --- [or-http-epoll-4] c.o.gateway.filters.ResponseFilter       : Adding the correlation id to the outbound headers. e8137332-2037-418a-9c5c-89af9d9ee12d
docker-gatewayserver-1        | 2022-03-25 01:54:37.343 DEBUG 1 --- [or-http-epoll-4] c.o.gateway.filters.ResponseFilter       : Completing outgoing request for http://localhost:8072/v1/organization/e3f6a72b-7d6c-41da-ac12-fb30fcd1e547.
```


<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
