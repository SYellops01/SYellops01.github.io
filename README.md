# Portfolio site

To make changes to the portfolio site, see below headings:

## 1. Customize your info

Almost everything on the home page that you need to change lives in **`_config.yml`**:

- `title` — your name
- `tagline` — your role (e.g. "Analytics Engineer")
- `email`, `linkedin`, `github`, `resume_url`
- `bio` — your "about me" paragraph
- `skills` — the chip list of selected skills under "About"

## 2. Edit or add projects

Each project is a file in `_client_projects/` or `_personal_projects/`.
To create a new project under either the 'Client Projects' or 'Personal Projects' section, duplicate an existing .md file in either of these

```yaml
title: "Project name"
subtitle: "Subtitle shown on the project page"
slug: project-name          # controls the URL: /projects/project-name/
model_name: "mart_something" # small mono label shown on the card
summary: "One sentence shown on the homepage card"
order: 1                     # controls display order on the homepage
thumbnail: thumbs/lineage-a.html  #the file path from root to the thumbnail you wish to use
stack: ["dbt", "SQL"]        # tech tags
demo_url: ""                 # optional live link
code_url: ""                 # optional GitHub repo link
```

The body of the file (below the `---`) is the write-up, in normal, which makes up the project page once clicked on.
Markdown — headings, lists, links all work.

To use a real screenshot in the write up, copy this into the markdown section.

## 3. Deployment on GitHub Pages

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
3. Once changes are pushed to 'main', select 'Actions' to view page deployment status. Once succeeded, load your GitHub page via the link.

## 4. (Optional) Custom domain

Buy a domain from any registrar, then in the same **Settings → Pages**
screen add it under "Custom domain." GitHub will give you DNS records
to add at your registrar — usually a CNAME record pointing at
`your-username.github.io`.
