# scraptraffic

### Создать сеть
docker network create scraptraffic_network

### Удалить раздел
docker volume rm scraptraffic_mysql_data

### Создать раздел
docker volume create scraptraffic_mysql_data

# Поднимаем сервисы
docker compose --project-name scraptraffic -f docker-compose.yml -f docker-compose.override.yml up -d