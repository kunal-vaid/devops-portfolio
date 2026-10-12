# Upwork Portfolio Starter Pack

Built for you on Oct 7, 2026 — real, working code samples to link from your
Upwork profile's portfolio section, so clients see code instead of just claims.

## What's inside

- **`helm-charts/webapp/`** — a production-ready Helm chart: Deployment with
  rolling updates, Service, Ingress (TLS-ready), HPA autoscaling, ConfigMap,
  hardened security defaults (non-root, read-only root FS, resource limits).
- **`ansible-roles/webapp/`** — an idempotent Ansible role that provisions a
  Linux host and deploys a web app behind nginx: multi-OS support, handlers
  (reload not restart), Jinja2 templates, `nginx -t` validation, log rotation.
- **`proposal-template.md`** — a reusable proposal skeleton. Fill the
  [BRACKET]s per gig, keep it short, attach this repo's link on fixed-price
  jobs.

## Get it onto GitHub (10 minutes)

1. Go to github.com/new, name the repo `devops-portfolio` (public).
2. In a terminal:

```bash
cd upwork-portfolio
git init
git add .
git commit -m "DevOps portfolio samples: Helm chart + Ansible role"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/devops-portfolio.git
git push -u origin main
```

3. On Upwork: profile → Portfolio → **+ Add project** → paste the GitHub repo
   URL for the Helm chart and again for the Ansible role, with a one-line
   description of what each demonstrates.

## Before you apply — the review checklist

From the profile review: **buy Connects first** (0 = you can't submit a single
proposal), set hours to "Less than 30 hrs/week", raise the $50/hr rate, fix the
Fujitsu job title to match your K8s story, add Helm/Python/CI-CD skills, list
your OCP + ITIL V3 certs, and verify your ID.

## Notes

- The samples are real and reviewed for syntax, but they're portfolio demos —
  read them through once before linking, and swap in any real work details
  (project names, environments) that make them yours.
- Don't commit secrets. There are none in here.
