# Debounce and Throttle

**Debounce**

Call the function if a stipulated time period has elapsed and there are no clicks. It is a function of keystrokes.

For example, if I am typing an input in a search box, the moment I stop, a call goes with the last inserted value

This is backward-looking. The data going from the call will be from the last input click.


**Throttle**

Call the function if the stipulated time period has elapsed since the last click and function is being called again.

For example, if I am given a button and I keep clicking on it, the call will be eligible to go after intervals of 500ms. This is forward-looking. The data going in the call will be from the next function call