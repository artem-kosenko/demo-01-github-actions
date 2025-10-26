# =====================
# Build stage
# =====================
FROM python:3.12-slim AS build

WORKDIR /app

# Copy application code and tests
COPY app ./app
COPY tests ./tests
COPY requirements.txt .

# Install all dependencies including test dependencies
RUN pip install --no-cache-dir -r requirements.txt \
    && pip install --no-cache-dir pytest httpx

# Run tests
RUN pytest tests

# =====================
# Runtime stage
# =====================
FROM python:3.12-slim AS runtime

WORKDIR /app

# Copy app code
COPY app ./app

# Install only runtime dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Expose port and set entrypoint
EXPOSE 8000
ENTRYPOINT ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
