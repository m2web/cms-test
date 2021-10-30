# CMS-Test Tree Output

This tree command output below after this repo was created by a cloning the remote repo:

```bash
.
├── archetypes
│   └── default.md
├── config.toml
├── content
│   ├── about.md
│   ├── admin
│   │   ├── config.yml
│   │   └── index.html
│   ├── contact.md
│   ├── _index.md
│   └── posts
│       └── entry-from-netlify-cms.md
├── data
│   └── social.json
├── README.md
├── static
│   └── images
│       └── uploads
│           └── dune.jpg
├── themes
│   └── hugo-theme-ava
```

Then, after running git submodule update --init, the tree command output below:

```bash
.
├── archetypes
│   └── default.md
├── cms-test-tree.md
├── config.toml
├── content
│   ├── about.md
│   ├── admin
│   │   ├── config.yml
│   │   └── index.html
│   ├── contact.md
│   ├── _index.md
│   └── posts
│       └── entry-from-netlify-cms.md
├── data
│   └── social.json
├── README.md
├── static
│   └── images
│       └── uploads
│           └── dune.jpg
├── themes
│   └── hugo-theme-ava
│       ├── archetypes
│       │   └── default.md
│       ├── assets
│       │   ├── js
│       │   │   ├── darkm.js
│       │   │   └── prefixfree.js
│       │   └── scss
│       │       ├── _base.scss
│       │       ├── components
│       │       │   ├── _contact-form.scss
│       │       │   └── _pagination.scss
│       │       ├── _main.scss
│       │       ├── _mixins.scss
│       │       ├── _mode-dark.scss
│       │       ├── _mode-light.scss
│       │       ├── _reset.scss
│       │       ├── style.scss
│       │       ├── _typography.scss
│       │       └── _variables.scss
│       ├── config.toml
│       ├── CONTRIBUTING.md
│       ├── exampleSite
│       │   ├── archetypes
│       │   │   └── default.md
│       │   ├── config.toml
│       │   ├── content
│       │   │   ├── about.md
│       │   │   ├── contact.md
│       │   │   ├── _index.md
│       │   │   └── posts
│       │   │       ├── example2.md
│       │   │       ├── example3.md
│       │   │       ├── example4.md
│       │   │       ├── example5.md
│       │   │       ├── example6.md
│       │   │       ├── example7.md
│       │   │       ├── example8.md
│       │   │       ├── example.md
│       │   │       └── _index.md
│       │   └── data
│       │       └── social.json
│       ├── images
│       │   ├── default.jpeg
│       │   ├── screenshot.png
│       │   └── tn.png
│       ├── layouts
│       │   ├── 404.html
│       │   ├── _default
│       │   │   ├── baseof.html
│       │   │   ├── list.html
│       │   │   ├── page.html
│       │   │   └── single.html
│       │   ├── index.html
│       │   ├── partials
│       │   │   ├── dark-mode-toggle.html
│       │   │   ├── date.html
│       │   │   ├── footer.html
│       │   │   ├── google-analytics.html
│       │   │   ├── header.html
│       │   │   ├── icons.html
│       │   │   ├── og.html
│       │   │   ├── other-metas.html
│       │   │   ├── site-title.html
│       │   │   ├── subheader.html
│       │   │   ├── summary.html
│       │   │   └── welcome.html
│       │   ├── post
│       │   │   └── single.html
│       │   ├── section
│       │   └── shortcodes
│       │       └── contact-form.html
│       ├── LICENSE
│       ├── README.md
│       ├── static
│       │   ├── favicon.ico
│       │   ├── humans.txt
│       │   ├── images
│       │   │   └── mangoose.jpeg
│       │   └── svg
│       │       ├── download-cloud.svg
│       │       ├── dribbble.svg
│       │       ├── folder.svg
│       │       ├── github.svg
│       │       ├── globe.svg
│       │       ├── heart.svg
│       │       ├── instagram.svg
│       │       ├── linkedin.svg
│       │       ├── map-pin.svg
│       │       ├── menu.svg
│       │       └── twitter.svg
│       └── theme.toml
```

Let's focus on the theme/hugo-theme-ava/layouts folder:

```bash
.
├── 404.html
├── _default
│   ├── baseof.html
│   ├── list.html
│   ├── page.html
│   └── single.html
├── index.html
├── partials
│   ├── dark-mode-toggle.html
│   ├── date.html
│   ├── footer.html
│   ├── google-analytics.html
│   ├── header.html
│   ├── icons.html
│   ├── og.html
│   ├── other-metas.html
│   ├── site-title.html
│   ├── subheader.html
│   ├── summary.html
│   └── welcome.html
├── post
│   └── single.html
├── section
├── shortcodes
│   └── contact-form.html
```
