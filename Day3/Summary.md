# Maintenance mode :
- Maintenance mode is a feature in PHP that allows you to take your application offline for maintenance, without disrupting the user experience. It can be useful for tasks such as: Updating your database schema, Deploying a new feature, Bug fixes, and Routine maintenance tasks.


* Laravel : Use the php artisan down command to put your application into maintenance mode. You can also use the --fresh option to refresh the time remaining on the maintenance page.


- Maintenance mode is for preventing any users other than administrators from using the site while maintenance is taking place, though it's not designed to prevent user access during version upgrades.

# Faker_locale -

- In PHP, faker_locale is a configuration option that lets you set the locale for Faker, a library that generates fake data. You can add the faker_locale option to your config/app.php configuration file. 
 
- Faker can generate fake data for a variety of purposes, including: Bootstrapping a database, Creating XML documents, Stress testing persistence, and Anonymizing data from a production service. 
 
- Faker has built-in capabilities to generate fake data for things like people, addresses, phone numbers, companies, and more. It also has modifiers to customize the output, such as unique(), optional(), and valid(). 


# bcrypt_rounds=12

- In PHP, bcrypt round=12 means that the bcrypt hashing algorithm will use 12 rounds to create a password hash. This is an increase from the default of 10 rounds, and is often used to increase security as computing power increases.

- Bcrypt is a cryptographic hashing function that's used to create strong password storage systems. It's designed to be slow and adaptable to computing power, which makes it a good choice for hashing passwords. The longer it takes to hash a password, the harder it is for malicious users to generate "rainbow tables" of all possible string hash values. 

- You can increase the number of rounds in Laravel by changing the bcrypt.rounds value in the config/hashing.php file. You can also increase the number of rounds to 13 or more if you have lots of resources available or require a high level of security. 



# debug=true
- In PHP, debug=true in a .env file means that the application's debug mode is enabled. This is useful for local development because it shows errors. 
 
* Here's some more information about debug mode in PHP: 
 
* When to use debug mode
- Debug mode is best for local development, but should be turned off for production environments. 
 
# How to enable or disable debug mode
- To enable debug mode, set the APP_DEBUG environment variable to true in the .env file. To disable debug mode, set the APP_DEBUG environment variable to false

# session 

- Session in PHP is a way of temporarily storing and making data accessible across all the website pages. It will create a temporary file that stores various session variables and their values. This will be destroyed when you close the website.


# broadcast 
- Broadcasting in PHP is a feature that allows you to share data and event names between a server-side Laravel application and a client-side JavaScript application. It works by having clients connect to named channels on the frontend, and then the Laravel application broadcasts events to those channels on the backend. 
 

 # cache 
 