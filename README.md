# openbasalt.org

Source of the [openbasalt.org](https://openbasalt.org) website.

Plain static HTML and CSS, no build step. The only scripts are the analytics
tag and its small bot filter, both described below. Served by GitHub Pages from the
`main` branch root, with the custom domain set in `CNAME`.

```
index.html        home page
404.html          not found page
assets/site.css   styles (light and dark via prefers-color-scheme)
assets/umami-filter.js  keeps automated browsers out of the visit count
assets/           favicons and the social preview image
robots.txt, sitemap.xml
```

To preview locally, serve the folder with any static server, for example
`python3 -m http.server 8000`, and open http://localhost:8000.

## Privacy and analytics

Every page loads [Umami](https://umami.is), self-hosted at
`analytics.openbasalt.org`, to count visits. It sets no cookies, stores no
personal data and keeps no cross-site identifier, so there is no consent
banner. The tag carries `data-do-not-track="true"`, so browsers that send Do
Not Track are not counted at all, and `data-domains` limits it to
`openbasalt.org` and `www.openbasalt.org`, so local previews and forks never
report anything. The footer of the home page says the same in one line.

The tag also carries `data-before-send="umamiBeforeSend"`, a function defined
in `assets/umami-filter.js` and loaded just before it. It keeps automated
browsers out of the count without blocking them: crawlers, previews and test
tools can fetch every page as usual, they are just not counted. Umami calls the
function before each report, and it skips the report when `navigator.webdriver`
is true, when the user agent carries a common headless or bot marker
(HeadlessChrome, PhantomJS, bot, crawler, spider, slurp, facebookexternalhit,
preview and similar, case insensitive), or when the screen is exactly 800x600
and the browser reports no languages at all. Every other report goes out
unchanged. It stores nothing and sets no cookie. When the filter changes, bump
the `?v=` query on its tag in both HTML files.

Published text follows the project style: no em or en dashes, no bold, no
ellipsis.
