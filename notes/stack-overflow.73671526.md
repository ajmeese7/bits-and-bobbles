---
id: 7b6h1r39wkhrxzwc2e7gtqz
title: 'Set default permissions for new files in Linux directory'
desc: 'How can I mount /var/www to /www using linux mount --bind command?'
updated: 1664737044161
created: 1662824580000
tags:
  - linux
  - setfacl
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73671526/6456163) for the original answer.

I think what you're looking for here is the `setfacl` command, which sets the default permissions for a specified directory. After you mount the directory, try the following:

```shell
sudo setfacl -d -m u:www-data:rwx /www
```

If you want to change the existing permissions as well, add the `-R` flag:

```shell
sudo setfacl -R -d -m u:www-data:rwx /www
```
