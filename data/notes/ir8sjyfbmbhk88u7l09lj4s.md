
> See [here](https://stackoverflow.com/a/72681340/6456163) for the original answer.

The key is returning false after calling your function, so the page redirect is not triggered by the input submission:

```html
<form>
  <label for="pswd">ENTER PASSWORD</label>
  <br>
  <input class="box" type="password" id="pswd">
  <br>
  <input class="confirm" type="submit" value="SUBMIT" onclick="checkPswd(); return false;" />
</form>
```

```js
function checkPswd() {
  let confirmPassword = "08012020";
  let password = document.getElementById("pswd").value;

  if (password === confirmPassword) {
    alert("CORRECT!");
  } else{
    alert("Password is incorrect, Please try again.")
  }
}
```

I would like to add that performing client-side password checking is very insecure since the source code can easily be inspected, so if you are hoping to use this in a real website I would suggest you consider a different approach!
