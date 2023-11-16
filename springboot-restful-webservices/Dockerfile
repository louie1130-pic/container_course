FROM maven:3.8.2-eclipse-temurin-17 

WORKDIR /app

COPY . .

RUN mvn -f /app/pom.xml clean package -DskipTests

#

ENTRYPOINT ["java", "-jar", "springboot-restful-webservices.jar"]
