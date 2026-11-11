# Lourdes Madero Psicología

Static website built with [Zola](https://www.getzola.org/) (tested with 0.19).

## Run it

```sh
zola serve   # preview at http://127.0.0.1:1111, reloads on every change
zola build   # writes the final site to public/
```

## Where things are

| File | What it contains |
| --- | --- |
| `config.toml` | Site title, description and **contact details** (WhatsApp, email, address). |
| `content/_index.md` | **Home page**: page title and hero text, plus the "Conóceme" Markdown. |
| `content/cita.md` | The quote shown on the home page. |
| `content/especialidades/` | "En qué me especializo": one folder per item (name and icon). |
| `content/servicios/` | The "Servicios" page, published at `/servicios/` (the old `/programas/` URL redirects there). Its `_index.md` holds the page title, subtitle and the "La primera sesión" text; its sub-folders are the services (name, duration, **price**, image), shown as cards on the home page and in "Formatos y tarifas" on `/servicios/`. The text in each service folder is its description on `/servicios/`; `image` is only used by the home cards. |
| `content/opiniones/` | Testimonials: one folder per person (name and text). |
| `content/acerca-de.md` | The "Sobre mí" page, in Markdown. |
| `templates/base.html` | Layout shared by every page: header, menu and the contact footer. |
| `templates/index.html` | Layout of the home page. |
| `templates/page.html` | Layout of single pages (used by "Sobre mí"): the `[extra] image` on the left, the text on the right. |
| `templates/servicios.html` | Layout of the "Servicios" page: same look as "Sobre mí", plus the price list. |
| `sass/` | The styles, written in Sass. Zola compiles `sass/style.scss` to `/style.css`. Colours, font and sizes are in `sass/_tokens.scss`; the other files are one per part of the site (header, home, page, footer). |
| `static/fonts/raleway/` | The Raleway font, hosted with the site (no Google Fonts requests). `OFL.txt` is its licence. |
| `static/images/` | Photos and icons. |

Rule of thumb: **text lives in `content/`, layout lives in `templates/`**.

`content/cita.md`, the `especialidades/` and `opiniones/` folders and the
service sub-folders in `servicios/` are content only: they have `render = false`,
so they are not published as pages of their own (`servicios/_index.md` itself is
the published "Servicios" page). Any template can reuse them with `get_section` (folders)
or `get_page` (`cita.md`). Items in a folder are shown in order of their `weight`.

## Common edits

- **Change a price**: edit `price` in `content/servicios/<service>/_index.md`.
- **Change a service description**: edit the text below the closing `+++` in
  `content/servicios/<service>/_index.md`.
- **Change a page's photo**: edit `image` (a file in `static/images/`) and
  `image_alt` under `[extra]` in `content/acerca-de.md` or
  `content/servicios/_index.md`.
- **Add a testimonial**: copy a folder in `content/opiniones/`, then edit its
  `title` (the author), `weight` (its position) and the text. Keep
  `render = false`: without it Zola publishes an empty placeholder page.
- **Change phone or email**: edit `[extra]` in `config.toml`. The "Hablemos" and
  "Escríbeme por WhatsApp" buttons open a WhatsApp chat with the `whatsapp` number.
- **Change a colour**: edit `sass/_tokens.scss`; every page picks it up.
- **Add a new page**: create `content/new-page.md` with a `title`; it will be
  published at `/new-page/` using `templates/page.html`.
