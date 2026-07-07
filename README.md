# Guided Spring Boot Project

This repository is stores my progress on this Spring guide: [Building an Application with Spring Boot](https://spring.io/guides/gs/spring-boot).

## Commands

Run these commands from the `spring-boot/` directory unless noted otherwise.

| Command | Purpose |
| --- | --- |
| `cd spring-boot` | Move into the Maven project directory from the repository root. |
| `./mvnw spring-boot:run` | Start the Spring Boot application locally on port `8080`. |
| `curl http://localhost:8080` | Call the running service and print the greeting response. |
| `./mvnw test` | Run the unit, integration, and Spring context tests. |
| `./mvnw package` | Compile the project, run tests, and build the application JAR. |

## Java files

| File | Description |
| --- | --- |
| `spring-boot/src/main/java/com/example/springboot/Application.java` | Main Spring Boot entry point. It starts the application and defines a `CommandLineRunner` bean that prints the Spring bean names at startup. |
| `spring-boot/src/main/java/com/example/springboot/HelloController.java` | REST controller for the `/` route. It returns the greeting text used by the tutorial and tests. |
| `spring-boot/src/test/java/com/example/springboot/ApplicationTests.java` | Basic Spring Boot context-load test that verifies the application can start successfully in the test environment. |
| `spring-boot/src/test/java/com/example/springboot/HelloControllerTest.java` | MockMvc-based test that calls `/` without starting a real server and verifies the HTTP status and response body. |
| `spring-boot/src/test/java/com/example/springboot/HelloControllerIntegrationTest.java` | Integration test that starts the application on a random port and verifies the `/` endpoint through `RestTestClient`. |
