
> See [here](https://stackoverflow.com/a/57666910/6456163) for the original answer.

I was in the process of writing this and saw Tim's comment, which is exactly what I was going to say. It seems much easier to add the string "TEXT" to the information you want in the PHP instead of the SQL. Here is an example:

```php
echo "TEXT" . $valueAA . $valueAVAR;
```
