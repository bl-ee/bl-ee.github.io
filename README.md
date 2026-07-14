# bl-ee.github.io

Brian W. Lee's research homepage and technical notes, built with
[Quarto](https://quarto.org/).

## Local development

Check the Quarto installation and start a local preview:

```bash
quarto check
quarto preview
```

The preview includes draft notes and marks them with a draft banner.

## Production render

Render the complete production site:

```bash
quarto render
```

The generated site is written to `_site/`. This directory is ignored and
should not be committed.

## Create a new note

Copy the unpublished example note into a directory named for the note's URL
slug:

```bash
mkdir -p notes/<slug>
cp notes/example-note/index.qmd notes/<slug>/index.qmd
```

Then:

1. Replace the sample title, description, ISO date, and content.
2. Keep `draft: true` while writing.
3. Remove `draft: true` when publishing.
4. Include `{{< include /_macros.qmd >}}` when shared math macros are needed.
5. Run `quarto preview` before committing.

The example note is unpublished, but it is not private: its source is visible
in this public repository.

## Deployment

Pushes to `main` trigger `.github/workflows/publish.yml`, which renders the
site and deploys `_site/` as a GitHub Pages artifact. In the repository's
GitHub Pages settings, **Build and deployment → Source** must be set to
**GitHub Actions**.

If executable content later causes Quarto to create `_freeze/`, commit that
directory. Do not add `_freeze/` to `.gitignore`.