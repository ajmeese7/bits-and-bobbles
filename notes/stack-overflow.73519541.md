---
id: xwiuciw74voesgy2joqj019
title: 'Interact with the shadow DOM in Selenium'
desc: 'Selenium and tiktok accept cookied button'
updated: 1664736530153
created: 1661711340000
tags:
  - python
  - selenium
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73519541/6456163) for the original answer.

What I noticed when using the Selenium head to manually debug is that the `cookie` element does not show up on my machine. If you have anything on your browser/machine that could be preventing the cookie popup, that may be a factor.

An additional problem is that the `tiktok-cookie-banner` element uses the shadow DOM, which introduces a whole separate element of complexity. To solve this problem, I recommend the [shadow-automation-selenium](https://github.com/sukgu/shadow-automation-selenium) package, which the documentation explains how to use to interact with the element you are interested in. More information about the shadow DOM can be found in [this thread](https://stackoverflow.com/a/55761810/6456163).
