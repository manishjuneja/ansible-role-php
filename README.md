# Ansible Role: PHP

[![CI](https://github.com/manishjuneja/ansible-role-php/workflows/CI/badge.svg?event=push)](https://github.com/manishjuneja/ansible-role-php/actions?query=workflow%3ACI)

Installs PHP on RedHat/CentOS and Debian/Ubuntu servers.

## Requirements

If you're using an older LTS release of Ubuntu or RHEL, with an old/outdated version of PHP, you need to use a repo or PPA with a maintained PHP version, as this role only works with [PHP versions that are currently supported](http://php.net/supported-versions.php) by the PHP community.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    php_packages: []

A list of the PHP packages to install (OS-specific by default). You'll likely want to install common packages like `php`, `php-cli`, `php-devel` and `php-pdo`, and you can add in whatever other packages you'd like (for example, `php-gd` for image manipulation, or `php-ldap` if you need to connect to an LDAP server for authentication).

_Note: If you're using Debian/Ubuntu, you also need to install `libapache2-mod-fastcgi` (for cgi/PHP-FPM) or `libapache2-mod-php7.0` (or a similar package depending on PHP version) if you want to use `mod_php` with Apache._

    php_packages_extra: []

A list of extra PHP packages to install without overriding the default list.

    php_enable_webserver: true

If your usage of PHP is tied to a web server (e.g. Apache or Nginx), leave this default value. If you are using PHP server-side or to run some small application, set this value to `false` so this role doesn't attempt to interact with a web server.

    php_webserver_daemon: "httpd"

The default values for the HTTP server deamon are `httpd` (used by Apache) for RedHat/CentOS, or `apache2` (also used by Apache) for Debian/Ubuntu. If you are running another webserver (for example, `nginx`), change this value to the name of the daemon under which the webserver runs.

    php_default_version_debian: ""

(Debian/Ubuntu only) The default version of PHP in the given OS version repositories. The specific version is set per distro and per version, but you can override it by providing a value here, like `"7.4"`.

## License

MIT / BSD
