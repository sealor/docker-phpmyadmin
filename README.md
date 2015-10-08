# phpMyAdmin Docker container

This container serves phpMyAdmin based on the lightweight web server "Nginx". In comparison to [nazarpc/phpmyadmin](https://hub.docker.com/r/nazarpc/phpmyadmin/), this container consumes less disk space.

**How to use with MySQL container:**
```
docker run --name mysql -e MYSQL_ROOT_PASSWORD=password -d mysql
docker run --rm --link mysql:mysql -p 1234:80 sealor/phpmyadmin
```
---

**How to use with MariaDB container:**
```
docker run --name mariadb -e MYSQL_ROOT_PASSWORD=password -d mariadb
docker run --rm --link mariadb:mysql -p 1234:80 sealor/phpmyadmin
```
---

**How to use with local MySQL server on host (should be similar for MariaDB):**
```
sudo sed -i 's/^bind-address/#bind-address/' /etc/mysql/my.cnf
sudo mysql -u root -p -e "GRANT ALL PRIVILEGES ON *.* TO 'root'@'172.17.%' IDENTIFIED BY 'password';"
sudo service mysql restart

docker run --rm --add-host mysql:172.17.42.1 -p 1234:80 sealor/phpmyadmin
```
---

**GitHub repository:**
https://github.com/sealor/docker-phpmyadmin
