## 1. What is Maven ?
- **Maven** is a **build automation and project management tool** for **Java-based projects**.  
- It helps in **building, testing, packaging, and deploying** applications.  
- It also manages **project dependencies** automatically.

### 🔹 2. Main Features
1. **Build Automation** – Compiles code, runs tests, and packages applications automatically.  
2. **Dependency Management** – Automatically downloads and manages required libraries (JARs).  
3. **Project Management** – Standardizes project structure and configuration.  
4. **Plugin Support** – Uses plugins to add extra build features (e.g., compile, deploy, test).  
5. **Integration** – Works well with IDEs (IntelliJ, Eclipse, VS Code) and CI/CD tools.

<br>

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




