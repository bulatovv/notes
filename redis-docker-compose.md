---
tags: docker, docker-compose, redis
---
# Запуск сервиса redis через docker-compose
```yml
services:
	redis:
		image: redis:alpine
		command: redis-server --appendonly yes --requirepass "${REDIS_PASSWORD}"
		volumes:
			- redis-data:/data
		restart: unless-stopped
volumes:
	redis-data:

netrowks:
	redis-conn:
		driver: bridge
```


`command: redis-server --appendonly yes --requirepass "${REDIS_PASSWORD}"`
+ `--appendonly yes` - включить [AOF](redis-persistence.md)
+ --requirepass - установить пароль для дефолтного пользователя *(см. [Redis Access List](redis-acl))*

*см. [параметры конфигурации redis](redis-config)*