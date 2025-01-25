<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Project Setup Instructions

This repository includes a Laravel application that can be run either with Docker or traditional setup. Choose the setup method that best suits your needs.

## Docker Setup (Recommended)

### Prerequisites
- Docker
- Docker Compose

### Quick Start with Docker

1. Clone the repository:
```bash
git clone https://github.com/amitrjn/manaable-test-2.git
cd manaable-test-2
```

2. Copy the environment file:
```bash
cp .env.example .env
```

3. Configure your .env file with these database settings:
```
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=your_database
DB_USERNAME=your_username
DB_PASSWORD=your_secure_password
```

4. Build and start the Docker containers:
```bash
docker compose up -d --build
```

5. Install dependencies and set up Laravel:
```bash
docker compose exec app composer install
docker compose exec app php artisan key:generate
docker compose exec app php artisan migrate
```

6. Access the application at: http://localhost:8000

### Docker Services

- **PHP (8.2)**: PHP-FPM with Laravel extensions
- **MySQL (8.0)**: Database with persistent storage
- **Nginx**: Web server for Laravel

### Docker Commands

- Start containers: `docker compose up -d`
- Stop containers: `docker compose down`
- View logs: `docker compose logs`
- Run artisan commands: `docker compose exec app php artisan [command]`

## Traditional Setup

### Prerequisites
- PHP 8.2+
- Composer
- MySQL 8.0

### Quick Start (Without Docker)

1. Clone the repository:
```bash
git clone https://github.com/amitrjn/manaable-test-2.git
cd manaable-test-2
```

2. Install dependencies:
```bash
composer install
```

3. Set up environment file:
```bash
cp .env.example .env
php artisan key:generate
```

4. Configure your database in `.env`:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_database
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

5. Run migrations:
```bash
php artisan migrate
```

6. Start the development server:
```bash
php artisan serve
```

7. Access the application at: http://localhost:8000

## Database Management

### Migration Commands

```bash
# Run all migrations
php artisan migrate

# Fresh migration (drops all tables and re-runs migrations)
php artisan migrate:fresh

# Run migrations with seed data (if available)
php artisan migrate --seed
```

## Configuration and Maintenance

### Storage Permissions
```bash
chmod -R 775 storage bootstrap/cache
chown -R $USER:www-data storage bootstrap/cache
```

### Cache Management
```bash
# Clear application cache
php artisan cache:clear

# Clear config cache
php artisan config:clear

# Regenerate optimized files
php artisan optimize
```

## Troubleshooting

### Common Issues
- Ensure all required PHP extensions are installed
- Verify database connection settings
- Check storage directory permissions
- Run `php artisan route:clear` if routes are not working
- Use `php artisan config:cache` after updating environment variables

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
