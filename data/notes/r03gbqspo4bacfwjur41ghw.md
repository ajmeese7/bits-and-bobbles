
> See [here](https://stackoverflow.com/a/72635466/6456163) for the original answer.

One way to do this is with the following one-liner, ran from the directory where the logs are located:

```shell
ls -t | head -n -8 | xargs --no-run-if-empty rm
```

Explanation:
- `ls -t` - lists all the files in order from youngest to oldest
- `head -n -8` - gets all the files except the first 8
- `xargs --no-run-if-empty rm` - deletes the selected files if there are any, preventing errors if you ever have fewer than 8 logs

If you want to set this up to run automatically every day, giving you peace of mind in case your server is offline on the 7th day of a cycle and misses the one week mark, run `crontab -e` and add the following to your jobs:

```shell
0 0 * * * cd yourDirNameHere && ls -t | head -n -8 | xargs --no-run-if-empty rm
```

Then the log cleaner will be ran every night at midnight.
