### 1. What is Maven ?
- **Maven** is a **build automation and project management tool** for **Java-based projects**.  
- It helps in **building, testing, packaging, and deploying** applications.  
- It also manages **project dependencies** automatically.

---

## 🔹 2. Main Features
1. **Build Automation** – Compiles code, runs tests, and packages applications automatically.  
2. **Dependency Management** – Automatically downloads and manages required libraries (JARs).  
3. **Project Management** – Standardizes project structure and configuration.  
4. **Plugin Support** – Uses plugins to add extra build features (e.g., compile, deploy, test).  
5. **Integration** – Works well with IDEs (IntelliJ, Eclipse, VS Code) and CI/CD tools.

---

## 🔹 3. Key File — `pom.xml` (Project Object Model)
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
