Docker ArchivesSpace
====================

Run ArchivesSpace in Docker.

**Running**

```
# background mode
docker run --name build -d \
  -p 8080:8080 \
  -p 8081:8081 \
  -p 8089:8089 \
  -p 8090:8090 \
  markcooper/archivesspace

# foreground mode
docker run --name build -i -t \
  -p 8080:8080 \
  -p 8081:8081 \
  -p 8089:8089 \
  -p 8090:8090 \
  markcooper/archivesspace

# foreground mode and access container
docker run --name build -i -t \
  -p 8080:8080 \
  -p 8081:8081 \
  -p 8089:8089 \
  -p 8090:8090 \
  markcooper/archivesspace /bin/bash
```

**With MySQL**

```
# pull and run the official mysql docker image
docker run -d \
  -p 3306:3306 \
  --name mysql \
  -e MYSQL_ROOT_PASSWORD=123456 \
  -e MYSQL_DATABASE=archivesspace \
  -e MYSQL_USER=archivesspace \
  -e MYSQL_PASSWORD=archivesspace \
  mysql

# foreground mode
docker run --name build -i -t \
  -p 8080:8080 \
  -p 8081:8081 \
  -p 8089:8089 \
  -p 8090:8090 \
  -e ARCHIVESSPACE_DB_TYPE=mysql \
  --link mysql:db \
  markcooper/archivesspace
```

---