# Build TechDocs action

This action builds [TechDocs](https://backstage.io/docs/features/techdocs/techdocs-overview) out of markdown for use in the [Backstage](https://backstage.io/) developer portal. See [Creating and Publishing](https://backstage.io/docs/features/techdocs/creating-and-publishing) for instructions on the input format of documentation. This action will produce HTML output into the `site` folder that can for example be published on [Github Pages](https://pages.github.com/).

## Example usage

The example below checks out the repository (including your documentation), generates TechDocs and then publishes these to Github Pages.

```
on: [push]

jobs:
  build_techdocs_job:
    runs-on: ubuntu-latest
    name: A job to build TechDocs
    steps:
    - name: Checkout main
      uses: actions/checkout@v1
    - name: Build TechDocs
      uses: erikxiv/techdocs-action@v1
    - name: Deploy to GitHub Pages
      uses: crazy-max/ghaction-github-pages@v2
      with:
        target_branch: gh-pages
        build_dir: site
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```