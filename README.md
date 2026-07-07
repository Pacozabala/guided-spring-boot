# Guided Spring Boot Project

This repository is stores my progress on this Spring guide: [Building an Application with Spring Boot](https://spring.io/guides/gs/spring-boot).

## Commands

Run these commands from the `spring-boot/` directory unless noted otherwise.

- `./mvnw spring-boot:run`: Start the Spring Boot application locally on port `8080`. 
- `curl http://localhost:8080`: Call the running service and print the greeting response. 
- `./mvnw test`: Run the unit, integration, and Spring context tests. 
- `./mvnw package`: Compile the project, run tests, and build the application JAR. 

## Java Files and Notes
- `main/java/com/example/springboot/HelloController.java`: Web controller for simple web application, which returns a string greeting.
    - Class is flagged as a `@RestController`: ready for use by Spring MVC to handle web requests.
    - `@RestController` combines `@Controller` and `@ResponseBody`, which results in returning data rather than a view.
    - `@GetMapping` maps "/" to the `index()` method.
- `main/java/com/example/springboot/Application.java`: Class created by Initializr, sorting and printing all bean names in the command line during runtime.
    - `SpringBootApplication` combines the following:
        - `@Configuration`: tags class as source of bean def'ns for application context.
        - `@EnableAutoConfiguration`: tells Spring Boot to start adding beans based on classpath settings, other beans, property settings, etc.
        - `@ComponentScan`: tells Spring to look for other components, configs, services in the com/example package, letting it find controllers.
    - `main()` uses Spring Boot's `SpringApplication.run()` to launch an app.
    - `CommandLineRunner` method as `@Bean`, runs on startup, retrieves all beans created by the app. Prints the beans.
- `test/java/com/example/springboot/HelloControllerTest.java`: Calls `/` w/o starting a real server and verifies HTTP status and response body.
    - `MockMvc` comes from Spring Test, enables sending HTTP requests into the `DispatcherServlet` and make assertions about the result.
    - `@SpringBootTest`: asking whole app context to be created.
        - Alternatively, use `@WebMvcTest` to create only the web layers
- `test/java/com/example/springboot/HelloControllerIntegrationTest.java`: Full-stack integration test that starts the app on a random port (`webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT`). 
    - Verifies `/` endpoint through `RestTestClient`, where actual port is configured automatically.
- `test/java/com/example/springboot/ApplicationTests.java`: Spring Boot context-load test that verifies the application can start successfully in the test environment.
- Spring Boot provides management services (health, audits, beans) in the actuator module.