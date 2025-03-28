
# STEPS

```bash

git clone https://github.com/rjfortis/devbox-wp

cd devbox-wp

devbox shell

devbox run init_start_services

curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar

chmod +x wp-cli.phar

php -d memory_limit=256M wp-cli.phar core download

mysql -u root -e "CREATE DATABASE wordpress_db;"

sed -i "/define( 'DB_HOST'/i\$mysql_unix_port = \"localhost:\" . getenv(\"MYSQL_UNIX_PORT\");" wp-config-sample.php

cp wp-config-sample.php wp-config.php

sed -i "s/define( 'DB_NAME', '.*' );/define( 'DB_NAME', 'wordpress_db' );/" wp-config.php

sed -i "s/define( 'DB_USER', '.*' );/define( 'DB_USER', 'root' );/" wp-config.php

sed -i "s/define( 'DB_PASSWORD', '.*' );/define( 'DB_PASSWORD', '' );/" wp-config.php

sed -i "s/define( 'DB_HOST', '.*' );/define( 'DB_HOST', \$mysql_unix_port );/" wp-config.php

rm -rf .git

```

## if you want setup a vitetheme

```bash

devbox run stop_services

git clone git@github.com:rjfortis/rfmtheme.git wp-content/themes/rfmtheme

devbox run npm_install

devbox run start_services

```
