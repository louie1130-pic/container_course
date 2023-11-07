# Build stage
FROM maven:3.8.2-eclipse-temurin-17

WORKDIR /app

COPY . .

RUN mvn -f /app/pom.xml clean package -DskipTests

COPY target/springboot-restful-webservices-0.0.1-SNAPSHOT.jar /app/springboot-restful-webservices.jar

ENTRYPOINT ["java", "-jar", "springboot-restful-webservices.jar"]