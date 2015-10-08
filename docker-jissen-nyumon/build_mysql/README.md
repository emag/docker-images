# build_mysql

## Create shorturl_service database and the table

attach the mysql container and execute these commands.

``` sh
mysql -u root -e "GRANT ALL PRIVILEGES ON *.* TO 'nodeuser'@'localhost';"
mysql -u root -e "GRANT ALL PRIVILEGES ON *.* TO 'nodeuser'@'%' IDENTIFIED BY 'pas4mysql';"
mysql -u nodeuser -e "CREATE DATABASE shorturl_service;"
mysql shorturl_service -u nodeuser -e " \
CREATE TABLE url_list ( \
  hash CHAR(12) PRIMARY KEY, \
  url VARCHAR(256) UNIQUE NOT NULL COLLATE utf8_bin \
);"
```