# Portfolio site

A clean, minimal Jekyll portfolio built for GitHub Pages. Themed around
data pipelines/lineage to fit an analytics engineering CV — swap the copy
and it works for any field.

## 1. Customize your info

Almost everything you need to change lives in **`_config.yml`**:

- `title` — your name
- `tagline` — your role (e.g. "Analytics Engineer")
- `email`, `linkedin`, `github`, `resume_url`
- `bio` — your about-me paragraph
- `skills` — the chip list under About

## 2. Edit or add projects

Each project is a file in `_projects/`. Two examples are included —
edit them directly, or duplicate one to add a third project. Front
matter fields:

```yaml
title: "Project name"
subtitle: "One-line subtitle shown on the project page"
slug: project-name          # controls the URL: /projects/project-name/
model_name: "mart_something" # small mono label shown on the card
summary: "One sentence shown on the homepage card"
order: 1                     # controls display order on the homepage
thumbnail: thumbs/lineage-a.html  # or lineage-b.html
stack: ["dbt", "SQL"]        # tech tags
demo_url: ""                 # optional live link
code_url: ""                 # optional GitHub repo link
```

The body of the file (below the `---`) is the write-up, in normal
Markdown — headings, lists, links all work.

To use a real screenshot instead of the abstract SVG diagrams, drop an
image in `assets/images/`, and in `_layouts/project.html` swap:

```liquid
{% include {{ page.thumbnail }} %}
```

for:

```liquid
<img src="{{ '/assets/images/your-image.png' | relative_url }}" alt="{{ page.title }}">
```

(and do the same on the homepage card in `index.html`).

## 3. Preview locally (optional)

Requires Ruby installed.

```bash
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000`.

## 4. Deploy on GitHub Pages

1. Create a new **public** GitHub repository named
   `your-username.github.io` (this exact naming gives you a free URL at
   `https://your-username.github.io`). If you'd rather use a project
   repo with a different name, that's fine too — your site will be at
   `https://your-username.github.io/repo-name/`, in which case also set
   `baseurl: "/repo-name"` in `_config.yml`.
2. Push this folder's contents to that repository:
   ```bash
   git init
   git add .
   git commit -m "Initial portfolio site"
   git branch -M main
   git remote add origin https://github.com/your-username/your-username.github.io.git
   git push -u origin main
   ```
3. In the repo on GitHub: **Settings → Pages → Build and deployment →
   Source**, select **Deploy from a branch**, branch `main`, folder
   `/ (root)`. Save.
4. Wait a minute or two, then visit `https://your-username.github.io`.

## 5. (Optional) Custom domain

Buy a domain from any registrar, then in the same **Settings → Pages**
screen add it under "Custom domain." GitHub will give you DNS records
to add at your registrar — usually a CNAME record pointing at
`your-username.github.io`.
