# Spring Microservices in Action - Second Edition. Chapter 4

<br/>

### Introduction

Code used on the 4th Chapter of the Spring Microservices in Action - Second Edition Manning publication book. This code contains the Licensing Microservice.

<br/>

### Initial Configuration

1.	Apache Maven (http://maven.apache.org)
2.	Git Client (http://git-scm.com)
3.  Docker(https://www.docker.com/products/docker-desktop)

<br/>

### How To Use

To clone and run this application, you'll need [Git](https://git-scm.com), [Maven](https://maven.apache.org/), [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html). From your command line:

```bash
# Clone this repository
$ git clone https://github.com/ihuaylupo/manning-smia

# Go into the repository
$ cd chapter04/licensing-service

# To build the code examples for Chapter 4 as a docker image, open a command-line 
# window and execute the following command:
$ mvn clean package dockerfile:build

# Run the app using the docker-compose up command. Remember, you need to execute
#the command on the root folder of the project where the docker-compose.yml is.
$ docker-compose up
```



<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
