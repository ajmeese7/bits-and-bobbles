
> See [here](https://stackoverflow.com/a/72932790/6456163) for the original answer.

One way to achieve what you are looking for in pure CSS is with an attribute prefix selector (which uses a form of regular expressions). In your case the following would likely do the trick:

```css
[id^="edit-field-geolocation-proximity-center-geocoder"] .form-item {
  /* your styles here :) */
}
```

[This thread](https://stackoverflow.com/a/8903313/6456163) offers a lot of additional excellent methods on how to use regex in CSS if you would like to do some additional reading.
