---
id: 7x0ejxlnnfn7p9nh0nflgjy
title: 'Get `nth` word of URL parameter in PHP'
desc: 'How to get first word of URL parameter'
updated: 1664735200645
created: 1566944400000
tags:
  - php
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/57680284/6456163) for the original answer.

To break the string at a space, you would use the explode function. That separates the parameter and breaks it into an array, so to get the first word you just need to get the 0th index:

```php
$fullname = explode(" ", $_GET["name"])[0];
```

If space in your URL is encoded as in your example, you just need to replace the space with the encoding:

```php
$fullname = explode("%20", $_GET["name"])[0];
```

**Edit**: As pointed out in the comments, the first method should be the way to go because your method of getting the parameter automatically decodes the URL.
