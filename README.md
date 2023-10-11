# How To Get ExpressionEngine running on Cloudways

1. Disable Varnish cache.
2. [Enable necessary PHP extensions](https://support.cloudways.com/en/articles/7891624-how-to-enable-php-functions):
   - escapeshellcmd (REQUIRED)
   - tmpfile (SOME ADDONS MIGHT NEED THIS)
3. Make sure you have [set correct file permissions](https://docs.expressionengine.com/latest/installation/installation.html#3-set-file-permissions).
4. Use memcached instead of file cache.
5. Move system/ to private_html/ (you can't place files in project root directory).
   - Set system path in index.php and admin.php to: '../private_html/system'
6. Check your file permissions again.
