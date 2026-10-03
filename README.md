# openbasalt.org

Source of the [openbasalt.org](https://openbasalt.org) website.

Plain static HTML and CSS, no build step and no JavaScript of its own (the only
script is the analytics tag described below). Served by GitHub Pages from the
`main` branch root, with the custom domain set in `CNAME`.

```
index.html        home page
404.html          not found page
assets/site.css   styles (light and dark via prefers-color-scheme)
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

Published text follows the project style: no em or en dashes, no bold, no
ellipsis.
