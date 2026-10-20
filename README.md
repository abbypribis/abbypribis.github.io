# abbypribis.github.io

Personal academic page for Abigail Linda Pribisova, served at
<https://abbypribis.github.io>.

Built with [pandoc](https://pandoc.org) from the
[basicpage](https://github.com/basicpage/basicpage.github.io) template (MIT).

## Layout

| Path                  | What it is                                           |
| --------------------- | ---------------------------------------------------- |
| `src/index.md`        | All page content and metadata. This is what you edit. |
| `pandoc/`             | HTML template and Lua filters.                        |
| `website/`            | Everything served: CSS, images, `files/cv.pdf`.       |
| `website/index.html`  | Generated, gitignored. Never edit by hand.            |

## Editing

Content lives in `src/index.md`. The YAML header sets the title, picture,
contact details and the icon links (CV, ORCID, Scholar, LinkedIn); commenting a
line out removes that item from the page.

Publications are fenced ` ```json {.paper} ` blocks. Education entries use a
`[Location (Years)]{.cv-meta}` span, which floats right on wide screens and
stacks on narrow ones.

## Previewing locally

Requires pandoc (`brew install pandoc`). Build, then serve:

    make website
    python3 -m http.server 8000 --directory website

Open <http://localhost:8000>. After an edit, re-run `make website` and refresh.

Note that browsers cache `style.css` aggressively: after changing CSS, use a
hard reload (⌘⇧R) or tick "Disable cache" in the DevTools Network tab.

## Deploying

Pushing to the default branch triggers `.github/workflows/webpage.yaml`, which
runs pandoc in a container and publishes `website/` to GitHub Pages. This needs
Settings → Pages → Source set to **GitHub Actions**.
