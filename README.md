# Dowpe

Docker WordPress Environment

## Softwate Included
- nginx (https://hub.docker.com/_/nginx/)
- MariaDB (https://hub.docker.com/_/mariadb/)
- Dowpe - PHP (https://github.com/Nismit/dowpe-php)
  - Composer (https://getcomposer.org/)
  - WP-CLI (http://wp-cli.org/)

## Usage
If you have already installed `docker-compose`, you just need only 3 steps to run WordPress!

```
git clone 
cd dowpe
docker-compose up
```

After spin up all containers, you can access to http://localhost:8080

### How to stop/remove

```
// stop
ctrl + c

// remove container
docker-compose down
```

## Config
In `docker-compose.yml`, you might need to change some variables.
[Dowpe - PHP](https://github.com/Nismit/dowpe-php) is needed some environment variables to boot.

### Dowpe - PHP Config

| Variables     | Default       |
| ------------- | ------------- |
| WP_VERSION    | latest        |
| WP_LOCALE     | en_US         |
| WP_THEME      | wp-multibyte-patch duplicate-post  |
| WP_URL        | localhost\:8080  |
| WP_TITLE      | Dowpe-WordPress  |
| WP_ADMIN      | admin  |
| WP_PASSWORD   | password  |
| WP_EMAIL      | example@example.com  |

**Mixed with MySQL(Mariadb) Variables**

| Variables                         | Example Value       |
| -------------                     | ------------- |
| MYSQL_ROOT_PASSWORD               | password        |
| MYSQL_HOST                        | mysql         |
| MYSQL_DATABASE                    | wordpress  |
| MYSQL_USER                        | dowpe_user  |
| MYSQL_PASSWORD                    | dowpe_password  |
| MYSQL_PREFIX (use in dowpe php)   | _wp01  |

Mariadb image is supported `Docker Secrets` for `MYSQL_ROOT_PASSWORD, MYSQL_ROOT_HOST, MYSQL_DATABASE, MYSQL_USER, and MYSQL_PASSWORD` (https://hub.docker.com/_/mariadb/)

### nginx Config
It has been already set up nginx config, but if you want to chage some settings, it's available to customize.

**Friendly Reminder**

You should check `config/default.conf` at 29 lines because fast cgi pass must same as `php container name` in `docker-compose.yml`.