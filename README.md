# laravel-spatie-permission-tutorial

## Installation
### Install via Composer
```bash
composer require spatie/laravel-permission
```
### Optional: The service provider will automatically get registered. Or you may manually add the service provider in your config/app.php file
```bash
'providers' => [
    // ...
    Spatie\Permission\PermissionServiceProvider::class,
];
```
### You should publish the migration and the config/permission.php config file with:
```bash
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
```
it will create config and database migration

### Run migration
```bash
php artisan migrate
```

## Basic setup
### First, add the Spatie\Permission\Traits\HasRoles trait to your User model(s):
```php
use Illuminate\Foundation\Auth\User as Authenticatable;
use Spatie\Permission\Traits\HasRoles;

class User extends Authenticatable
{
    use HasRoles;

    // ...
}
```
### Create role & permission
```php
use Spatie\Permission\Models\Role;
use Spatie\Permission\Models\Permission;

$role = Role::create(['name' => 'writer']);
$permission = Permission::create(['name' => 'edit articles']);
```

### Direct permission
- give direct permission to user
- remove permission from user
- give multiple permissions
- check user has permissions

### Permission via role
- assign role to user
- remove role from user
- sync roles
- check user has role
- give permission to role
- remove permission from role
- check role has permission

### Check authorization
- via middleware
- via controller middleware
- via Gate
- via authorize
- via blade
