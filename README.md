# knowledge-base

STEM definitions, concepts, code snippets to help understand and grasp the abstract & concrete world around.

Published with [Docusaurus](https://docusaurus.io/) to GitHub Pages:
**https://kritchie.github.io/knowledge-base/**

## Write a note

Notes are MDX files under [`docs/`](docs/). The sidebar is generated from the
folder tree ([`sidebars.ts`](sidebars.ts)), so there is no index to maintain.

```
docs/
  intro.mdx              # landing note
  concepts/              # one idea per page
  snippets/              # runnable code + why
```

Front matter: `title`, `description`, optional `sidebar_position`, `tags`.
Folder label and order come from `_category_.json`.

Available in every page:

| Feature | Syntax | Plugin |
| --- | --- | --- |
| Math | `$inline$`, `$$block$$` | [remark-math](https://github.com/remarkjs/remark-math) + [rehype-katex](https://github.com/remarkjs/remark-math/tree/main/packages/rehype-katex) |
| Diagrams | ` ```mermaid ` fence | [@docusaurus/theme-mermaid](https://docusaurus.io/docs/markdown-features/diagrams) |
| Admonitions | `:::tip` | [built-in](https://docusaurus.io/docs/markdown-features/admonitions) |

## Local development

```bash
npm install
npm start        # dev server, hot reload, http://localhost:3000/knowledge-base/
npm run build    # production build into build/
npm run serve    # serve the production build
npm run typecheck
```

Node >= 20.

## Deployment

Push to `main` runs [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml):
build, upload artifact, deploy with
[`actions/deploy-pages`](https://github.com/actions/deploy-pages).
Pull requests run [`.github/workflows/test-deploy.yml`](.github/workflows/test-deploy.yml)
(typecheck + build, no deploy).

One-time repository setup: **Settings > Pages > Build and deployment > Source =
GitHub Actions**. No `gh-pages` branch is used.

> Ref: [Docusaurus deployment guide](https://docusaurus.io/docs/deployment#deploying-to-github-pages)
> — GitHub Actions artifact flow chosen over `npm run deploy`, which pushes a built
> `gh-pages` branch from a developer machine and needs a personal token in CI.
