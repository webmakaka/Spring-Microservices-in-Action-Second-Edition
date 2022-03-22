## Spring Microservices in Action - Second Edition. Chapter 5

# Introduction
Welcome to Spring Microservices in Action, Chapter 5.  Chapter 5 introduces the Spring Cloud Config service and how you can use it managed the configuration of your microservices.  By the time you are done reading this chapter you will have built and/or deployed:

1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system/ classpath or GitHub-based repository.
2.  A licensing service that will manage licensing data used within Ostock.
3.  A Postgres SQL database used to hold the data.

## Initial Configuration
1.	Apache Maven (http://maven.apache.org)  All of the code examples in this book have been compiled with Java version 11.
2.	Git Client (http://git-scm.com)
3.  Docker(https://www.docker.com/products/docker-desktop)

## How To Use

To clone and run this application, you'll need [Git](https://git-scm.com), [Maven](https://maven.apache.org/), [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html). From your command line:

```bash
# Clone this repository
$ git clone https://github.com/ihuaylupo/manning-smia

# Go into the repository, by chaning to the directory where you have downloaded the 
# chapter 5 source code
$ cd chapter05

# The build command

Will execute the [Spotify dockerfile plugin](https://github.com/spotify/dockerfile-maven) defined in the pom.xml file.  

This is the first chapter we will have multiple Spring projects that need to be be built and compiled.  Running the above command at the root of the project directory will build all of the projects.  If everything builds successfully you should see a message indicating that the build was successful.

# The Run command

This command will run our services using the docker-compose.yml file located in the /docker directory. 

If everything starts correctly you should see a bunch of Spring Boot information fly by on standard out.  At this point all of the services needed for the chapter code examples will be running.

# Database
You can find the database script as well in the docker directory.
```

<br/>

### Run configserver local 

```
$ cd configserver
$ mvn spring-boot:run
```

<br/>


```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8071/licensing-service/dev \
    | jq
```


<br/>


http://0.0.0.0:8200/ui/vault/auth


<br/>

### As a docker image

```
// To build the code examples for Chapter 5 as a docker image, open a command-line 
// window and execute the following command:
$ mvn clean package dockerfile:build
```

<br/>

```
// Now we are going to use docker-compose to start the actual image.  To start the docker image, stay in the directory containing  your chapter 5 source code and  Run the following command: 
$ docker-compose -f docker/docker-compose.yml up
```

<br/>

```
// Start working after recreate
$ docker-compose -f docker/docker-compose.yml rm
$ docker-compose -f docker/docker-compose.yml up
```

<br/>


```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8071/licensing-service/default \
    | jq
```


<br/>


```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8071/licensing-service/prod \
    | jq
```

<br/>


```
{
  "name": "licensing-service",
  "profiles": [
    "prod"
  ],
  "label": null,
  "version": null,
  "state": null,
  "propertySources": [
    {
      "name": "classpath:/config/licensing-service-prod.properties",
      "source": {
        "example.property": "I AM PROD",
        "spring.datasource.url": "jdbc:postgresql://database:5432/ostock_prod",
        "spring.datasource.username": "postgres",
        "spring.datasource.password": "postgres"
      }
    },
    {
      "name": "classpath:/config/licensing-service.properties",
      "source": {
        "example.property": "I AM THE DEFAULT",
        "spring.jpa.hibernate.ddl-auto": "none",
        "spring.jpa.database": "POSTGRESQL",
        "spring.datasource.platform": "postgres",
        "spring.jpa.show-sql": "true",
        "spring.jpa.hibernate.naming-strategy": "org.hibernate.cfg.ImprovedNamingStrategy",
        "spring.jpa.properties.hibernate.dialect": "org.hibernate.dialect.PostgreSQLDialect",
        "spring.database.driverClassName": "org.postgresql.Driver",
        "spring.datasource.testWhileIdle": "true",
        "spring.datasource.validationQuery": "SELECT 1",
        "management.endpoints.web.exposure.include": "*",
        "management.endpoints.enabled-by-default": "true"
      }
    }
  ]
}
```


<br/>


```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8080/actuator/env \
    | jq
```

<br/>

```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8071/actuator/env \
    | jq
```

<br/>

### Vault

<br/>

```
$ docker run -d -p 8200:8200 --name vault -e 'VAULT_DEV_ROOT_TOKEN_ID=myroot' -e 'VAULT_DEV_LISTEN_ADDRESS=0.0.0.0:8200' vault
```

<br/>


```
http://0.0.0.0:8200/ui/vault/auth

token: myroot
```

<br/>

Check the book how to create and set vault

<br/>

```
$ curl -X "GET" "http://localhost:8071/licensing-service/default" -H "X-Config-Token: myroot"
```

<br/>

### Protecting sensitive configuration information

<br/>

```
// ENCRYPT
// POST
$ curl \
    --data postgres \
    --header "Content-Type: text/plain" \
    --request POST \
    --url http://localhost:8071/encrypt
```

<br/>

```
// DECRYPT
// POST
$ curl \
    --data d3c6fc76de9d78d0e36156f5f101c16e41daed579969659b8fe25ccddd241e2c \
    --request POST \
    --header "Content-Type: text/plain" \
    --url http://localhost:8071/decrypt
```

<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
