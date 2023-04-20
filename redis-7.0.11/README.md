# Redis Docker Compose

## Starting
Bring-up the Redis container via:
```bash
docker-compose up -d
```

It'll create a Redis server:
Password: `secret`
Host: `127.0.0.1:6389`

## Access
Access it via the info above from your host (Laptop) or use the client inside the container:
```
docker-compose exec redis -a secret
```

## Hello World
Create a `message` key with content of `Hello World.` and get the key afterward.
```bash
127.0.0.1:6379> set message "Hello World."
OK

127.0.0.1:6379> keys *
1) "message"

127.0.0.1:6379> get message
"Hello World."
```

## View Logs
See the Redis server logs via:
```bash
docker-compose logs -f --tail 1000
```

## Sources
- https://hub.docker.com/_/redis