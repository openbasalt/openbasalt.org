# openbasalt.org

Source of the [openbasalt.org](https://openbasalt.org) website.

Plain static HTML and CSS, no build step. The only scripts are the analytics
tag and its small bot filter, and the gallery viewer, all described below. Served by GitHub Pages from the
`main` branch root, with the custom domain set in `CNAME`.

```
index.html        home page
gallery/index.html  gallery: Samba Conductor screenshots and a pointer to the Basalt OS gallery
404.html          not found page
assets/site.css   styles (light and dark via prefers-color-scheme)
assets/umami-filter.js  keeps automated browsers out of the visit count
assets/gallery.js  gallery viewer and the optional Videos section (same file as on basalt-os.org)
assets/gallery/   gallery images: <id>-720.webp and .jpg thumbnails, <id>-1600.webp
assets/           favicons and the social preview image
robots.txt, sitemap.xml
```

To preview locally, serve the folder with any static server, for example
`python3 -m http.server 8000`, and open http://localhost:8000.

## Gallery

`gallery/index.html` works like the Basalt OS gallery (see the README of
basalt-os/basalt-os.org): each image is a `figure` in a `ul.shots` with a
one-line caption and its source and date, in three files under
`assets/gallery/` (720 px WebP and JPEG thumbnails, a 1600 px WebP for the
viewer). Only lab captures with made-up names, no real accounts, e-mail
addresses, internal host names or addresses, passwords or keys. Without
JavaScript every thumbnail is a link to the large image.

Videos: the Videos section stays hidden until the JSON block
`#gallery-videos` in `gallery/index.html` lists at least one video, as
`[{"id": "<YouTube video id>", "title": "...", "caption": "..."}]`. Nothing
is requested from YouTube until a person presses Play; then the player loads
from youtube-nocookie.com.

The footer links to the project on GitHub, X and YouTube with plain links
and inline icons, no widgets.

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
the `?v=` query on its tag in every HTML file.

Published text follows the project style: no em or en dashes, no bold, no
ellipsis.
