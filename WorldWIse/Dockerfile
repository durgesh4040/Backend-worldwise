# Build stage
FROM maven:3.8.7-openjdk-17-slim AS build

WORKDIR /app

# Copy pom.xml and source code
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn -f pom.xml clean package

# Package stage
FROM openjdk:17-jdk-alpine AS final

WORKDIR /app

# Copy the JAR from the build stage
COPY --from=build /app/target/WorldWIse-0.0.1-SNAPSHOT.jar /app/app.jar

# Expose the application port
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "/app/app.jar"]
