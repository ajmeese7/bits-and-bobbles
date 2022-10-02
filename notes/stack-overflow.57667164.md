---
id: qfamtbq83qo8rdmogk1n39o
title: 'Iterate over objects returned from Google Maps API'
desc: 'How to fetch Latitude and Longitude of 5 Nearby Places from Google Maps API using PHP JSON object?'
updated: 1664732666090
created: 1566889080000
tags:
  - php
  - json
  - google-maps
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/57667164/6456163) for the original answer.

kshetline answered your question the way you would interact with the JSON object in JavaScript, but since you never mentioned JavaScript and only have PHP in your question's tags I am going to try to answer you with PHP.

To access properties of a JSON object in PHP, you must use the [arrow syntax](https://www.w3schools.com/js/js_json_php.asp):

```php
$result = $djd->results;
for($i=0; $i<5; $i++){
    // Do what you want with them from here
    $lat = $result[$i]->geometry->location->lat;
    $lng = $result[$i]->geometry->location->lng;

    // Example of how to return them
    echo json_encode($lat);
    echo json_encode($lng);
}
```

I do not know what the JSON returned looks like, so I based my PHP off of the JSON in kshetline's answer. I'm sure their JSON is correct, so this should work.
