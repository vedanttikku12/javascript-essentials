# Async Vs Defer

During normal html page execution, if we encounter a script tag, whether inline scripts or external, it blocks further page rendering. We can obviously move the scripts to the end of the page but if it is a long script that takes 1) time to load 2) time to execute, that affects page performance. Moreover, what if that script is not so critical to block our rendering and our DOMContentLoad and load events.

A better would obviously be to download them in parallel while the page execution is going on.

Here is where Async and Defer come into the picture.


**Defer**

-> Render non-blocking
-> Document Order in execution

A script with defer attribute would make sure that it loads without blocking render.

However, DOMContentLoaded event would need this script to be executed first.

If there are two scripts like:

```
<script src="long.js" defer>
<script src="small.js" defer>

```

Here if small.js loads first, long.js will still be executed before, thereby maintaining the order. The is to ensure that if small.js depends on long.js, that order change would be detrimental.


**Async**

-> Render non-blocking
-> Download Order in execution

A script with async will execute independently.
It is non-blocking and has no relation to the DOMContentLoaded event.
If it downloads before that event, the HTML parsing will pause and async script execution will happen.

The order in document does not matter. Whichever loads first, gets executed first and so on.


**Dynamic Scripts**

We can also add more scripts inside the inline script tag. By default, they behave like async scripts. Their download starts as soon as they are appended to the DOM.

We can of course, set the async attribute to false for them to be executed in the document order.

```
<script>
  const newScriptEl = document.createElement('script);

  newScriptEl.src="./newScript.js";

  newScriptEl.async = false;

  document.body.append(newScriptEl);
</script>
```