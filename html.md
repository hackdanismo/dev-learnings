# HTML

Initial `HTML` document structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <meta name="color-scheme" content="light dark">
    <meta name="description" content="Description of the page here. This is for SEO (Search Engine Optimisation).">

    <title>Example Page</title>

    <!-- Favicon -->
    <link rel="icon" href="/favicon.ico" sizes="any">
    <link rel="icon" href="/icon.svg" type="image/svg+xml">
    <link rel="apple-touch-icon" href="/apple-touch-icon.png">

    <!-- CSS stylesheet(s) -->
    <link rel="stylesheet" href="styles/style.css">

    <!-- Preload example -->
    <!-- <link rel="preload" href="/fonts/inter.woff2" as="font" type="font/woff2" crossorigin> -->
</head>
<body>
    <a class="skip-link" href="#main">Skip to main content</a>

    <header>
        <nav aria-label="Primary"></nav>
    </header>

    <main id="main" tabindex="-1">
        <section aria-labelledby="section-heading">
        <h1 id="section-heading"></h1>
        </section>
    </main>

    <footer>
        <nav aria-label="Footer"></nav>
    </footer>

    <noscript>
        <p>JavaScript is disabled in your browser.</p>
    </noscript>

    <!-- Scripts -->
    <script src="scripts/main.js" defer></script>
</body>
</html>
```
