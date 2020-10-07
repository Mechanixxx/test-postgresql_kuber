**1. Выполнить команду:**

	kubectl create -f pgconfigmap.yml (создаем карту конфигурации б/д)
**2. Выполнить команду:**

	kubectl create -f postgres-storage.yml (создаем хранилище)
**3 Выполнить команду:**

	kubectl create -f postgres-deployment.yml ( деплоим базу на контейнере из docker-hub)
**4. Выполнить команду:**

	kubectl create -f postgres-service.yml (создаем сервис для postgresql)

**Проверяем, какой порт слушает postgres:**
	
	kubectl get svc postgres
	
***У меня получилось так:*** 

	*postgres   NodePort   10.98.169.0   <none>        5432:30917/TCP   73m*
	
**Смотрим состояние pod-а:**

	kubectl get pods
***У меня получилось так:***

	*postgres-84ff4497db-2q4z9   1/1     Running   0          77m*
	
