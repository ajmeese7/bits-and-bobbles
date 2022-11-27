
> See [here](https://stackoverflow.com/a/72585441/6456163) for the original answer.

This answer is modified from the awesome answer by @hmomin, except this answer gets the words in German instead of English as you requested:

```python
import requests

url = "https://10fastfingers.com/speedtests/get_words"

data = {
    "speedtest_mode": "",
    "speedtest_id": "2",
}

cookies = {
    "CAKEPHP": "c79f210mdl6n2jpp962g9vjk9f",
    "CookieConsent": "{stamp:%276CPboWb+OVPYxb8oz6CfbjxqXJzoYqXEDiPE62FxLheS24AUkkmksA==%27%2Cnecessary:true%2Cpreferences:true%2Cstatistics:true%2Cmarketing:true%2Cver:2%2Cutc:1654956041620%2Cregion:%27us%27}",
    "CakeCookie[lang]": "Q2FrZQ%3D%3D.5exP",
    "CakeCookie[alternate_language_suggestion]": "Q2FrZQ%3D%3D.9PBdWA%3D%3D",
}

headers = {
    "accept": "*/*",
    "accept-encoding": "gzip, deflate, br",
    "accept-language": "en-US,en;q=0.9",
    "cache-control": "no-cache",
    "content-length": "30",
    "content-type": "application/x-www-form-urlencoded; charset=UTF-8",
    "cookie": "CAKEPHP=c79f210mdl6n2jpp962g9vjk9f; CookieConsent={stamp:'6CPboWb+OVPYxb8oz6CfbjxqXJzoYqXEDiPE62FxLheS24AUkkmksA==',necessary:true,preferences:true,statistics:true,marketing:true,ver:2,utc:1654956041620,region:'us'}; CakeCookie[lang]=Q2FrZQ==.5exP; CakeCookie[alternate_language_suggestion]=Q2FrZQ==.9PBdWA==",
    "dnt": "1",
    "origin": "https://10fastfingers.com",
    "pragma": "no-cache",
    "referer": "https://10fastfingers.com/typing-test/german",
    "sec-fetch-dest": "empty",
    "sec-fetch-mode": "cors",
    "sec-fetch-site": "same-origin",
    "sec-gpc": "1",
    "user-agent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.5005.99 Safari/537.36",
    "x-requested-with": "XMLHttpRequest",
}

response_object = requests.post(url, data=data, cookies=cookies, headers=headers)
words = response_object.text
print(words)
```
