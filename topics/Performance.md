# Performance

**Time To First Byte (TTFB)**

Time taken from the time that page starts loading to the time when the first byte of the first request comes.

Reasons:

Too many redirects, low throughput of server (thrashing), no caching, insufficient infra, unoptimised DB tables, inefficient DB Server

Page starts loading -> Cache(Yes/No) -> DNS Lookup -> Establish connection -> Request -> Processing -> Response (Download) -> DOM Update -> Render

![Request Response Model](https://panelbear.com/static/img/docs/page-load-timeline.png)

> Cross-origin requests may not have response start if their Timing-Allow-Origin is not specified

> -main.css -> This excludes this file in Network Panel

Benchmark -> 0.8sec

**First Contentful Paint (FCP)**

When the first content appears

Benchmark -> 1.8 seconds


**Largest Contentful Paint (LCP)**

Benchmark -> 2.5 seconds - 4 seconds

Considers text blocks, images, videos, image tags inside svg

Does not currently consider svgs
Does not consider background tabs


**Preloading**

If a resource will surely be fetched but is placed later, we can fetch it beforehand. It will not be executed or applied.

```
<link rel="preload" href="media.css"/>
```

As we load critical CSS which is used for ATF (Above the fold) content in the head tag, we can fetch non-critical css using preload, so that when user scrolls down, it does not have to wait for JS to download and execute and then fetch the non-critical CSS.

> Preload fonts

> We can also preload Javascript lazy-loaded bundles using _/* webpackPreload: true */_

