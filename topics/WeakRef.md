# Weak Ref

How do you create an object that would sure-shot be garbage collected and there wouldn't be issues of unaware references. Well, this is the way.

There are two ways to track when this reference is garbage collected. One of them is using FinalizationRegistry API


```
let popupWindow = window.open('/someurl.html');

// First approach

let timer = setInterval(() => {
  if (popupWindow.deref() === undefined) {
    console.log('popup window was garbage-collected');
    clearInterval(timer);
  }
});

//second approach

const finalizers = new FinalizationRegistry(() => {
  console.log('popup window was garbage-collected');
});

finalizers.register(popup.deref());

```

Reference: https://web.dev/detached-window-memory-leaks/#solution-postmessage