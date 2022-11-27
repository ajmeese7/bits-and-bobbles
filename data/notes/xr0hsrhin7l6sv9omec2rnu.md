
> See [here](https://stackoverflow.com/a/57394863/6456163) for the original answer.

You are never using `$condition1` and `$condition2` after you give them their static values, which might be the problem here.

Another thing I would consider is switching from your current `$result` assignment to this:

```php
$sql = "SELECT * FROM client_scope WHERE client_scope_id = '$siteID'
        AND client_Id='".$_SESSION['clientId']."'";
$result = $conn->query($sql) or die($conn->error);
```

In your current query, you didn't include single quotes around `$siteId`, which was likely one of the problems because I had the same issue with a query yesterday.

Another problem was you had a set of single quotes inside another set of single quotes with your `client_Id` assignment, which doesn't work. Using the period operator, this method joins the `$_SESSION` part of the query with the rest. This is explained [here](https://stackoverflow.com/a/3383845/6456163).

Finally, the `or die($conn->error)` part of `$result` typically shows you errors that may exist like this in your queries in the future. For an explanation of this, see [here](https://stackoverflow.com/a/35669638).

This may be a personal preference, but I have always seen your foreach loop written as something similar to this:

```php
while ($row = $result->fetch_assoc()) {
  echo json_encode($row);
}
```

I don't know if there is any functional difference, but it may be another factor.
