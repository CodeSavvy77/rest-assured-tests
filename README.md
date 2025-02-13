# REST Assured API Testing Project

## Overview
This project uses **REST Assured** for automating API testing. It validates the responses, status codes, and data from RESTful web services.

## Prerequisites
Ensure you have the following installed:
- **Java** (JDK 8 or higher)
- **Gradle**
- **TestNG**
- **REST Assured** library

## Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/CodeSavvy77/rest-assured-tests.git
   ```
2. Navigate to the project folder:
   ```sh
   cd project-root
   ```
3. Build the project:
   ```sh
   gradle build
   ```

## Dependencies
Add the following dependencies in **build.gradle**:
```gradle
dependencies {
    testImplementation 'io.rest-assured:rest-assured:5.3.0'
    testImplementation 'org.testng:testng:7.8.0'
}
```

## Running Tests
To execute tests, run:
```sh
gradle test
```
Or for TestNG:
```sh
gradle test --tests testng.xml
```

## Sample Test Case
```java
import io.restassured.RestAssured;
import io.restassured.response.Response;
import org.testng.Assert;
import org.testng.annotations.Test;

import static io.restassured.RestAssured.*;

public class SampleTest {
    @Test
    public void testGetRequest() {
        RestAssured.baseURI = "https://jsonplaceholder.typicode.com";
        Response response = given()
            .when()
            .get("/posts/1")
            .then()
            .statusCode(200)
            .extract().response();
        
        Assert.assertEquals(response.jsonPath().getString("id"), "1");
    }
}
```

## Reports
- Test execution reports will be available in the `build/reports/tests/test` folder.
- You can integrate **Extent Reports** or **Allure Reports** for better visualization.
