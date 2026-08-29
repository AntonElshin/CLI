docker compose up

### Запустить docker compose c игнорированием override и билдом, только по docker-compose.yml
docker compose -f docker-compose.yml up -d --build

### Запустить docker compose c override и билдом, только по docker-compose.yml
docker compose --project-name flowerfantasy up -d --build

docker compose up -d --build

### Запустить docker compose с билдом без использования кэша
docker compose build --no-cache

docker compose up -d --build

docker-compose build laravel      # пересобрать образ
docker-compose up -d laravel     # перезапустить контейнер с новым образом

docker-compose build nextjs      # пересобрать образ
docker-compose up -d nextjs     # перезапустить контейнер с новым образом

docker-compose build scheduler
docker-compose up -d scheduler   # если есть scheduler

### Показать созданные разделы
docker volume ls

### Удалить неиспользуемые разделы
docker volume prune

### Удалить контейнер
docker rm -f frontend

### Вывести активные процессы
docker ps

### Залогиниться в GitHub Docker Registry
docker login ghcr.io
https://github.com/AntonElshin?tab=packages

# Вывести список сетей
docker network ls

# gateway
docker compose --project-name gateway up -d

# flowerfantasy

### Создать сеть
docker network create flowerfantasy_network

### Удалить раздел
docker volume rm flowerfantasy_mysql_data
docker volume rm flowerfantasy_laravel_storage
docker volume rm flowerfantasy_uploads

### Создать раздел
docker volume create flowerfantasy_mysql_data
docker volume create flowerfantasy_laravel_storage
docker volume create flowerfantasy_uploads

### Собрать и запушить образ flowerfantasy-service:latest
docker build -t ghcr.io/antonelshin/flowerfantasy-service:latest -f docker/Dockerfile .
docker push ghcr.io/antonelshin/flowerfantasy-service:latest

### Собрать образ flowerfantasy-ui:latest
docker build -t ghcr.io/antonelshin/flowerfantasy-ui:latest -f docker/Dockerfile .
docker push ghcr.io/antonelshin/flowerfantasy-ui:latest

# Поднимаем сервисы
docker compose --project-name flowerfantasy up -d

# vmig

### Создать сеть
docker network create vmig_network

docker network create scraptraffic_network

### Удалить раздел
docker volume rm vmig_postgres_data
docker volume rm vmig_laravel_storage
docker volume rm vmig_uploads

docker volume rm scraptraffic_mysql_data

### Создать раздел
docker volume create vmig_postgres_data
docker volume create vmig_laravel_storage
docker volume create vmig_uploads

docker volume create scraptraffic_mysql_data

### Собрать и запушить образ vmig-service:latest
docker build -t ghcr.io/antonelshin/vmig-service:latest -f docker/Dockerfile .
docker push ghcr.io/antonelshin/vmig-service:latest

# Поднимаем сервисы
docker compose --project-name vmig up -d

# Получаем образы из GHCR
docker compose pull

# Создание самоподписанных сертификатов через Git Bash
перейти в папку nginx/certs

# 1. Создать приватный ключ
openssl genrsa -out local_flowerfantasy.key 2048

# 2. Создать самоподписанный сертификат на основе ключа
openssl req -x509 -days 365 -key local_flowerfantasy.key -out local_flowerfantasy.crt -subj "//CN=flowerfantasy.local"


openssl genrsa -out local_vmig.key 2048
openssl req -x509 -days 365 -key local_vmig.key -out local_vmig.crt -subj "//CN=vmig.local"

### Создание топиков
docker ps

docker container ps

docker exec -it fd1a39db769f kafka-topics --create --topic smec_themes_administration.out --bootstrap-server localhost:9093 --replication-factor 1 --partitions 1

docker exec -it fd1a39db769f kafka-topics --create --topic smec_call_history.top_themes.out --bootstrap-server localhost:9093 --replication-factor 1 --partitions 1

docker exec -it fd1a39db769f kafka-topics --create --topic SMEC.SMEC-CALL-HISTORY.IN --bootstrap-server localhost:9093 --replication-factor 1 --partitions 1

docker exec -it fd1a39db769f kafka-topics --create --topic SMEC.SMEC-CALL-HISTORY.OUT --bootstrap-server localhost:9093 --replication-factor 1 --partitions 1


docker exec -it fd1a39db769f kafka-topics --create --topic cti_web.request.out --bootstrap-server localhost:9093 --replication-factor 1 --partitions 3

docker exec -it fd1a39db769f kafka-topics --create --topic cti_web.responce.in --bootstrap-server localhost:9093 --replication-factor 1 --partitions 3

docker exec -it fd1a39db769f kafka-topics --create --topic cti_ng.event.out --bootstrap-server localhost:9093 --replication-factor 1 --partitions 3

docker exec -it fd1a39db769f kafka-topics --create --topic cti_web.event.in.out --bootstrap-server localhost:9093 --replication-factor 1 --partitions 3


docker exec -it fd1a39db769f kafka-consumer-groups --bootstrap-server localhost:9093 --describe --group fscc.themes-service.themes-administration_group

docker exec -it fd1a39db769f kafka-consumer-groups --bootstrap-server localhost:9092 --list

docker exec -it fd1a39db769f kafka-consumer-groups --bootstrap-server localhost:9092 --group fscc.themes-service.themes-administration_group-2 --describe | grep smec_themes_administration.out


