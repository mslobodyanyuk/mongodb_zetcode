MongoDB PHP tutorial
====================================================

* ***Actions on the deployment of the project:***

- Making a new project mongodb_zetcode.loc:
				
		sudo chmod -R 777 /var/www/LARAVEL/MongoDB/mongodb_zetcode.loc

		//!!!! .conf
		sudo cp /etc/apache2/sites-available/test.loc.conf /etc/apache2/sites-available/mongodb_zetcode.loc.conf
				
		sudo nano /etc/apache2/sites-available/mongodb_zetcode.loc.conf

		sudo a2ensite mongodb_zetcode.loc.conf

		sudo systemctl restart apache2

		sudo nano /etc/hosts
		
		cd /var/www/LARAVEL/MongoDB/mongodb_zetcode.loc
				
- Deploy project:

	`git clone << >>`
	
	_+ Сut the contents of the folder up one level and delete the empty one._

	`composer install`		
											
_- For install MongoDB and Compass follow the tutorial:_

Tech On Tech	

[MongoDB Compass Install In Ubuntu]( https://www.youtube.com/watch?v=No_DXalfy60&ab_channel=ProgrammingKnowledge )

MongoDB - 
<https://docs.mongodb.com/manual/installation/>

MongoDB Compass - 
<https://www.mongodb.com/try/download/compass>
									
---									
			
ZetCode
			
[MongoDB PHP tutorial]( http://zetcode.com/db/mongodbphp/ )

* ***Actions:***

	`sudo systemctl start mongod`

	`sudo systemctl status mongod`

- Creating a database 

	`mongo testdb`

- Fill in cars collection in testdb:

```
db.cars.insert({name: "Audi", price: 52642})
db.cars.insert({name: "Mercedes", price: 57127})
db.cars.insert({name: "Skoda", price: 9000})
db.cars.insert({name: "Volvo", price: 29000})
db.cars.insert({name: "Bentley", price: 350000})
db.cars.insert({name: "Citroen", price: 21000})
db.cars.insert({name: "Hummer", price: 41400})
db.cars.insert({name: "Volkswagen", price: 21600})
```	

- Installing PHP driver

	`composer require mongodb/mongodb`

_When installing the driver, you need to know the location of the `php.ini` file to enable the necessary extensions in it. You can view the paths to the location of files using the `phpinfo()` function. For example, call by specifying in `public/indeх.php` in an empty project folder OR in the `index()` method of the currently used controller:_

```php
<?php
	phpinfo();
```

OR

```php
public function index(){
	phpinfo();
...	
```

	- To enable extensions, verify that they are enabled in your .ini files:
		- /etc/php/7.2/cli/php.ini

<https://www.php.net/manual/en/mongodb.installation.manual.php>

	php -i | grep extension_dir
		
		extension_dir => /usr/lib/php/20170718 => /usr/lib/php/20170718

	sudo nano /etc/php/7.2/cli/php.ini
		
		extension="/usr/lib/php/20170718/mongodb.so"

	sudo nano /etc/php/7.2/apache2/php.ini
	
		extension="/usr/lib/php/20170718/mongodb.so"
		
	sudo systemctl restart apache2		

- Database statistics

Used classes in `dbstats.php`:

```php
MongoDB\Driver\Manager
MongoDB\Driver\Command
MongoDB\Driver\Cursor
MongoDB\Driver\Exception\Exception
```

![screenshot of sample]( https://github.com/mslobodyanyuk/mongodb_zetcode/blob/master/public/images/1.png )

- Listing databases

Used classes in `list_databases.php`:

```php
MongoDB\Driver\Manager
MongoDB\Driver\Command
MongoDB\Driver\Exception\Exception
```

_Added `." <br/>"` to display a newline in the browser in the echo-construct._

![screenshot of sample]( https://github.com/mslobodyanyuk/mongodb_zetcode/blob/master/public/images/2.png )

- Reading data

Used classes in `read_all.php`:

```php
MongoDB\Driver\Manager
MongoDB\Driver\Query
MongoDB\Driver\Exception\Exception
```

![screenshot of sample]( https://github.com/mslobodyanyuk/mongodb_zetcode/blob/master/public/images/3.png )

- Filtering data

Used classes in `filtering.php`:

```php
MongoDB\Driver\Manager
MongoDB\Driver\Query
MongoDB\Driver\Exception\Exception
```

![screenshot of sample]( https://github.com/mslobodyanyuk/mongodb_zetcode/blob/master/public/images/4.png )

- Projections

Used classes in `projection.php`:

```php
MongoDB\Driver\Manager
MongoDB\Driver\Query
MongoDB\Driver\Exception\Exception
```

![screenshot of sample]( https://github.com/mslobodyanyuk/mongodb_zetcode/blob/master/public/images/5.png )

                ...

- Limiting data output

Used classes in `read_limit.php`:

```php
MongoDB\Driver\Manager
MongoDB\Driver\Query
MongoDB\Driver\Exception\Exception
```

![screenshot of sample]( https://github.com/mslobodyanyuk/mongodb_zetcode/blob/master/public/images/6.png )

- Bulk write

Used classes in `bulkwrite.php`:

```php
MongoDB\Driver\Manager
MongoDB\Driver\BulkWrite
MongoDB\BSON\ObjectID
MongoDB\Driver\Exception\Exception
```

![screenshot of sample]( https://github.com/mslobodyanyuk/mongodb_zetcode/blob/master/public/images/7.png )

####useful links:

ZetCode
			
[MongoDB PHP tutorial]( http://zetcode.com/db/mongodbphp/ )

Tech On Tech	

[MongoDB Compass Install In Ubuntu]( https://www.youtube.com/watch?v=No_DXalfy60&ab_channel=TechOnTech )

Download Compass 

<https://www.mongodb.com/try/download/compass>

MongoDB Compatibility

<https://docs.mongodb.com/drivers/php#compatibility>

PHP manual

<https://www.php.net/manual/en/mongodb.installation.manual.php>

[MongoDB driver]( https://www.php.net/manual/en/set.mongodb.php )

[MongoDB Driver Classes]( https://www.php.net/manual/ru/book.mongodb.php )

<https://www.php.net/manual/en/class.mongodb-driver-manager.php>