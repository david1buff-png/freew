# Base Alpine
FROM alpine:3.22

# Install dependencies
RUN apk add --no-cache bash wget unzip ca-certificates \
    && update-ca-certificates

# Create app directory
WORKDIR /app

# Download latest v2ray-core
RUN wget -O v2ray.zip https://github.com/v2fly/v2ray-core/releases/latest/download/v2ray-linux-64.zip \
    && unzip v2ray.zip -d /app \
    && rm v2ray.zip

# Copy config
COPY config.json /app/config.json

# Expose WebSocket port
EXPOSE 8080

# Run v2ray
ENTRYPOINT ["./v2ray", "run", "-c", "/app/config.json"]
