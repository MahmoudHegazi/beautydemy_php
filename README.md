# beautydemy_php

0. if you did not use add script in aws it will not work this step number0

easy steps to create the db on lightsail and how to create account

1. enter ```mysql``` to enter to the database
2. password can be found in bitnami_credentials in root dir
3. follow this awesome steps:

I solved in this way: I logged in with root username

mysql -u root -p -h localhost
I created a new user with

CREATE USER 'francesco'@'localhost' IDENTIFIED BY 'some_pass';
then I created the database

CREATE DATABASE shop;
I granted privileges for new user for this database

GRANT ALL PRIVILEGES ON shop.* TO 'francesco'@'localhost';
Then I logged out root and logged in new user

quit;
mysql -u francesco -p -h localhost
I rebuilt my database using a script

source shop.sql;
And that's it.. Now from php works without problems with the call

 $conn = new mysqli("localhost", "francesco", "some_pass", "shop");
