---
id: sahtik0t9snvikmkks9pppx
title: 'Authenticate for Google Identity Services (GIS)'
desc: 'Login using Google authentication without opening new window/tab'
updated: 1664737464642
created: 1663631220000
tags:
  - javascript
  - google
  - gis
  - gapi
  - authentication
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73778561/6456163) for the original answer.

GAPI is now being discontinued, and Google is transitioning to Google Identity Services (GIS). The new method is similar to that which was suggested by @AlexfromJitbit, with some small modifications:

```html
<html>
  <body>
    <script src="https://accounts.google.com/gsi/client" async defer></script>
    <div id="g_id_onload"
         data-client_id="YOUR_CLIENT_ID"
         data-ux_mode="redirect"
         data-login_uri="https://www.example.com/your_login_endpoint">
    </div>
    <div class="g_id_signin" data-type="standard"></div>
  </body>
</html>
```

This code is pulled from the new [GIS example](https://developers.google.com/identity/gsi/web/guides/migration#redirect-mode_1), and is recommended for all new applications as the old API will be retired as of 31 March 2023.
