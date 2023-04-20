# PostgreSQL Docker Compose

## Starting
Bring-up the PostgreSQL container via:
```bash
docker-compose up -d
```

It'll create a PostgreSQL database server:
Username: `postgres`
Password: `secret`
Host: `127.0.0.1:5442`

## Access
Access it via:

Access it via the info above from your host (Laptop) or use the client inside the container:
```
docker-compose exec -it -e PGPASS=secret postgres psql -U postgres
```

## Hello World
Create a database with a table then add and retrieve a row.
```bash
postgres=# CREATE DATABASE `social`;

postgres=# USE `social`;

postgres=# CREATE TABLE persons (
    id int,
    name varchar(255),
    email varchar(255),
    PRIMARY KEY (id)
);
CREATE TABLE

postgres=# INSERT INTO persons (id, name, email) VALUES (1, 'Amirreza', 'nasiri.amirreza.96@gmail.com');
INSERT 0 1

postgres=# SELECT * FROM persons;
 id |   name   |            email             
----+----------+------------------------------
  1 | Amirreza | nasiri.amirreza.96@gmail.com
(1 row)
```

## View Logs
See the Postgres server logs via:
```bash
docker-compose logs -f --tail 1000
```

## Sources
- https://hub.docker.com/_/postgres