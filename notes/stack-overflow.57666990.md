---
id: xz9gt68pw6ghmdamvtybbyo
title: 'Format dynamic URL to be SEO friendly with htaccess and PHP'
desc: 'How to format URL on Website with htaccess'
updated: 1664735216510
created: 1566887160000
tags:
  - php
  - htaccess
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/57666990/6456163) for the original answer.

[This](https://grokbase.com/t/php/php-general/0159ts8x8h/passing-parameters-in-the-url-using-forward-slashes#20010509ss83mvqx7894e90njxvrsjgkcg) page appears to have a solution to what you are trying to do:

```php
<?
    $Params = explode( '/', $PATH_INFO );

    while( list( $Index, $Value ) = each( $Params )) {
        echo "Params[ $Index ] = $Value<BR>\n";
    }
?>
```


> Hit this URL:

> http://whatever.site.com/ThisIsAProgram/these/directories/are/not/real

> You should get:

> Params[ 0 ] =

> Params[ 1 ] = these

> Params[ 2 ] = directories

> Params[ 3 ] = are

> Params[ 4 ] = not

> Params[ 5 ] = real

And to display the PHP file as just the file name, try this:

```text
Options +MultiViews
RewriteEngine On

RewriteCond %{THE_REQUEST} /([^.]+)\.php [NC]
RewriteRule ^ /%1 [NC,L,R]
RewriteCond %{REQUEST_FILENAME}.php -f
RewriteRule ^ %{REQUEST_URI}.php [NC,L]
```

----------

**EDIT**: If you are wanting a more complete example, [this answer](https://serverfault.com/a/210766) covers it a lot more in depth than I could. This will definitely help you cover all your bases and understand the issue if my other linked article doesn't make it clear enough.
