
- migration 
- seeders 
- make : controller 
- artisan 

# Laravel Migrations
- Migrations are like version control for your database. They allow you to define the structure of your database tables and easily apply changes over time.

# Basic Concepts
- Migration: A file that contains the code to create or modify database tables.
- Schema Builder: A set of classes provided by Laravel to build and modify tables.


# Common Commands

## Creating a Migration
- To create a new migration file, use the make:migration command:
`php artisan make:migration create_users_table`

- This command will generate a new migration file in the database/migrations directory. The filename will include a timestamp for ordering.

## Running Migrations
- To apply all pending migrations to the database, use the migrate command:

`php artisan migrate`

- This command executes the up method in each migration file that has not been run yet, creating or modifying tables as defined.

## Rolling Back Migrations
- To revert the last batch of migrations, use the migrate:rollback command:
`php artisan migrate:rollback`
- This command executes the down method in the most recent batch of migrations, undoing the changes made by migrate.


## Rolling Back All Migrations
- To revert all migrations and return the database to its original state, use the migrate:reset command:

`php artisan migrate:reset`

- This command rolls back all migrations by executing the down method for each migration file.


## Refreshing Migrations
- To reset and then re-run all migrations, use the migrate:refresh command:
`php artisan migrate:refresh`

- This command first rolls back all migrations and then re-applies them, useful for resetting the database to a clean state.

## Migrating Specific Tables
- To run migrations for a specific table, you need to specify the migration file:
`php artisan migrate --path=/database/migrations/2024_09_01_create_users_table.php`
- Replace the path with the specific migration file you want to run.

## Checking Migration Status
- To check the status of all migrations (which have been run or not), use the migrate:status
`php artisan migrate:status `
- This command lists all migrations with their current status, indicating whether they have been applied or not.


## Migration File Structure
- Each migration file contains two primary methods:

1. up: Defines the changes to apply to the database (e.g., creating tables, adding columns).
2. down: Defines the changes to revert (e.g., dropping tables, removing columns).


<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class CreateUsersTable extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('users', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->string('email')->unique();
            $table->timestamp('email_verified_at')->nullable();
            $table->string('password');
            $table->rememberToken();
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('users');
    }
}
