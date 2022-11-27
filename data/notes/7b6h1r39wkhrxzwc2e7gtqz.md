
> See [here](https://stackoverflow.com/a/73671526/6456163) for the original answer.

I think what you're looking for here is the `setfacl` command, which sets the default permissions for a specified directory. After you mount the directory, try the following:

```shell
sudo setfacl -d -m u:www-data:rwx /www
```

If you want to change the existing permissions as well, add the `-R` flag:

```shell
sudo setfacl -R -d -m u:www-data:rwx /www
```
