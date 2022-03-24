# Spring Microservices in Action - Second Edition. Chapter 3

<br/>

###  Introduction

Code used on the 3rd Chapter of the Spring Microservices in Action - Second Edition Manning publication book. This code contains the Licensing Microservice.

<br/>

###  Initial Configuration

1.	Apache Maven (http://maven.apache.org)
2.	Git Client (http://git-scm.com)

<br/>

### How To Use

To clone and run this application, you'll need [Git](https://git-scm.com), [Maven](https://maven.apache.org/), [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html). From your command line:


```bash
# Clone this repository
$ git clone https://github.com/ihuaylupo/manning-smia

# Go into the repository
$ cd chapter3/licensing-service

# Install dependencies
$ mvn install

# Run the app
$ mvn spring-boot:run
or 
$ java -jar target/licensing-service-0.0.1-SNAPSHOT.jar
```

<br/>

```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8080/v1/organization/optimaGrowth/license/0235431845 \
    | jq
```

<br/>

**response:**

```
{
  "id": 716,
  "licenseId": "0235431845",
  "description": "Software product",
  "organizationId": "optimaGrowth",
  "productName": "Ostock",
  "licenseType": "full",
  "_links": {
    "self": {
      "href": "http://localhost:8080/v1/organization/optimaGrowth/license/0235431845"
    },
    "createLicense": {
      "href": "http://localhost:8080/v1/organization/optimaGrowth/license"
    },
    "updateLicense": {
      "href": "http://localhost:8080/v1/organization/optimaGrowth/license"
    },
    "deleteLicense": {
      "href": "http://localhost:8080/v1/organization/optimaGrowth/license/0235431845"
    }
  }
}

```

<br/>

```
// DELETE
$ curl \
    --header "Content-Type: application/json" \
    --request DELETE \
    --url http://localhost:8080/v1/organization/optimaGrowth/license/0235431845
```


<br/>

**response:**


```
Deleting license with id 0235431845 for the organization optimaGrowth
```


<br/>

```
// POST
$ curl \
    --data '{
      "licenseId":"0235431845",
      "organizationId":"Optima Growth",
      "description":"Software product",
      "descrproductNameiption":"Ostock",
      "licenseType":"complete"
    }' \
    --header "Content-Type: application/json" \
    --header "Accept-Language: es" \
    --request POST \
    --url http://localhost:8080/v1/organization/optimaGrowth/license
```

<br/>

**response:**


```
Licencia creada License(id=0, licenseId=0235431845, description=Software product, organizationId=optimaGrowth, productName=null, licenseType=complete)
```

<br/>


```
$ mvn clean package && java -jar target/licensing-service-0.0.1-SNAPSHOT.jar
```


<br/>

### Microservice's health

```
// GET
$ curl \
    --header "Content-Type: application/json" \
    --request GET \
    --url http://localhost:8080/actuator/health \
    | jq
```


<br/>

**response:**


```
{
  "status": "UP",
  "components": {
    "diskSpace": {
      "status": "UP",
      "details": {
        "total": 117610516480,
        "free": 7816773632,
        "threshold": 10485760
      }
    },
    "ping": {
      "status": "UP"
    }
  }
}
```

<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://javadev.org/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://javadev.ru/chat/">Телеграм чат</a>
