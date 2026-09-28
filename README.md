# JShaw Lab website

A minimal Jekyll site for the JShaw Lab, built to be edited without touching
any HTML/CSS for day-to-day updates.

## Editing content

Everything you'll routinely change lives in plain text/YAML files:

| To change...                          | Edit...                       |
|----------------------------------------|--------------------------------|
| Lab name, tagline, contact info, nav   | `_config.yml`                 |
| Accent color                           | `accent_color` in `_config.yml`|
| Homepage hero photo                    | `hero_image` in `_config.yml` |
| Team members + photos                  | `_data/team.yml`               |
| Publications                           | `_data/publications.yml`       |
| Software projects + colors             | `_data/software.yml`           |
| Research overview text (homepage)      | `index.md`                     |
| How-to-join text                       | `join.md`                      |

### Trying a different accent color

Open `_config.yml` and change `accent_color` to any hex code — that's it,
no CSS file to touch. It drives the active nav underline, links, the "View
all publications" link, buttons, and the software-page color dots. A few
tested-looking options are listed right above the setting in `_config.yml`
(a couple of blues, a salmon, a dusty rose, sage, brick red) — paste one in,
save, and refresh your local preview (see below) to compare before you
commit.

### Adding a homepage photo

Drop an image (lab group photo, a building, you — anything roughly
1600x900 or wider works well) at `assets/img/hero.jpg`, then set:

```yaml
hero_image: "assets/img/hero.jpg"
hero_image_caption: "Optional caption shown under the photo"
```

in `_config.yml`. Leave `hero_image` blank to hide it again.

### Adding a team member

1. Drop a square-ish photo (min. ~400x400px) into `assets/img/team/`.
2. Add a new entry to `_data/team.yml`, following the example block already
   in that file.
3. Commit and push.

### Adding a publication or software tool

Copy an existing entry in `_data/publications.yml` or `_data/software.yml`
and edit the fields. No other file needs to change — both pages and the
homepage's "Recent Publications" list render automatically from this data.
For software, `color` sets that tool's identifying dot/accent, and
`publication` (optional) adds a small standardized "venue, year" note
linking to the paper — omit it for tools with nothing published yet.

## Previewing locally

```bash
export GEM_HOME="$HOME/gems"; export PATH="$HOME/gems/bin:$PATH"  # already in ~/.bashrc
bundle exec jekyll serve --livereload
```

Then open http://localhost:4000. Every save auto-rebuilds and refreshes the
page for you.

## Deploying

This repo is meant to be named `<username>.github.io` (or configured as a
project site) and served directly by GitHub Pages — just push to `main`.
No build step, no GitHub Actions workflow needed.
