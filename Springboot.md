## 1 🌱 Spring vs Spring Boot

### 🔹 1. What is Spring?
- **Spring** is a **Java-based framework** for building **enterprise-level applications**.  
- Provides features like:
  - **Inversion of Control (IoC) / Dependency Injection**
  - **Aspect-Oriented Programming (AOP)**
  - **Transaction management**
  - **MVC framework for web applications**
- Helps in building modular, maintainable, and testable applications.  
- Requires **manual configuration** (XML or Java-based) for most things.

### 🔹 2. What is Spring Boot?
- **Spring Boot** is a **framework built on top of Spring** to simplify Spring application development.  
- Focuses on **auto-configuration** and **convention over configuration**.  
- Key features:
  - **Embedded server** (Tomcat, Jetty, etc.) — no need to deploy WAR files.  
  - **Starter dependencies** — one dependency brings everything needed for a feature.  
  - **Minimal configuration** — reduces boilerplate code.  
  - **Production-ready features** — metrics, health checks, logging.

### 🔹 3. Difference Between Spring and Spring Boot

| Feature | Spring | Spring Boot |
|---------|--------|------------|
| **Configuration** | Manual configuration needed (XML/Java) | Auto-configuration by default |
| **Setup** | Requires lots of setup and boilerplate code | Quick setup with Spring Initializr |
| **Server** | Needs external server (WAR deployment) | Embedded server included (runs as JAR) |
| **Dependencies** | Add dependencies manually | Starter POMs simplify dependency management |
| **Complexity** | More flexible, but complex for beginners | Less flexible, but simpler and faster for development |
| **Use Case** | Enterprise applications needing custom setup | Microservices, REST APIs, or quick Spring apps |

### 🔹 4. Summary
- **Spring** = Powerful, flexible Java framework (requires manual setup).  
- **Spring Boot** = Opinionated framework to **simplify Spring development**, reduce configuration, and make projects production-ready quickly.

---

## 2. 🌱What is Maven ?
### 🔹 1. Definition
- **Maven** is a **build automation and project management tool** for **Java-based projects**.  
- It helps in **building, testing, packaging, and deploying** applications.  
- It also manages **project dependencies** automatically.
  

### 🔹 2. Main Features
1. **Build Automation** – Compiles code, runs tests, and packages applications automatically.  
2. **Dependency Management** – Automatically downloads and manages required libraries (JARs).  
3. **Project Management** – Standardizes project structure and configuration.  
4. **Plugin Support** – Uses plugins to add extra build features (e.g., compile, deploy, test).  
5. **Integration** – Works well with IDEs (IntelliJ, Eclipse, VS Code) and CI/CD tools.


### 🔹 3. Key File — `pom.xml` (Project Object Model)
- The heart of every Maven project.  
- Contains all project details and configurations.

### It defines:
1. **Project info** – name, version, description, etc.  
2. **Dependencies** – external libraries the project needs.  
3. **Build plugins** – extra tools for building/testing.  
4. **Project structure** – how code and resources are organized.

### Example:
```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter</artifactId>
        </dependency>
    </dependencies>
</project>
```

### 🔹 4. Dependency Management
- You don’t need to manually download .jar files.
- Just declare dependencies in pom.xml.
- Maven automatically downloads them from Maven Central Repository.
- It also manages transitive dependencies (dependencies of your dependencies).
```
<dependency>
    <groupId>org.mongodb</groupId>
    <artifactId>mongodb-driver-sync</artifactId>
    <version>4.11.0</version>
</dependency>
```

### 🔹 5. Common Maven Commands

| Command               | Description                                           |
| --------------------- | ----------------------------------------------------- |
| `mvn clean`           | Deletes previously compiled files (target folder).    |
| `mvn compile`         | Compiles the source code.                             |
| `mvn test`            | Runs unit tests.                                      |
| `mvn package`         | Packages code into a `.jar` or `.war` file.           |
| `mvn install`         | Installs the package into the local Maven repository. |
| `mvn spring-boot:run` | Runs a Spring Boot application.                       |

### 🔹 6. Maven Project Structure
```
my-project/
 ├── src/
 │   ├── main/
 │   │   ├── java/        → Source code
 │   │   └── resources/   → Config files (application.properties)
 │   └── test/            → Test code
 ├── target/              → Compiled output (created after build)
 └── pom.xml              → Maven configuration file
```

### 🔹 7. Why Use Maven
- ✅ Easy dependency management
- ✅ Standard project layout
- ✅ Automated build process
- ✅ Integration with popular IDEs
- ✅ Easy to use in CI/CD pipelines
- ✅ Reduces manual setup and errors

## 🌱 What is Maven Wrapper (mvnw)
The Maven Wrapper allows you to run Maven commands **without installing Maven globally**.
It ensures that everyone uses the **same Maven version** for your project.

---
## 3. 🌱Spring Boot Project Structure
When you create a Spring Boot project (using Spring Initializr or manually with Maven/Gradle), it follows a standard directory structure defined by Maven conventions.
```
my-springboot-project/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/demo/
│   │   │       ├── DemoApplication.java
│   │   │       ├── controller/
│   │   │       ├── service/
│   │   │       └── repository/
│   │   └── resources/
│   │       ├── application.properties
│   │       ├── static/
│   │       ├── templates/
│   │       └── banner.txt
│   └── test/
│       └── java/
│           └── com/example/demo/
│               └── DemoApplicationTests.java
├── pom.xml
└── README.md
```
### 📘 Folder and File Explanation
### 1. src/main/java/
- Contains **all Java source code** for your application.
- Organized by **package structure**, usually starting with your base package (e.g., `com.example.demo`).

**Common Sub-packages:**
| Folder              | Purpose                                                                   |
| ------------------- | ------------------------------------------------------------------------- |
| `controller`        | Contains REST controllers (`@RestController`) that handle HTTP requests.  |
| `service`           | Business logic layer (`@Service`).                                        |
| `repository`        | Data access layer (`@Repository`), usually interfaces for JPA or MongoDB. |
| `model` or `entity` | Classes that represent database tables or data models.                    |
| `config`            | Configuration files or custom beans (`@Configuration`).                   |

### 2. src/main/resources/
Contains **non-code resources** like:
| File/Folder                                   | Purpose                                                          |
| --------------------------------------------- | ---------------------------------------------------------------- |
| `application.properties` or `application.yml` | Main configuration file (DB, ports, profiles, etc.)              |
| `static/`                                     | Stores static files like CSS, JS, images (served automatically). |
| `templates/`                                  | For HTML templates (used with Thymeleaf or Freemarker).          |

### 3. src/test/java/
- Contains unit tests and integration tests.
- By default, includes a test file named DemoApplicationTests.java.
- Uses frameworks like JUnit and Mockito for testing.

### 4. pom.xml
The `pom.xml` is the **Maven configuration file**.
It defines:
- **Project dependencies** (like Spring Boot, JPA, etc.)  
- **Plugins** (like `  spring-boot-maven-plugin`)  
- **Build information and project metadata**

```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

### 5. DemoApplication.java
The **main entry point** of the Spring Boot app.
Contains the `@SpringBootApplication` annotation which:
- Enables component scanning
- Enables auto-configuration
- Marks it as a Spring Boot app
```
@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

### 6. target/
- Created after you build the project using Maven (`mvn package`).
- Contains compiled `.class` files, JAR/WAR files, and other build artifacts.

### 🧩 Typical Flow
- A request hits a `Controller` (@RestController).
- The Controller calls a `Service` for business logic.
- The Service interacts with a `Repository` to fetch or save data.
- The Repository talks to the `Database` via JPA, JDBC, or Mongo.
- Data flows back to the Controller → Response to the client.

---

## 4. Structure of pom.xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             https://maven.apache.org/xsd/maven-4.0.0.xsd">

    
    <!-- POM model version -->
    <modelVersion>4.0.0</modelVersion>

    
    <!-- Parent POM: Inherits Spring Boot defaults, plugin configs, and dependency management -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.7.18</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

    
    <!-- Project coordinates -->
    <groupId>com.example</groupId>          <!-- Organization/package -->
    <artifactId>myFirstProject</artifactId> <!-- Project/module name -->
    <version>0.0.1-SNAPSHOT</version>       <!-- Version (SNAPSHOT = in development) -->
    <name>myFirstProject</name>             <!-- Display name -->
    <description>First project for Spring Boot</description> <!-- Short description -->
    <url/>                                  <!-- Project website (optional) -->

    
    <!-- Optional metadata -->
    <licenses>
        <license/>                          <!-- License info (optional) -->
    </licenses>
    
    <developers>
        <developer/>                        <!-- Developers info (optional) -->
    </developers>
    
    <scm>
        <connection/>                        <!-- Source control connection info -->
        <developerConnection/>
        <tag/>
        <url/>
    </scm>

    
    <!-- Project-level properties -->
    <properties>
        <java.version>8</java.version>      <!-- Java version used for compilation -->
    </properties>

    
    <!-- Project dependencies -->
    <dependencies>
        <!-- Spring Boot Web Starter: for building REST APIs and web apps -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- Spring Boot Test Starter: for unit/integration testing -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope> <!-- Only used during testing -->
        </dependency>
    </dependencies>

    
    <!-- Build configuration -->
    <build>
        <plugins>
            <!-- Spring Boot Maven Plugin: allows running and packaging Spring Boot apps -->
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>

---

## 🧩 IoC (Inversion of Control)
**Definition**
- **IoC (Inversion of Control)** is a **design principle** where the control of object creation, configuration, and lifecycle is **transferred from the developer to the Spring container.**
- In simple terms:
  - You don’t create objects manually using new; the framework does it for you.

**🎯 Main Objective**
- To reduce tight coupling between components.
- To increase flexibility, testability, and maintainability.
- To centralize object management inside a container.

**⚙️ How IoC Works**

- Define Beans
  - Using annotations (@Component, @Service, @Repository, @Bean)
  - Or XML configuration.
- Spring Container (IoC container) reads those definitions.
- The container creates, initializes, and injects dependencies automatically.
- You access objects using the ApplicationContext.

**🧭 In Short**
- 🧠 IoC = Concept
- ⚙️ Implemented via ApplicationContext
- 💉 Achieved through Dependency Injection (DI)

- List of annotations for classes managed by the Spring IoC container
@Controller
@RestController
@Service
@Repository
@Component
@Configuration
@Bean

---

## 6.🌱 @SpringBootApplication

- Definition:
It is a **convenience annotation** that combines three commonly used Spring annotations:
```
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan
```
So, using @SpringBootApplication saves you from declaring all three separately.

**Main Purpose**
- Marks the main class of a Spring Boot application.
- Helps Spring Boot auto-configure the application based on dependencies.
- Enables component scanning to detect beans, controllers, and configurations automatically.

### Internally Includes
**@SpringBootConfiguration**
- It’s a specialized version of @Configuration.
- Allows you to define beans using @Bean methods.
  
**@EnableAutoConfiguration**
- Tells Spring Boot to automatically configure the application
- based on dependencies in the classpath.
Example: If spring-boot-starter-web is present, it configures Tomcat, MVC, etc.

**@ComponentScan**
- Scans the package (and its subpackages) of the class where it is declared.
- Automatically detects components annotated with:
`@Component`
`@Service`
`@Repository`
`@Controller`

---

##  🧩 7.@Transactional

**What is @Transactional**
- `@Transactional` is used in Spring Boot to manage **database transactions** automatically.
- Ensures a set of operations execute as one unit —
  -either **all succeed** or **all rollback** (atomicity).

**⚙️ Default Rollback Behavior**
| Exception Type  | Example                                                                | Rollback by Default? |
| --------------- | ---------------------------------------------------------------------- | -------------------- |
| ✅ **Unchecked** | `RuntimeException`, `NullPointerException`, `IllegalArgumentException` | ✔️ Yes               |
| ❌ **Checked**   | `Exception`, `IOException`, `SQLException`                             | ❌ No                 |

**🧠 Why rollbackFor is Needed**
- By default, Spring only rolls back for unchecked exceptions.
- If a method throws a checked or custom exception,
  Spring commits the transaction unless told otherwise.

✅ To fix this, specify:
```
@Transactional(rollbackFor = MyCustomException.class)
```

**⚡ What Happens Internally**

When you annotate a method with @Transactional:

1. Spring creates a **proxy** for that method.
2. Before executing, it **starts a transaction**.
3. Executes your database code.
4. If everything passes → **commit**.
5. If any RuntimeException occurs → **rollback**.













