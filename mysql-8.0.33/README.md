# MySQL Docker Compose

## Starting
Bring-up the MySQL container via:
```bash
docker-compose up -d
```

It'll create a MySQL database server:
Username: `root`
Password: `secret`
Host: `127.0.0.1:3316`

## Access
Access it via:
```bash
mysql --user=root --password=secret --host=127.0.0.1 --port=3316
```

Or use the client inside the container:
```
docker-compose exec mysql mysql --user=root --password=secret
```

## Hello World
Create a database with a table then add and retrieve a row.
```bash
mysql> CREATE DATABASE `social`;
Query OK, 1 row affected (0.04 sec)

mysql> USE `social`;
Database changed

mysql> CREATE TABLE `persons` (
    id int,
    name varchar(255),
    email varchar(255),
    PRIMARY KEY (id)
);
Query OK, 0 rows affected (0.19 sec)

mysql> INSERT INTO `persons` (id, name, email) VALUES (1, "Amirreza", "nasiri.amirreza.96@gmail.com");
Query OK, 1 row affected (0.04 sec)

mysql> SELECT * FROM `persons`;
+----+----------+------------------------------+
| id | name     | email                        |
+----+----------+------------------------------+
|  1 | Amirreza | nasiri.amirreza.96@gmail.com |
+----+----------+------------------------------+
1 row in set (0.00 sec)
```

## View Logs
See the MySQL server logs via:
```bash
docker-compose logs -f --tail 1000
```

## Sources
- https://hub.docker.com/_/mysql