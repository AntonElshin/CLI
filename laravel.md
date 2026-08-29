composer global require laravel/installer

# доступен интерпретатор php и laravel
php artisan tinker

php artisan up
php artisan down LogMiddleware

# сгенерировать ключ
php artisan key:generate

# перезагрузка секции autoload
php artisan dump

php artisan make:controller TestController
php artisan route:list
php artisan route:cache
php artisan route:clear

php artisan config:cache
php artisan config:clear

php artisan make:middleware

# Добавление докера к существующему проекту Laravel через Composer как dev-зависимости
composer require laravel/sail --dev
php artisan sail:install

# Создание нового проекта
laravel new example-app

# Для заполнения папки vendor для проекта, скачанного из гита
composer install

cd example-app
npm install && npm run build
composer run dev

php artisan migrate

php artisan migrate:rollback --step=3

php artisan migrate:reset

php artisan schedule:run
php artisan schedule:list

php composer.phar install

На локальной машине

php artisan migrate
php artisan db:seed
php artisan reviews:parse

На хостинге

/opt/php/8.4/bin/php composer.phar install

/opt/php/8.4/bin/php composer.phar update

/opt/php/8.4/bin/php artisan key:generate
/opt/php/8.4/bin/php artisan migrate
/opt/php/8.4/bin/php artisan db:seed
/opt/php/8.4/bin/php artisan reviews:parse
/opt/php/8.4/bin/php artisan schedule:run

/opt/php/8.4/bin/php artisan schedule:list

/opt/php/8.4/bin/php artisan config:clear
/opt/php/8.4/bin/php artisan cache:clear

/opt/php/8.4/bin/php artisan tinker



php artisan app:seed-once