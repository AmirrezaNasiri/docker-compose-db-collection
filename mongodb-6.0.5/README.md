# MongoDB Docker Compose

## Starting
Bring-up the MongoDB container via:
```bash
docker-compose up -d
```

It'll create a MongoDB database server:
Username: `root`
Password: `secret`
Host: `127.0.0.1:27027`

## Access
Access it via the credentials above from your host (Laptop) or use the client inside the container:
```
docker-compose exec mongo mongosh -u root -p secret
```

## Hello World
Create a collection (database), insert a record and retrive a collection.
```bash
test> use my-app
switched to db my-app

my-app> db.products.insertOne({id:1, name:"LG G5"})
{
  acknowledged: true,
  insertedId: ObjectId("644107e27cc7abd80f4b49d1")
}

my-app> db.products.find()
[
  { _id: ObjectId("644107e27cc7abd80f4b49d1"), id: 1, name: 'LG G5' }
]
```

## View Logs
See the MongoDB server logs via:
```bash
docker-compose logs -f --tail 1000
```

## Sources
- https://hub.docker.com/_/mongo
- https://mkyong.com/mongodb/mongodb-hello-world-example/