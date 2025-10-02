# How to Configure MkDocs

## Basic Configuration

### Requirements

- MkDocs job file in `.github/workflows`
- MkDocs config file (`mkdocs.yml`) in the root of the project
- `docs` folder with at least `index.md` file

---

## Project Structure Example

```git
project-root/
└───.github/
    | workflows/
    | mkdocs-deploy.yml
    | ci.yml
|
│   mkdocs.yml
│   README.md
└───docs/
    │   index.md
    │   more pages...
```

---

## mkdocs.yml Example

```yaml
site_name: Your Project Name
theme:
  name: material
nav:
  - Home: index.md
  - Guide: page.md
```

---

## Local Development

To serve the documentation locally:

```powershell
mkdocs serve
```

---

## Deploying to GitHub Pages

1. Add a workflow file (e.g., `.github/workflows/mkdocs-deploy.yml`):
2. Example workflow:

```yaml
name: Deploy MkDocs
on:
  push:
    branches: [ main ]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.x'
      - run: pip install mkdocs mkdocs-material
      - run: mkdocs gh-deploy --force
```

---

## Useful Plugins

- `mkdocs-material`: Modern theme
- `mkdocs-awesome-pages-plugin`: Custom navigation
- `mkdocs-mermaid2-plugin`: Diagrams support

Install plugins with pip, then add to `mkdocs.yml` under `plugins:`.

---

## References

- [MkDocs Documentation](https://www.mkdocs.org/)
- [MkDocs Material](https://squidfunk.github.io/mkdocs-material/)
