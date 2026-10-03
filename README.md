# openbasalt.org

Source of the [openbasalt.org](https://openbasalt.org) website.

Plain static HTML and CSS, no build step and no JavaScript. Served by GitHub
Pages from the `main` branch root, with the custom domain set in `CNAME`.

```
index.html        home page
404.html          not found page
assets/site.css   styles (light and dark via prefers-color-scheme)
assets/           favicons and the social preview image
robots.txt, sitemap.xml
```

To preview locally, serve the folder with any static server, for example
`python3 -m http.server 8000`, and open http://localhost:8000.

Published text follows the project style: no em or en dashes, no bold, no
ellipsis.

