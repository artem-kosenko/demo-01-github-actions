# Java REST API Example

Simple example Spring Boot REST API with CI/CD pipeline (GitHub Actions + Docker).

### 🚀 Endpoint

```
GET /health → {"status":"ok"}
```

### Local run
```
./mvnw spring-boot:run
```

### Docker
```
docker build -t demo:latest .
docker run -p 8080:8080 demo:latest
```

### CI/CD
- Build and test -> on each push/PR
- Docker push to the GHCR -> on push to main
