# Movve Corporate Landing Page

Movve Corporate Landing Page is a Quasar/Vue single-page application for the Movve corporate wellness service. The page presents the brand, service offering, benefits, plans, mission, and contact channels for business leads.

## Project Overview

- Product name: Movve Corporativo
- Framework: Quasar 2 with Vue 3
- Build tool: Vite via `@quasar/app-vite`
- Router mode: hash
- Main output: static SPA files in `dist/spa`
- Local development host: `127.0.0.1`
- Local development port: `9000`
- Production URL: `https://robmoraes.github.io/movve-landingpage/`
- Production base path: `/movve-landingpage/`

## Requirements

Use a Node.js version supported by the project engines:

```bash
node --version
npm --version
```

The project supports Node `^22.12`, `^24`, `^26`, or `^28`.

## Install Dependencies

```bash
npm install
```

## Run Locally

Start the local development server:

```bash
npm run dev
```

The app runs at:

```text
http://127.0.0.1:9000
```

If port `9000` is already in use, stop the running process or change the dev server port in `quasar.config.js`.

## Quality Checks

Format source files:

```bash
npm run format
```

Run lint checks:

```bash
npm run lint
```

Build the production bundle:

```bash
npm run build
```

## Deployment

This project builds to a static SPA.

Generate the production build:

```bash
npm run build
```

Deploy the contents of:

```text
dist/spa
```

The current deployment target is the default GitHub Pages repository URL. Other static hosting platforms such as Netlify, Vercel, Cloudflare Pages, Nginx, or Apache can also serve the generated files, but the Quasar `publicPath` must match the final hosted path.

Because the project uses hash routing, no special server rewrite rule is required for route fallback. The generated `index.html` and asset files can be served directly from the web root.

For production builds, Quasar is configured with `publicPath: '/movve-landingpage/'` so generated assets resolve correctly under the default GitHub Pages repository path. Local development continues to use `/`.

### GitHub Pages Deployment

The publishing target for this repository is GitHub Pages using GitHub Actions at:

```text
https://robmoraes.github.io/movve-landingpage/
```

In the GitHub repository settings:

- Open `Settings > Pages`.
- Set `Source` to `GitHub Actions`.
- Keep HTTPS enforcement enabled.

The workflow file is:

```text
.github/workflows/deploy.yml
```

Current workflow:

```yaml
name: Deploy GitHub Pages

on:
  push:
    branches:
      - main

permissions:
  contents: read
  pages: write
  id-token: write

env:
  FORCE_JAVASCRIPT_ACTIONS_TO_NODE24: true

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v6

      - uses: actions/setup-node@v6
        with:
          node-version: 22

      - run: npm ci
      - run: npm run build

      - uses: actions/upload-pages-artifact@v5
        with:
          path: dist/spa

  deploy:
    needs: build
    runs-on: ubuntu-latest

    environment:
      name: github-pages

    steps:
      - uses: actions/deploy-pages@v5
```

If the repository is not rooted at this project folder, update the workflow commands with the correct `working-directory`.

### Optional Custom Domain Configuration

The current deployment uses the default GitHub Pages URL, not a custom domain. If a custom domain is enabled later, the intended production domain is:

```text
movvecorporativo.com.br
```

For GitHub Pages, configure the DNS hosted zone in AWS Route 53 with these records:

```text
movvecorporativo.com.br      A      185.199.108.153
movvecorporativo.com.br      A      185.199.109.153
movvecorporativo.com.br      A      185.199.110.153
movvecorporativo.com.br      A      185.199.111.153
www.movvecorporativo.com.br  CNAME  <github-user-or-org>.github.io
```

Replace `<github-user-or-org>` with the GitHub account or organization that owns the repository.

After creating the DNS records:

- Confirm that the Route 53 hosted zone is assigned to the domain registrar name servers.
- Wait for DNS propagation.
- Go back to `Settings > Pages` in GitHub.
- Confirm the custom domain as `movvecorporativo.com.br`.
- Enable `Enforce HTTPS` after GitHub completes certificate provisioning.

Optional verification commands:

```bash
dig movvecorporativo.com.br A
dig www.movvecorporativo.com.br CNAME
```

## Developer Contact

- Carlos R Moraes
- about.robmoraes.dev.br
