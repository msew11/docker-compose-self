# mongo-sharding

## 启动容器

```
docker-compose up -d
```

## 初始化副本集

```
docker-compose exec config-0 sh -c "mongosh < /scripts/init-configserver.js"

docker-compose exec shard-0 sh -c "mongosh < /scripts/init-shard0.js"
docker-compose exec shard-1 sh -c "mongosh < /scripts/init-shard1.js"
```

## 初始化路由

```
docker-compose exec router-0 sh -c "mongosh < /scripts/init-router.js"
```

## 常用命令

```
docker-compose exec router-0 mongosh --port 27017
> sh.status()

# 指定数据库跑业务脚本
docker-compose exec router-0 sh -c "mongosh <db_name> < /scripts/<init_script>.js"
```
