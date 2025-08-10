# Проверить, установлен ли maven. Узнать его версию
mvn --version

# Очистка target директории
mvn clean

# Очистка и компиляция проекта
mvn clean compile

# Очистка, компиляция, копирование проекта в локальный репозиторий .m2
mvn clean install

# Очистка, компиляция, копирование проекта в локальный репозиторий .m2, деплой проекта в удалённый репозиторий
mvn clean install

# Построить дерево зависимостей проекта
mvn dependency:tree -Dverbose

# Параметры для отключения ssl для работы через https для разных версий Maven
Maven less 3.6.3
-Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true

Maven 3.9.9
-Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.resolver.transport=wagon