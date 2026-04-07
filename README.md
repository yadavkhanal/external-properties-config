**External Properties Configuration**

**This repository serves as a supplementary project to:  
**[**https://github.com/yadavkhanal/gateway_and_configserver**](https://github.com/yadavkhanal/gateway_and_configserver)

**It demonstrates how externalized properties stored in a repository can be dynamically fetched by a Spring Cloud Config Server at runtime using GitHub Actions.**

**This is a Spring Boot-based project that showcases how to externalize application configuration using property files and environment variables. This approach enables flexible, environment-specific configuration without requiring changes to application code.**

**🚀 Overview**

**This project demonstrates how to:**

- **Externalize configuration from the application**
- **Use environment variables and external .properties files**
- **Override default application configurations**
- **Follow best practices aligned with the 12-Factor App methodology**

**Benefits of Externalized Configuration**

- **Improved portability across environments (dev, QA, prod)**
- **Enhanced security (no hardcoded secrets)**
- **Better maintainability**

**⚙️ Configuration Strategy**

**Spring Boot supports loading configuration from multiple sources:**

- **application.yml (default)**
- **External .properties files**
- **Environment variables**
- **Command-line arguments**

**External configuration overrides internal configuration when properly defined.**

**🔄 Configuration Priority**

**Spring Boot resolves properties in the following order (highest priority first):**

- **Command-line arguments**
- **External configuration files**
- **Environment variables**
- **Internal application.properties or application.yml**

**💡 Example Usage**

**@Value("\${app.name}")  
private String appName;  
<br/>@RestController  
public class AppController {  
<br/>@GetMapping("/name")  
public String getAppName() {  
return appName;  
}  
}**

**🌍 Environment Variables**

**You can override properties using environment variables:**

**export APP_NAME=EnvApp**

**Spring Boot automatically maps:**

**APP_NAME → app.name**

**🐳 Docker Usage (Optional)**

**version: '3'  
services:  
app:  
image: external-properties-config  
environment:  
\- APP_NAME=DockerApp  
volumes:  
\- ./external-config:/config  
command: >  
java -jar app.jar  
\--spring.config.location=file:/config/application-external.properties**

**✅ Best Practices**

- **Do NOT store secrets in source code**
- **Use environment variables for sensitive data**
- **Use external files for environment-specific configurations**
- **Keep default values in application.yml (or .properties)**
- **Use profiles (application-dev.properties, etc.) when needed**

**📚 Key Concepts**

- **Externalized Configuration**
- **Spring Environment Abstraction**
- **Property Sources Hierarchy**
- **12-Factor App (Configuration)**

**🛠️ Tech Stack**

- **Java**
- **Spring Boot**
- **Maven**
- **Docker (optional)**