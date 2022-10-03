---
id: pr8ia07n2sdkf6i0pal6mcf
title: 'Human readable duration format'
desc: ''
updated: 1664741386535
created: 1591801020000
---

### JavaScript

```js
function formatDuration (seconds) {
  if (seconds == 0) return 'now';
  let years = 0, days = 0, hours = 0, minutes = 0;

  if (seconds >= 31536000) {
    years = parseInt(seconds / 31536000);
    seconds = seconds % 31536000;
  }
  if (seconds >= 86400) {
    days = parseInt(seconds / 86400);
    seconds = seconds % 86400;
  }
  if (seconds >= 3600) {
    hours = parseInt(seconds / 3600);
    seconds = seconds % 3600;
  }
  if (seconds >= 60) {
    minutes = parseInt(seconds / 60);
    seconds = seconds % 60;
  }

  let numMetrics = [years, days, hours, minutes, seconds]
    .reduce(function(acc, val) { return acc + (val != 0 ? 1 : 0); }, 0);

  let result = "";
  if (years != 0) {
    result += years + " year" + (years > 1 ? 's' : '');
    if (numMetrics == 2) result += " and ";
    if (numMetrics > 2) result += ", ";
    numMetrics--;
  }
  if (days != 0) {
    result += days + " day" + (days > 1 ? 's' : '');
    if (numMetrics == 2) result += " and ";
    if (numMetrics > 2) result += ", ";
    numMetrics--;
  }
  if (hours != 0) {
    result += hours + " hour" + (hours > 1 ? 's' : '');
    if (numMetrics == 2) result += " and ";
    if (numMetrics > 2) result += ", ";
    numMetrics--;
  }
  if (minutes != 0) {
    result += minutes + " minute" + (minutes > 1 ? 's' : '');
    if (numMetrics == 2) result += " and ";
    if (numMetrics > 2) result += ", ";
    numMetrics--;
  }
  if (seconds != 0) {
    result += seconds + " second" + (seconds > 1 ? 's' : '');
  }

  return result.trim();
}
```

### CoffeeScript

```coffee
formatDuration = (seconds) ->
  if seconds == 0
    return 'now';
  [years, days, hours, minutes] = [0,0,0,0]

  if seconds >= 31536000
    years = parseInt(seconds / 31536000);
    seconds = seconds % 31536000;
  if seconds >= 86400
    days = parseInt(seconds / 86400);
    seconds = seconds % 86400;
  if seconds >= 3600
    hours = parseInt(seconds / 3600);
    seconds = seconds % 3600;
  if seconds >= 60
    minutes = parseInt(seconds / 60);
    seconds = seconds % 60;

  `numMetrics = [years, days, hours, minutes, seconds]
    .reduce(function(acc, val) { return acc + (val != 0 ? 1 : 0); }, 0);`

  result = "";
  if years != 0
    result += years + " year" + `(years > 1 ? 's' : '')`;
    if numMetrics == 2
      result += " and ";
    if numMetrics > 2
      result += ", ";
    numMetrics--;
  if days != 0
    result += days + " day" + `(days > 1 ? 's' : '')`;
    if numMetrics == 2
      result += " and ";
    if numMetrics > 2
      result += ", ";
    numMetrics--;
  if hours != 0
    result += hours + " hour" + `(hours > 1 ? 's' : '')`;
    if numMetrics == 2
      result += " and ";
    if numMetrics > 2
      result += ", ";
    numMetrics--;
  if minutes != 0
    result += minutes + " minute" + `(minutes > 1 ? 's' : '')`;
    if numMetrics == 2
      result += " and ";
    if numMetrics > 2
      result += ", ";
    numMetrics--;
  if seconds != 0
    result += seconds + " second" + `(seconds > 1 ? 's' : '')`;

  return result.trim();
```
