# Andrus Díaz Playground

The small public site at [playground.andrusdiaz.dev](https://playground.andrusdiaz.dev).
It is deliberately boring: editing one HTML file and pushing `main` updates the
site through Flux. There is no image build, registry, database, or server to
manage.

## Publish a change

1. Edit [`k8s/kaido/site/index.html`](k8s/kaido/site/index.html).
2. Preview it locally in a browser if useful.
3. Commit and push:

   ```powershell
   git add k8s/kaido/site/index.html
   git commit -m "Update playground"
   git push origin main
   ```

Flux checks `main` every minute and rolls the static Nginx pod when the HTML
changes. Expect a normal update to appear within about two minutes.

## Guardrails

This repository is public so Flux and collaborators such as Hermes can read it
without a deploy key. Do not add passwords, API keys, private URLs, or customer
data. The Flux identity for this repository is limited to its own Kubernetes
namespace and the namespace has restricted pod security, a resource budget, and
no outbound network access.

## Layout

- `k8s/kaido/site/index.html` — the page to change.
- `k8s/kaido/kustomization.yaml` — turns the page into a versioned ConfigMap.
- `k8s/kaido/app.yaml` — the small static Nginx Deployment and ClusterIP Service.
Fast GitOps playground for playground.andrusdiaz.dev
