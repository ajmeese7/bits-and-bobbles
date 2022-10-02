---
id: 77l69khkyodwil66ey7y2xr
title: 'Remove additional file extensions from filenames'
desc: 'Regex Function to remove Double Extension'
updated: 1664737896747
created: 1664665931000
tags:
  - regex
  - python
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73921072/6456163) for the original answer.

What I recommend is running a regex to remove `.pdf` when the name string ends with it, like so:

```python
if pdf_checker(name):
    newName = re.sub(r'\.pdf$', '.txt', name)
    convert_pdf_to_txt(name, newName)
```

Then replace this line:

```python
make_new_text_file = open(text_folder_path + '/' + path + '.txt', 'w')
```

With the following:

```python
make_new_text_file = open(text_folder_path + '/' + txtname, 'w')
```
