FROM python:3.11-slim AS base

# Add curl for health check
RUN apt-get update && \
    apt-get install -y --no-install-recommends curl && \
    rm -rf /var/lib/apt/lists/*      
# rm -rf /var/lib/apt/lists/*   to cleanup apt cache to reduce image size

# Set the working dir
WORKDIR /app

# instll requirments
COPY requirements.txt ./requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

From base AS runner

EXPOSE 80

COPY . .

ENV FLASK_ENV=development
CMD ["python", "app.py"]
