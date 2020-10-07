**1. Выполнить команду:**

	kubectl create -f pgconfigmap.yml (создаем карту конфигурации б/д)
**2. Выполнить команду:**

	kubectl create -f postgres-storage.yml (создаем хранилище)
**3 Выполнить команду:**

	kubectl create -f postgres-deployment.yml ( деплоим базу на контейнере из docker-hub)
**4. Выполнить команду:**

	kubectl create -f postgres-service.yml (создаем сервис для postgresql)
