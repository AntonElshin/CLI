# очистка кэша view
php artisan view:clear

# создание/обновление структуры БД
php artisan migrate

# команда для выполнения php artisan db:seed только один раз
php artisan app:seed-once

# обновление проектной документации
php generate_project_doc.php

# выгрузка пунктов приёма из старой БД
php artisan legacy:generate-point-seeder

# форматирование PointSeeder после выгрузки
php -d memory_limit=-1 vendor/laravel/pint/builds/pint database/seeders/Core/PointSeeder.php