# Build stage
FROM eclipse-temurin:17-jdk AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN ./mvnw clean package spring-boot:repackage

# Runtime stage
FROM gcr.io/distroless/java17
WORKDIR /app
COPY --from=build /app/target/demo-0.1.0-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]
