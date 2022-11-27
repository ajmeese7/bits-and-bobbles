
> See [here](https://stackoverflow.com/a/72669696/6456163) for the original answer.

One way to do this is to ignore the first two lines of the output in sed:

```shell
sed "1,2 ! s/[^[:blank:]]\{1,\}/$green&$off/3";
```
