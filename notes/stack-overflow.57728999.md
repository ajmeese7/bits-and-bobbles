---
id: cozn8kms7qug72gdzd4cv5r
title: 'Failed to load resource: Preflight response is not successful'
desc: ''
updated: 1664736529102
created: 1567191000000
tags:
  - jquery
  - cordova
  - xmlhttprequest
  - cors
  - ios
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/57728999/6456163) for the original answer.

If you're still experiencing this issue, it appears to have been solved [here](https://github.com/ionic-team/cordova-plugin-ionic-webview/issues/70). The recommended solutions were:

- Implementing CORS server-side
- Using [Cordova native http plugin](https://github.com/silkimen/cordova-plugin-advanced-http)
