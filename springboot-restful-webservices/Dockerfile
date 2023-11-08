# Package stage
FROM maven:3.8.2-eclipse-temurin-17 AS build

WORKDIR /app

COPY . .

RUN mvn -f /app/pom.xml clean package -DskipTests

# Build stage
FROM eclipse-temurin:17-jre-alpine

WORKDIR /usr/local/lib

COPY --from=build /app/target/springboot-restful-webservices-0.0.1-SNAPSHOT.jar springboot-restful-webservices.jar

#COPY target/springboot-restful-webservices-0.0.1-SNAPSHOT.jar /app/springboot-restful-webservices.jar

ENTRYPOINT ["java", "-jar", "springboot-restful-webservices.jar"]