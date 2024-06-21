# Stage 1: Build the application (can use any Java version)
FROM maven:alpine AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn package

# Stage 2: Copy the application to an image with Java 17
FROM adoptopenjdk/openjdk17:alpine-jre

# Copy only the JAR file from the builder stage
COPY builder:/app/target/*.jar app.jar

WORKDIR /opt/app
ENTRYPOINT ["java", "-jar", "app.jar"]
