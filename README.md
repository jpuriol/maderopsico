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
| `content/_index.md` | **Home page text**: hero, quote, specialties, services (prices), testimonials. The Markdown at the bottom is the "Conóceme" section. |
| `content/acerca-de.md` | The "Sobre mí" page, in Markdown. |
| `templates/base.html` | Layout shared by every page: header, menu and the contact footer. |
| `templates/index.html` | Layout of the home page. |
| `templates/page.html` | Layout of single pages (used by "Sobre mí"). |
| `sass/` | The styles, written in Sass. Zola compiles `sass/style.scss` to `/style.css`. Colours, font and sizes are in `sass/_tokens.scss`; the other files are one per part of the site (header, home, page, footer). |
| `static/fonts/raleway/` | The Raleway font, hosted with the site (no Google Fonts requests). `OFL.txt` is its licence. |
| `static/images/` | Photos and icons. |

Rule of thumb: **text lives in `content/`, layout lives in `templates/`**.

## Common edits

- **Change a price**: edit `price` under `[[extra.services]]` in `content/_index.md`.
- **Add a testimonial**: copy one `[[extra.testimonials]]` block in `content/_index.md`.
- **Change phone or email**: edit `[extra]` in `config.toml`. The "Hablemos" and
  "Escríbeme por WhatsApp" buttons open a WhatsApp chat with the `whatsapp` number.
- **Change a colour**: edit `sass/_tokens.scss`; every page picks it up.
- **Add a new page**: create `content/new-page.md` with a `title`; it will be
  published at `/new-page/` using `templates/page.html`.
