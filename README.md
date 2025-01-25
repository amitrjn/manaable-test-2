<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Laravel Docker Development Environment

This repository includes a Docker-based development environment for Laravel 11.6.0. The setup includes PHP 8.2, MySQL 8.0, and Nginx, configured for optimal Laravel development.

## Prerequisites

- Docker Engine 24.0+
- Docker Compose v2.0+
- Git

## Features

- **PHP 8.2**: Configured with all required Laravel extensions
- **MySQL 8.0**: Persistent data storage
- **Nginx**: Optimized for Laravel applications
- **Docker Compose**: Orchestrates all services
- **Health Checks**: Ensures proper service startup order
- **Persistent Storage**: MySQL data persists between container restarts
- **Custom Network**: Isolated network for better security

## Quick Start

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

## Development Workflow

### Starting the Application
```bash
# Start all services in detached mode
docker compose up -d

# Watch the logs
docker compose logs -f
```

### Common Development Tasks
```bash
# Run migrations
docker compose exec app php artisan migrate

# Clear cache
docker compose exec app php artisan cache:clear

# Run tests
docker compose exec app php artisan test

# Install new dependencies
docker compose exec app composer require package-name
```

### Database Management
```bash
# Access MySQL CLI
docker compose exec db mysql -u laravel -p laravel

# Import database
docker compose exec -T db mysql -u laravel -p laravel < backup.sql

# Export database
docker compose exec db mysqldump -u laravel -p laravel > backup.sql
```

### Container Management
```bash
# Stop all containers
docker compose down

# Stop and remove volumes (warning: this will delete database data)
docker compose down -v

# Rebuild containers
docker compose up -d --build

# View container status
docker compose ps

# View logs for specific service
docker compose logs [service] # e.g., docker compose logs app
```

### Troubleshooting

1. **Permission Issues**
   ```bash
   # Fix storage permissions
   docker compose exec app chown -R www-data:www-data storage
   docker compose exec app chmod -R 775 storage
   ```

2. **Database Connection Issues**
   - Ensure MySQL container is healthy: `docker compose ps`
   - Check MySQL logs: `docker compose logs db`
   - Verify .env database credentials match docker-compose.yml

3. **Container Access**
   ```bash
   # Access PHP container
   docker compose exec app bash

   # Access MySQL container
   docker compose exec db bash

   # Access Nginx container
   docker compose exec nginx sh
   ```

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains thousands of video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the [Laravel Partners program](https://partners.laravel.com).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[WebReinvent](https://webreinvent.com/)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[DevSquad](https://devsquad.com/hire-laravel-developers)**
- **[Jump24](https://jump24.co.uk)**
- **[Redberry](https://redberry.international/laravel/)**
- **[Active Logic](https://activelogic.com)**
- **[byte5](https://byte5.de)**
- **[OP.GG](https://op.gg)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
