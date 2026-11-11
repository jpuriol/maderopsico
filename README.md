# Lourdes Madero Psicología

Static website built with [Zola](https://www.getzola.org/) (tested with 0.19).

```sh
zola serve   # preview at http://127.0.0.1:1111, reloads on every change
zola build   # writes the final site to public/
```

## How it works

Each page is one Markdown file in `content/`. The text below the closing `+++`
is the page's main text; everything else the page shows (photo, subtitle, and
lists such as services or testimonials) is in the front matter above it. Each
page has its own template, and two Sass files hold all the styles: one with the
values (colours, sizes, spacing), one with the rules.

| File | What it contains |
| --- | --- |
| `config.toml` | Site title, description, contact details |
| `content/_index.md` | Home: hero, quote, specialties, testimonials (front matter) + "Conóceme" (body) |
| `content/acerca-de.md` | "Sobre mí" |
| `content/servicios.md` | "Servicios": the services (front matter) + intro text (body) |
| `templates/base.html` | `<head>`, header, `{% block content %}`, footer |
| `templates/index.html` | The home page |
| `templates/acerca-de.html` | The "Sobre mí" page |
| `templates/servicios.html` | The "Servicios" page |
| `sass/_variables.scss` | Colours, font sizes, spacing, widths |
| `sass/style.scss` | Every rule, in page order |
| `static/` | Photos, icons and the Raleway font (`OFL.txt` is its licence) |

## Common edits

- **Change text**: edit the page's file in `content/`.
- **Change a price**: edit `price` in `content/servicios.md`; the home page
  cards read the same list.
- **Add a testimonial**: copy an `[[extra.testimonials]]` block in
  `content/_index.md` and change `author` and `text`.
- **Change a photo**: put the file in `static/images/` and set `image` and
  `image_alt` in that page's front matter.
- **Change contact details**: edit `[extra]` in `config.toml`.
- **Change a colour or spacing**: edit `sass/_variables.scss`.

## Add a page

Create `content/x.md` with a `title` and `template = "x.html"`, write that
template (copy `templates/acerca-de.html`), and add a menu link in
`templates/base.html`. The page is published at `/x/`.
