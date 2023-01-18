# Document Load


**DOMContentLoaded** - When the initial HTML document has been downloaded and parsed

**load** - event is fired when the whole page is loaded, i.e., scripts, stylesheets, images are also loaded. This is for the initial page downloaded from the server. This does not take into account lazy-loaded bundles

**unload** - event is fired when the user is just leaving the page. No delays or asking the user tasks can be done here. Can be used to send page statistics to the server, like total time the user was on the website.

**beforeunload** - event is fired when the user has decided to leave the page. Here, we can ask the user whether (s)he wants to indeed leave the page or stay there.


Caveats:
https://javascript.info/onload-ondomcontentloaded#domcontentloaded-and-styles

Styles before Scripts pauses the DOM building till styles are downloaded. This also delays DOMContentLoaded event

*The paint doesn't pause till DOMContentLoaded is not done. The browser follows a WYSIWYG approach, i.e., paint the element that you see*

> Scripts encountered have to be executed before continuing to read the further html in the page. The exception is async. So, script download and execution will impact DOMContentLoaded.


*navigator.sendBeacon*

Send data to a url. Mostly done in an unload event, when user is leaving the page. 

**readyState**

Accessed using document.readyState

*readyStateChange* is the event name that can be invoked on the document object.

It has three values:

1) Pending
2) Interactive (DOMContentLoaded is called here)
3) Complete (load event is called here)

