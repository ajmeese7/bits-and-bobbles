
> See [here](https://stackoverflow.com/a/73737844/6456163) for the original answer.

The problem is your use of the `find_element` method, because afterwords you attempt to access an index of the variable, when it is a single element in length.

What you are looking for is the `find_elements` command, which will return a list from which you can select individual elements. For more information, see the Selenium documentation on this topic [here](https://selenium-python.readthedocs.io/locating-elements.html).
