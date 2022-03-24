# Spring Microservices in Action - Second Edition. Chapter 1

<br/>

###  Introduction

Code used on the 1st Chapter of the Spring Microservices in Action - Second Edition Manning publication book. This code contains a basic Spring Boot application. 

<br/>

###  Initial Configuration

1.	Apache Maven (http://maven.apache.org)
2.	Git Client (http://git-scm.com)

<br/>

###  How To Use

To clone and run this application, you'll need [Git](https://git-scm.com), [Maven](https://maven.apache.org/), [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html). From your command line:

```bash
# Clone this repository
$ git clone https://github.com/ihuaylupo/manning-smia

# Go into the repository
$ cd chapter01/simple-application/

# Install dependencies
$ mvn install

# Run the app
$ mvn spring-boot:run
or 
$ java -jar target/SimpleApplication-0.0.1-SNAPSHOT.jar
```

<br/>

```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8080/hello/javadev?lastName=marley \
    | jq
```


<br/>

```
// POST
$ curl \
    --data '{
      "firstName":"javadev",
      "lastName":"marley"
    }' \
    --header "Content-Type: application/json" \
    --request POST \
    --url http://localhost:8080/hello \
    | jq
```

<br/>

**response:**

```
{
  "message": "Hello javadev marley"
}

```


<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
