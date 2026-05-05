# Lab 3 — Run Java Spring Boot App in a Container

## Objective
Containerize a Java Spring Boot application using Docker with Maven and Java 17.

## Project Structure
Lab3/
├── Dockerfile
├── pom.xml
├── src/
│   └── main/java/com/example/demo/
│       └── DemoApplication.java
└── README.md

## Steps

### 1. Clone the Application Code
```bash
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
```

### 2. Write the Dockerfile
```dockerfile
FROM maven:3.9.6-eclipse-temurin-17
WORKDIR /app
COPY . .
RUN mvn package -DskipTests
EXPOSE 8080
CMD ["java", "-jar", "target/demo-0.0.1-SNAPSHOT.jar"]
```

### 3. Build app1 Image
```bash
docker build -t app1 .
docker images | grep app1
```

### 4. Run container1
```bash
docker run -d --name container1 -p 8080:8080 app1
docker ps
```
![screenshots](screenshot-lab3-1.png)


### 5. Test the Application
```bash
curl http://localhost:8080
```

### 6. Stop and Delete the Container
```bash
docker stop container1
docker rm container1
docker ps -a
```

## Result
✅ Java Spring Boot app successfully containerized and running on port 8080.
