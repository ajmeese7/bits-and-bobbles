---
id: 1pudr09k5317l5cb8hk40ap
title: 'Join PHP variable with string'
desc: 'UNION ALL does not echo out additional text'
updated: 1664735218634
created: 1566886500000
tags:
  - php
  - pdo
  - mysql
  - sql
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/57666910/6456163) for the original answer.

I was in the process of writing this and saw Tim's comment, which is exactly what I was going to say. It seems much easier to add the string "TEXT" to the information you want in the PHP instead of the SQL. Here is an example:

```php
echo "TEXT" . $valueAA . $valueAVAR;
```
