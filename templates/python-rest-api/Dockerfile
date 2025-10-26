FROM python:3.12-slim AS build
WORKDIR /app

# install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# copy app and tests
COPY app ./app
COPY tests ./tests

# set PYTHONPATH so 'from app.main import app' works
ENV PYTHONPATH=/app

# run tests
RUN pytest tests

# ---- Runtime stage ----
FROM python:3.12-slim AS runtime
WORKDIR /app

COPY --from=build /app/app ./app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
