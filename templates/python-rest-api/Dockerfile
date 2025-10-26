# Build stage
FROM python:3.12-slim AS build

WORKDIR /app

# Copy application code and tests
COPY app ./app
COPY tests ./tests

# Install dependencies
RUN pip install --no-cache-dir fastapi uvicorn pytest

# Run tests inside build stage
RUN pytest tests

# Runtime stage
FROM python:3.12-slim AS runtime
WORKDIR /app

# Copy only app code (not tests)
COPY --from=build /app/app ./app

# Expose port
EXPOSE 8080

# Start FastAPI
ENTRYPOINT ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8080"]
