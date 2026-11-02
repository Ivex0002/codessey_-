FROM ubuntu:latest

ENV APP_NAME=mission1_miniproject_docker

WORKDIR /app

COPY app.sh /app/app.sh

RUN apt-get update && \
    apt-get install -y curl && \
    chmod +x /app/app.sh && \
    useradd -m appuser && \
    rm -rf /var/lib/apt/lists/*

USER appuser

HEALTHCHECK --interval=30s --timeout=3s \
  CMD echo "health check ok" || exit 1

CMD ["/app/app.sh"]
