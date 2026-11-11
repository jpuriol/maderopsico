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
| `content/servicios/` | "Servicios": one folder per service (name, duration, **price**, image). |
| `content/opiniones/` | Testimonials: one folder per person (name and text). |
| `content/acerca-de.md` | The "Sobre mí" page, in Markdown. |
| `templates/base.html` | Layout shared by every page: header, menu and the contact footer. |
| `templates/index.html` | Layout of the home page. |
| `templates/page.html` | Layout of single pages (used by "Sobre mí"). |
| `sass/` | The styles, written in Sass. Zola compiles `sass/style.scss` to `/style.css`. Colours, font and sizes are in `sass/_tokens.scss`; the other files are one per part of the site (header, home, page, footer). |
| `static/fonts/raleway/` | The Raleway font, hosted with the site (no Google Fonts requests). `OFL.txt` is its licence. |
| `static/images/` | Photos and icons. |

Rule of thumb: **text lives in `content/`, layout lives in `templates/`**.

`content/cita.md` and the `especialidades/`, `servicios/` and `opiniones/`
folders are content only: they have `render = false`, so they are not published
as pages of their own. Any template can reuse them with `get_section` (folders)
or `get_page` (`cita.md`). Items in a folder are shown in order of their `weight`.

## Common edits

- **Change a price**: edit `price` in `content/servicios/<service>/_index.md`.
- **Add a testimonial**: copy a folder in `content/opiniones/`, then edit its
  `title` (the author), `weight` (its position) and the text. Keep
  `render = false`: without it Zola publishes an empty placeholder page.
- **Change phone or email**: edit `[extra]` in `config.toml`. The "Hablemos" and
  "Escríbeme por WhatsApp" buttons open a WhatsApp chat with the `whatsapp` number.
- **Change a colour**: edit `sass/_tokens.scss`; every page picks it up.
- **Add a new page**: create `content/new-page.md` with a `title`; it will be
  published at `/new-page/` using `templates/page.html`.
