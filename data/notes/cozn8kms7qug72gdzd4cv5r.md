
> See [here](https://stackoverflow.com/a/57728999/6456163) for the original answer.

If you're still experiencing this issue, it appears to have been solved [here](https://github.com/ionic-team/cordova-plugin-ionic-webview/issues/70). The recommended solutions were:

- Implementing CORS server-side
- Using [Cordova native http plugin](https://github.com/silkimen/cordova-plugin-advanced-http)
