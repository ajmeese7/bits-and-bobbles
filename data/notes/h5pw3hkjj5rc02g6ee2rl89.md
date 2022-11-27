
> See [here](https://stackoverflow.com/a/72618755/6456163) for the original answer.

A modification of the thread you linked to do what you are requesting:

```php
$dom = new DOMDocument();
$dom->loadHTML($content);

foreach ($dom->getElementsByTagName('img') as $img) {
    $current_src = $img->getAttribute('src');
    $new_src = preg_replace('http://', '/files/images', $current_src);
    $img->setAttribute( 'src', $new_src );
}

$content = $dom->saveHTML();
```

I don't have a machine with PHP readily available to test this for you (not at home), so let me know if you have any issues with it and I would be happy to troubleshoot for you.
