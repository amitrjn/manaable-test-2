<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Project Setup Instructions

## Getting Started

1. Clone the repository:
```bash
git clone <repository-url>
cd project-directory
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

## Database Setup Instructions

### Default Credentials and Configuration
The project uses MySQL as the database. Here are the default credentials from the `.env` file:

```env
DB_CONNECTION=mysql
DB_HOST=<database-host>
DB_PORT=3306
DB_DATABASE=<your-database-name>
DB_USERNAME=<database-username>
DB_PASSWORD=<database-password>
```

Make sure to replace the placeholder values in your `.env` file with your actual database credentials.

### Commands to Run Migrations

After setting up the database configuration, run the following commands:

```bash
# Run all migrations
php artisan migrate

# Fresh migration (drops all tables and re-runs migrations)
php artisan migrate:fresh

# Run migrations with seed data (if available)
php artisan migrate --seed
```

## Other Notes

### Important Configuration Tips
1. **Storage Directory Permissions**:
   ```bash
   chmod -R 775 storage bootstrap/cache
   chown -R $USER:www-data storage bootstrap/cache
   ```

2. **Cache Configuration**:
   ```bash
   # Clear application cache
   php artisan cache:clear
   
   # Clear config cache
   php artisan config:clear
   
   # Regenerate optimized files
   php artisan optimize
   ```

3. **Development Server**:
   ```bash
   # Start the development server
   php artisan serve
   ```

### Docker Environment
If you're using Docker, please refer to our Docker setup documentation for container-specific instructions and commands.

### Troubleshooting
- Ensure all required PHP extensions are installed
- Verify database connection settings
- Check storage directory permissions
- Run `php artisan route:clear` if routes are not working
- Use `php artisan config:cache` after updating environment variables

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
