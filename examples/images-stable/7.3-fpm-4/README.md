PHP 7.3 Nginx Image Stable Example
===========

This example exists primarily to test the following documentation:

* [PHP Service](https://docs.lando.dev/config/php.html)
* [Service Overrides](https://docs.lando.dev/config/services.html#advanced)

And probably other stuff

Start up tests
--------------

Run the following commands to get up and running with this example.

```bash
# Should start up successfully
lando poweroff
lando start
```

Verification commands
---------------------

Run the following commands to validate things are rolling as they should.

```bash
# Should use 7.3 as the default php version
lando ssh -s default -c "php -v" | grep "PHP 7.3"

# Should use 10.x as the default postgresql-client version
lando ssh -s default -c "psql -V" | grep "10."

# Should use nginx 1. as the default webserver version
lando ssh -s default_nginx -c "nginx -v 2>&1 | grep 1.17"

# Should install composer 1.x by default
lando ssh -s default -c "composer --version --no-ansi" | grep "Composer version 1."
```

Destroy tests
-------------

Run the following commands to trash this app like nothing ever happened.

```bash
# Should be destroyed with success
lando destroy -y
lando poweroff
```
