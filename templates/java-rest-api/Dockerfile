# Build stage
FROM amazoncorretto:17 AS build
WORKDIR /app

# Install Maven
RUN yum install -y maven && yum clean all

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

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
