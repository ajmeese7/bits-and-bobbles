---
id: ec6cknjyfvpq44zznh2fb7s
title: 'Selecting elements via CSS attribute selectors in Selenium'
desc: 'partial text in xpath'
updated: 1664736529084
created: 1657775640000
tags:
  - python
  - selenium
  - css
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72974187/6456163) for the original answer.

Xpath can be a hassle sometimes, I recommend using the CSS selector method to accomplish this:

```python
element = driver.find_elements_by_css_selector("[aria-label='1100-1200-200167-620038']")
```

You could them use the element in your `visibility_of_element_located` method.
