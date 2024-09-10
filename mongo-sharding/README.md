# mongo-sharding

## 启动容器

```
docker-compose up -d --build
```

## 初始化副本集

```
docker-compose exec config-0 sh -c "mongosh < /scripts/init-configserver.js"

docker-compose exec shard-rs0-0 sh -c "mongosh < /scripts/init-shard0.js"
docker-compose exec shard-rs1-0 sh -c "mongosh < /scripts/init-shard1.js"
```

## 初始化路由

```
docker-compose exec router-0 sh -c "mongosh < /scripts/init-router.js"
```

## 设置认证

```
docker-compose exec config-0 sh -c "mongosh admin < /scripts/auth.js"

docker-compose exec shard-rs0-0 sh -c "mongosh admin < /scripts/auth.js"
docker-compose exec shard-rs1-0 sh -c "mongosh admin < /scripts/auth.js"

docker-compose exec router-0 mongosh --port 27017 -u "admin" --authenticationDatabase admin
```

## 连接

```
docker exec -it router-0 mongosh --port 27017
docker-compose exec router-0 mongosh --port 27017
```

## 常用命令

```
# 查看数据库
show dbs

sh.status()
```
