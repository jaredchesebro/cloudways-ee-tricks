# How To Get ExpressionEngine running on Cloudways

1. Disable Varnish cache.
   - I could be wrong but I think some work would need to be done for this to play nice with forms and other dynamic content.
2. [Test server requirements with EE Server Wizard](https://github.com/ExpressionEngine/ExpressionEngine-Server-Wizard)
   - This doesn't seem to pickup on all requirements, hence step #3.
3. [Enable necessary PHP extensions](https://support.cloudways.com/en/articles/7891624-how-to-enable-php-functions):
   - escapeshellcmd (REQUIRED)
   - tmpfile (SOME ADDONS MIGHT NEED THIS)
4. Make sure you have [set correct file permissions](https://docs.expressionengine.com/latest/installation/installation.html#3-set-file-permissions). Cloudways seems a bit more strict vs other hosts.
   - `find system/ee \( -type d -exec chmod 755 {} \; \) -o \( -type f -exec chmod 644 {} \; \)`
5. [Add .htaccess file.](https://docs.expressionengine.com/v6/installation/best-practices.html#1-create-an-htaccess-file)
6. Move `system/` to `private_html/` (you can't place files in project root directory).
   - Set system path in `index.php` and `admin.php` to: `../private_html/system`
7. Check your file permissions again.
8. Use memcached or redis instead of file cache.
   - [cache driver (either memcached or redis)](https://docs.expressionengine.com/v6/general/system-configuration-overrides.html#cache_driver)
   - [cache driver backup should probably be set to file](https://docs.expressionengine.com/v6/general/system-configuration-overrides.html#cache_driver_backup)
   - [memcached settings](https://docs.expressionengine.com/v6/general/system-configuration-overrides.html#memcached)
   - [redis settings](https://docs.expressionengine.com/v6/general/system-configuration-overrides.html#redis)
   - [Redis will require some work in the Cloudways panel to enable it.](https://www.cloudways.com/blog/redis-cache-now-available/)
