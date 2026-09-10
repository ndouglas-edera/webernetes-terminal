# webernetes-terminal
A minimal, terminal-only view of "```my-webernetes-demo```"

## Embed within docs as an <iframe>
The browser loads the Webernetes application as a separate document. Its JavaScript runs in the ```<iframe>``` browser context, creates the in-browser Kubernetes cluster, and the docs page doesn't need to know anything about Webernetes. If the hosting configuration sends something like ```X-Frame-Options: DENY``` or complains about an incompatible CSP ```Content-Security-Policy: frame-ancestors 'none'``` the browser will refuse to display it.

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Terminal Demo</title>
</head>
<body>
  <iframe
    src="https://ndouglas-edera.github.io/webernetes-terminal/"
    style="
      width: 100%;
      height: 500px;
      border: 0;
    "
    title="Interactive Webernetes demo"
  ></iframe>
</body>
</html>
```

Otherwise, we will likely need to publish a small embeddable JavaScript bundle. The script would find the element and instantiate the terminal. That gives us something that feels much more like a documentation component than an ```<iframe>```. Hextra/Hugo is quite amenable to this sort of extension since Hextra supports site-level layout ```overrides``` and custom ```shortcodes```. So the docs repo realistically could provide a Hugo ```shortcode``` that emits the embed markup.
