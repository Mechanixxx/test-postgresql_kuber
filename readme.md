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

***Задание со "звездочкой" попробовал реализовать через secret.yml и cronJob.***

**создаем файл ~/.pgpass и в него вносим такие данные:**

	*postgres:5432:postgresdb:postgresadmin:admin123 где postgres - имя сервиса, 5432 - номер порта, на котором он висит, далее - логин и пароль админа БД, которые указаны в pgconfigmap.yml *

	*Содержимое файла .pgpass зашифровано в формате base64 и в таком виде указано в secret.yml*  	
**Применяем настройки:**

	*kubectl create -f secret.yml*

	*kubectl create -f cron.yml*
***Теперь куб автоматически делает бэкап базы ежедневно в 2 AM***
