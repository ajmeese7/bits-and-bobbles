---
id: 02a37oi2kumwxjlwwv6pftk
title: 'Pass list of variables to shell script in GitHub Actions'
desc: 'GitHub Actions pass list of variables to shell script'
updated: 1664736529035
created: 1657343520000
tags:
  - github-actions
  - shell
  - yaml
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72918267/6456163) for the original answer.

Today I was able to do this with the following YAML (truncated):

```yaml
...
with:
  targets: |
    FolderA/SubfolderA
    FolderB/SubfolderB
```

The actual GitHub Action passes this as an argument like the following:

```yaml
runs:
  using: docker
  image: Dockerfile
  args:
    - "${{ inputs.targets }}"
```

What this does is simply sends the parameters as a string with the newline characters embedded, which can then be iterated over similar to an array in a POSIX-compliant manner via the following shell code:

```shell
#!/bin/sh -l

targets="${1}"

for target in $targets
do
  echo "Proof that this code works: $target"
done
```

Which should be capable of accomplishing your desired task, if I understand the question correctly. You can always run something like `sh ./script.sh $target` in the loop if your use case requires it.
