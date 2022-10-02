---
id: zun8bhcow657s47nj90oq7q
title: 'Will user update or overwriting file before other session done in PHP?'
desc: ''
updated: 1664735177962
created: 1653584040000
tags:
  - php
  - file
  - json
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72392166/6456163) for the original answer.

PHP is synchronous unless you specify otherwise, so any write operations *should* be queued and prevent the vast majority of write conflicts. To be extra safe, I am copying an answer [\[link\]](https://stackoverflow.com/a/24080883/6456163) that explains how to do so below:

---

File access is simultaneous but you can use [`flock`](http://php.net/flock) to block other handles from accessing the file while you perform your read/write operations. It sounds like the best solution to your problem would be to use PDO and [SQLite](http://php.net/manual/en/book.sqlite.php) (if available). This way you have the database handle all locking for you but do not need a dedicated database server. SQLite is entirely file based.

If SQLite is not available, you'll want to make use of flock's `LOCK_EX` operation, this will only allow one write stream to access the file at a time, e.g.

```php
// create the file handle
$hnd = fopen($destpath, 'ab+');

if ($isReadOperation) {
    // shared lock - simultaneous reads can happen at one time
    flock($hnd, LOCK_SH);

    // perform your read operation
} else {
    // exclusive lock - only one write can occur at a time after all shared locks are released
    flock($hnd, LOCK_EX);

    // perform your read/write operation
}

// release the lock
flock($hnd, LOCK_UN);

// release the file handle
fclose($hnd);
```
