---
id: kfeqwwzucctubmzcu8vcg8i
title: 'Connect to CodeIgniter database from PHP'
desc: Can't get data through CodeIgniter query builder from and ODBC Connection
updated: 1664735222506
created: 1565374680000
tags:
  - php
  - codeigniter
  - odbc
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/57432006/6456163) for the original answer.

This might work instead:

```php
$sql = "SELECT * FROM utilizadores WHERE username = '$username' AND password='$password'";
$result = $conn->query($sql) or die($conn->error);

if ($result->num_rows > 0) {
  // return array
} else {
  return false;
}
```

This is similar to what I use with the mysqli library, but I don't know if it is something you are willing to incorporate into your project. It is a breeze to work with.

Also, it seems your method may be storing the passwords in cleartext, which is not a good idea.

**EDIT**- This is how I create my connection:

```php
$servername = "";
$username = "";
$password = "";
$dbname = "";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);
// Check connection
if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);
}
```

**EDIT #2**: The issue was using double quotes instead of single quotes. Please, nobody else fall into this demonic trap.
