<https://disk.yandex.ru/d/j-wms6WfZgtc9Q>

Dockerfile:

```
FROM python:3.11-slim

COPY /main /main

CMD ["python", "main/main.py"]
```
docker-compose.yml:
```
services:
  redis:
    image: redis
    ports:
        - "6379:6379"
    volumes:
      - /Users/hillow/VSCProjects/Testing/redis_config:/usr/local/etc/redis
  main:
    image: 'example-docker'
    env_file:
      - .env
    volumes:
      - /Users/hillow/VSCProjects/Testing/data:/data
    depends_on:
      - redis

```
