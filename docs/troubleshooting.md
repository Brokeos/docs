# Error resolution

Errors may occur, it is not necessarily from the CMS,
but here are the most common mistakes with their solutions!

## Common Problems

### The home page works but the other pages produce a 404 error

The url rewriting is not activated, you just have to activate it (see next question).

### URL rewriting is not enabled in Apache 2
You need to modify the `/etc/apache2/sites-available/000-default.conf` file and add these lines between the `<VirtualHost>` tags:
```xml
<Directory "/var/www/html">
  AllowOverride All
</Directory>
```

Then restart Apache2 with
```
service apache2 restart
```

### Error 500 during registration

If the account is created correctly despite the error, this problem can occur if
the sending of e-mails is not correctly configured, for this check
the configuration of the sending of emails on the admin panel of your site.

### The file has not been uploaded when uploading an image

This problem occurs when you upload an image with a weight greater than the
maximum allowed by PHP (default 2mo).

You can change the maximum size allowed when uploading in the configuration
of PHP (in `php.ini`) by changing the following values:
```
upload_max_filesize = 10M
post_max_size = 10M
```
