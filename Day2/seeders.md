# seeders

## Laravel Seeders
- Seeders are used to populate your database with sample data. They are particularly useful during development and testing.

## Basic Concepts
- Seeder: A class that contains methods to insert data into the database.
- Database Seeding: The process of running seeders to populate the database with initial data.

## Creating a Seeder
- To create a new seeder class, use the make:seeder command:
 ` php artisan make:seeder UsersTableSeeder`

- This command generates a new seeder file in the database/seeders directory. The filename will follow the format ClassNameSeeder.php.


## Defining Seed Data 
- Open the generated seeder file and add your data in the run method:
<?php

namespace Database\Seeders;

use Illuminate\Database\Seeder;
use Illuminate\Support\Facades\DB;

class UsersTableSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        DB::table('users')->insert([
            'name' => 'John Doe',
            'email' => 'john@example.com',
            'password' => bcrypt('password'),
        ]);
    }
}

- In this example, the run method inserts a new user into the users table.



## Running Seeders
- To run all seeders, use the db:seed command:

bash

`php artisan db:seed`
- This command executes all seeders defined in the DatabaseSeeder class.

# Running a Specific Seeder
- To run a specific seeder class, use the --class option:

bash

`php artisan db:seed --class=UsersTableSeeder`
- This command runs only the specified seeder class.

## DatabaseSeeder Class
- The DatabaseSeeder class, located in the database/seeders directory, is the main seeder class. It’s used to call other seeder classes:

php
Copy code
<?php

namespace Database\Seeders;

use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call([
            UsersTableSeeder::class,
            PostsTableSeeder::class,
        ]);
    }
}
- In this example, the run method calls the UsersTableSeeder and PostsTableSeeder classes to seed their respective tables.

## Rolling Back Seeders
If you need to revert changes made by seeders, you can manually delete or modify the data. Laravel doesn’t have a built-in command to roll back seeders like it does for migrations.

Common Commands
Create a Seeder
bash
`php artisan make:seeder SeederClassName`


## Run All Seeders
bash
`php artisan db:seed`
- Run a Specific Seeder
bash

`php artisan db:seed --class=SeederClassName`
- Refresh Migrations and Seeders
- To refresh migrations and seeders, you can use:

bash
`php artisan migrate:refresh --seed`
- This command rolls back and re-applies all migrations and then runs the seeders.

Example Seeder File
- Here’s a complete example of a seeder file:

php
Copy code
<?php

namespace Database\Seeders;

use Illuminate\Database\Seeder;
use Illuminate\Support\Facades\DB;
use Illuminate\Support\Facades\Hash;

class UsersTableSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        DB::table('users')->insert([
            [
                'name' => 'Alice',
                'email' => 'alice@example.com',
                'password' => Hash::make('password123'),
            ],
            [
                'name' => 'Bob',
                'email' => 'bob@example.com',
                'password' => Hash::make('password123'),
            ],
        ]);
    }
}
In this example, the UsersTableSeeder inserts two users into the users table with hashed passwords.