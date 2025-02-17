# 🏗️ Stage 1: Build the JAR
FROM maven:3.8.8-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests  # Builds the JAR

# 🚀 Stage 2: Run the JAR
FROM openjdk:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/gestion-station-ski-1.0.jar /app/gestion-station-ski-1.0.jar
EXPOSE 8082
ENTRYPOINT ["java", "-jar", "/app/station-ski.jar"]
