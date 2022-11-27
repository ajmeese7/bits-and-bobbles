
> See [here](https://stackoverflow.com/a/72974187/6456163) for the original answer.

Xpath can be a hassle sometimes, I recommend using the CSS selector method to accomplish this:

```python
element = driver.find_elements_by_css_selector("[aria-label='1100-1200-200167-620038']")
```

You could them use the element in your `visibility_of_element_located` method.
