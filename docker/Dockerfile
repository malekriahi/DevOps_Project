# Use Maven and OpenJDK 17 as the base image
FROM maven:3.9.6-eclipse-temurin-17 AS build

# Set working directory inside the container
WORKDIR /app

# Copy the Maven project files
COPY pom.xml .
COPY src ./src

# Build the project
RUN mvn clean package -DskipTests

# Use OpenJDK 17 as the runtime image
FROM openjdk:17-jdk-alpine

# Set working directory for runtime
WORKDIR /app

# Copy the built JAR from the build stage
COPY --from=build /app/target/station-ski.jar /app/station-ski.jar

# Expose the application port
EXPOSE 8082

# Run the application
ENTRYPOINT ["java", "-jar", "/app/station-ski.jar"]
