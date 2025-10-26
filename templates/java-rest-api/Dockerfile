# Build stage
FROM amazoncorretto:17-alpine AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN ./mvnw clean package spring-boot:repackage

# Runtime stage
FROM amazoncorretto:17-alpine AS runtime
WORKDIR /app
COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]
