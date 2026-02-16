# Security

+ [Set Security Headers in Webflow](#set-security-headers-in-webflow)
+ [X-Content-Type-Options](#x-content-type-options)
+ [X-Frame-Options](#x-frame-options)
+ [Cross-Origin-Resource-Policy](#cross-origin-resource-policy)
+ [Strict-Transport-Security](#strict-transport-security)
+ [Content Security Policy](#content-security-policy)

## Set Security Headers in Webflow
Developers do not have direct access to server configurations (e.g. `Apache`, `Nginx` or `.htaccess`), so the in-built `Webflow` security headings should be used. This is supported directly in `site settings`:

+ Go to `Site settings`
+ Click `Publishing`
+ Scroll to `Custom headers`
+ Toggle the `Enable custom site headers` option
+ Add the `security headers` here
+ Click `Publish` to republish and update the site with the changes

When this is turned on, `Webflow` will allow you to set custom `security headers` for the site. When off, the site will use the default headers.

<img width="1449" height="438" alt="Screenshot 2026-02-12 at 13 37 35" src="https://github.com/user-attachments/assets/0041c482-5a73-4a26-b2dc-572dc1ac31a0" />

A `security report` to check headers can be run [here](https://developer.mozilla.org/en-US/observatory/analyze?host=www.frontify.com).

## X-Content-Type-Options
This header is designed to only accept the trusted content of a file type. It's a security hardening header originally introduced by `Microsoft` and now supported by all modern browsers. Essentially: `"Do not guess (sniff) the file type — only trust the declared Content-Type header."`. Browsers sometimes try to be "helpful" by `MIME sniffing`: They look at file contents and override the declared type. An example, the server says:

```
Content-Type: text/plain
```

But the file contains:

```javascript
<script>alert(1)</script>
```

The browser may guess this is `HTML` or `JavaScript` and execute the code. This can lead to an `XSS` vulnerability. With this header set with the `nosniff` value, the browser will refuse to execute the file based on the server setting and treats the content of the file as text because of the `text/plain` specified. This is `safe` and is recommended by `OWASP`.

```
X-Content-Type-Options: nosniff
```

## X-Frame-Options
`X-Frame-Options` is a security header that controls whether other websites are allowed to embed your pages inside an `<iframe>`. It protects against `clickjacking` attacks. An example of `clickjacking`:

```html
<iframe src="https://yoursite.com/transfer-money" style="opacity:0"></iframe>
```

This may allow an attaker to place fake buttons over the top of the page. Basically, this prevents the website from being added to an `<iframe>` and to prevent it from being `framed`, so the browser blocks the embed entirely.

```
X-Frame-Options: DENY

# Only the same domain can frame the site
X-Frame-Options: SAMEORIGIN
```

## Cross-Origin-Resource-Policy
`Cross-Origin-Resource-Policy (CORP)` tells the browser: `"Only allow this resource to be loaded by pages from the same origin."`. It prevents other websites from embedding or reading your files. It is basically `anti–hotlinking` & `data-leak protection` built into the browser. `CORP` blocks the request at the browser level. 

Without this header, another site can freely load the assets from the site:

```html
<img src="https://yoursite.com/private-image.png">
<script src="https://yoursite.com/data.json"></script>
```

Same origin means:

+ `same protocol (https)`
+ `same domain`
+ `same port`

e.g. `https://example.com` → `https://example.com/image.png`

To set the header (only pages from the exact same origin can load it.). `Subdomains` count as different origins:

```
Cross-Origin-Resource-Policy: same-origin
```

## Strict-Transport-Security
`Strict-Transport-Security (HSTS)` tells the browser: `"Only ever connect to this site using HTTPS — never HTTP."`. It prevents downgrade attacks and insecure connections. Without this security header, an attacker on public Wi-Fi could:

+ `intercept`
+ `redirect`
+ `strip HTTPS`
+ `steal cookies/session`

This is called an `SSL stripping attack`.

When the browser sees:

```
Strict-Transport-Security: max-age=63072000; includeSubDomains; preload
```

This means: `"For the next 2 years, NEVER use HTTP for this site."`. Future visits to: `http://example.com` automatically become: `https://example.com` before any network request happens (an attacker can't intercept). The `max-age` value is the time in seconds the rule stays active. This example is: `63072000 = 2 years`. The browser forces `HTTPS` for 2 years. By including `includeSubDomains` this also applies to any subdomains e.g. `page.example.com`. With `preload`, this asks browsers to hardcode your domain into their built-in `HTTPS list` meaning even the very first visit is `HTTPS` and no initial `HTTP` request ever happens. Major browsers ship with this baked in.

Security standards like the `OWASP Foundation` recommend enabling `HSTS` for all production sites. It’s one of the `highest-value security headers` to use.

## Content Security Policy
Think of `Content Security Policy (CSP)` as a firewall for the browser. Instead of trusting every `script`, `image`, or `iframe` a page tries to load, `CSP` tells the browser: "Only load resources from these exact places — block everything else.". It's one of the strongest defenses against `XSS` and `supply-chain` attacks.

In simple terms, `CSP` tells the browser exactly which external resources are allowed to load — `scripts`, `styles`, `images`, `tracking pixels`, `frames`, etc. Everything not explicitly allowed is blocked.

If the CSP policy says:

```
script-src 'self'
```

A script like this is unable to run and the browser will block it immediately:

```html
<script src="https://evil.com/steal-cookies.js"></script>
```

Core keywords:

+ `'self'` - Your own domain only
+ `'none'` - Block completely
+ `'unsafe-inline'` - Allow inline <script> or style="" (sometimes required)
+ `'unsafe-eval'` - Allow eval() but avoid if necessary
+ `https://domain.com` - Allow specific external source. The preferred method

An example `CSP` may look like this:

```
default-src 'self'; script-src 'report-sample' 'self' https://ajax.googleapis.com/ajax/libs/webfont/1.6.26/webfont.js https://cdn-4.convertexperiments.com/v1/js/1004740-100417102.js https://cdn.jsdelivr.net/npm/@finsweet/attributes-autovideo@1/autovideo.js https://consent.cookiebot.com/uc.js https://player.vimeo.com/api/player.js https://use.typekit.net/zff2ofj.js https://www.googletagmanager.com/gtm.js; style-src 'report-sample' 'self' https://cdn.jsdelivr.net https://cdn.prod.website-files.com https://fonts.googleapis.com; object-src 'none'; base-uri 'self'; connect-src 'self' https://cdn-4.convertexperiments.com https://consentcdn.cookiebot.com https://eu01.rec.mouseflow.com https://px.ads.linkedin.com https://region1.analytics.google.com https://tags.srv.stackadapt.com https://trc-events.taboola.com https://ws.zoominfo.com; font-src 'self' data: https://cdn.prod.website-files.com https://fonts.gstatic.com https://use.typekit.net; frame-src 'self' https://www.googletagmanager.com; img-src 'self' https://alb.reddit.com https://cdn.prod.website-files.com https://px.ads.linkedin.com; manifest-src 'self'; media-src 'self'; report-uri https://698f2163e3e2c4cc2a5648c3.endpoint.csper.io?builder=true&v=2; worker-src 'none';
```

A browser extension for `Chrome` and `Firefox` can be used the generate the CSP [here](https://csper.io/generator).
