# beautydemy_php

#### read this and use add script when you lunch the lamp lightsail
https://aws.amazon.com/getting-started/hands-on/launch-lamp-web-app/
https://itectec.com/ubuntu/ubuntu-error-104528000-access-denied-for-user-rootlocalhost-using-password-no/

0. if you did not use add script in aws it will not work this step number0

easy steps to create the db on lightsail and how to create account

1. enter ```mysql``` to enter to the database
2. password can be found in bitnami_credentials in root dir
3. follow this awesome steps:
4. after this steps when we have password in the database for root to access it must be ```mysql -u root -p``` (password based login)


I solved in this way: I logged in with root username
```steps
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
```
