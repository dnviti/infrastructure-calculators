# infrastructure-calculators

Small, self-contained planning tools for infrastructure sizing, published as a
static GitHub Pages site: <https://dnviti.github.io/infrastructure-calculators/>

## Calculators

- **Proxmox + Ceph capacity calculator** —
  `proxmox/ceph/proxmox-ceph-capacity-calculator.html`. Raw capacity, what
  Ceph keeps after protection, and how much you can fill before the cluster
  stops accepting writes. Single file, no build step, works offline except for
  the Google Fonts request.

## Deploying

Deployment is manual on purpose:

1. Go to **Actions** → **Deploy GitHub Pages** → **Run workflow** → **Run workflow**.
2. Wait for the two jobs (`build`, `deploy`) to finish.

The workflow assembles the static site into `_site/` and publishes it with the
official `actions/upload-pages-artifact` + `actions/deploy-pages` actions.
GitHub Pages must be configured with **Source: GitHub Actions**
(Settings → Pages), which is how this repository is set up.

No changes to `main` deploy automatically — only explicit manual runs do.

## Adding a calculator

Drop a self-contained HTML file anywhere in the repository, link it from
`index.html`, and run the workflow. The deploy job copies `index.html` and the
`proxmox/` tree; if a new calculator lives elsewhere, add a line to the
"Assemble static site" step in `.github/workflows/deploy-pages.yml`.
