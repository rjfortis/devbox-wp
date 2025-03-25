


1. git clone https://github.com/rjfortis/devbox-wp

2. cd devbox-wp

3. direnv allow

4. cd ..

5. cd devbox-wp

6. curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

7. chmod +x wp-cli.phar

8. wp-cli.phar core download

9. wp-cli.phar db create

10. sed -i "/define( 'DB_HOST'/i\$mysql_unix_port = \"localhost:\" . getenv(\"MYSQL_UNIX_PORT\");" wp-config-sample.php

11. wp config create --dbname=wordpress_db --dbuser=root --dbpass= --dbhost=$mysql_unix_port

