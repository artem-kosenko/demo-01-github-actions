# Build stage
FROM maven:3.9.3-eclipse-temurin-17 AS build
WORKDIR /app

# Copy project files
COPY pom.xml .
COPY src ./src

# Build fat jar
RUN mvn -B clean package

# Runtime stage
FROM amazoncorretto:17 AS runtime
WORKDIR /app

# Copy fat jar from build stage
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
