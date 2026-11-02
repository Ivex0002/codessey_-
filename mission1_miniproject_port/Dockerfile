FROM ubuntu:latest

WORKDIR /app

COPY index.html /app/index.html

RUN apt-get update && \
    apt-get install -y python3 && \
    rm -rf /var/lib/apt/lists/*

EXPOSE 8000

CMD ["python3", "-m", "http.server", "8000"]