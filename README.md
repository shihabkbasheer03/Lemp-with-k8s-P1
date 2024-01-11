# Lemp-with-k8s-P1
1. Create some secrets for MySQL.

- Create a secret named mysql-root-pass wih key/value pairs as below:

`name: passwordvalue: R00t`

- Create a secret named mysql-user-pass with key/value pairs as below:

`name: usernamevalue: kodekloud_timname: passwordvalue: GyQkFRVNr3`

- Create a secret named mysql-db-url with key/value pairs as below:

`name: databasevalue: kodekloud_db3`

- Create a secret named mysql-host with key/value pairs as below:

`name: hostvalue: mysql-service`

2. Create a config map php-config for php.ini with variables_order = "EGPCS" data. 3. Create a deployment named lemp-wp.

4. Create two containers under it. First container must be nginx-php-container using image webdevops/php-nginx:alpine-3-php7 and second container must be mysql-container from image mysql:5.6. Mount php-config configmap in nginx container at /opt/docker/etc/php/php.ini location.

5) Add some environment variables for both containers:

- MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER, MYSQL_PASSWORD and MYSQL_HOST. Take their values from the secrets you created. Please make sure to use env field (do not use envFrom) to define the name-value pair of environment variables.

6) Create a node port type service lemp-service to expose the web application, nodePort must be 30008.

7) Create a service for mysql named mysql-service and its port must be 3306.

8. We already have a /tmp/index.php file on jump_host server.

- Copy this file into the nginx container under document root i.e /app and replace the dummy values for mysql related variables with the environment variables you have set for mysql related parameters. Please make sure you do not hard code the mysql related details in this file, you must use the environment variables to fetch those values.

- Once done, you must be able to access this website using Website button on the top bar, please note that you should see Connected successfully message while accessing this page.
