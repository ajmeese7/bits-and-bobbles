---
id: xotvh2n410zlhucecj873vv
title: 'Manipulate Pandas Index column on write'
desc: 'How to remove Pandas Index Column when Writting to CSV'
updated: 1664735134988
created: 1655572560000
tags:
  - python
  - pandas
  - dataframe
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72669566/6456163) for the original answer.

According to [this thread](https://github.com/pandas-dev/pandas/issues/26042), the problem can normally be avoided by skipping calling `reset_index`.

If that doesn't work for you, one alternative solution that was offered is to try the following:

```python
df.to_csv(" file_name.csv ")
df_new = pd.read_csv("file_name.csv").drop(["unnamed 0"], axis=1)
```
