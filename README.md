# 🧩 CSK Packages

This repository serves as the **central monorepo** for all **CiSkeleton (CSK)** packages — including modules, plugins, themes, and language packs.

Each package is managed as a **Git submodule**, enabling independent development, versioning, and distribution — while maintaining a unified structure for automation, updates, and releases.

## 🗂️ Repository Structure

Packages are organized by type:

```
packages/
├──languages
├──modules/
├──plugins/
└──themes/
```

Each subfolder contains Git submodule references to official CSK packages. Some packages may be private or access-restricted.

| Type      | Description                                  | Access |
| :-------- | :------------------------------------------- | :----: |
| Languages | Translation packs                            |   🔒   |
| Modules   | Extend core functionality (e.g., Blog, Shop) |   🔒   |
| Plugins   | Add features or integrations                 |   🔒   |
| Themes    | Frontend themes                              |   🔒   |

## 🛠️ Purpose

* Keep all official CSK extensions organized in one place.
* Provide a base for the CSK **in-app Marketplace**.
* Simplify updates, packaging, and distribution pipelines.
* Serve as a package index for automation, release tooling, and marketplace metadata.

## ⚙️ Automation
A package repository needs three things to work with this ecosystem:

1. **Repo variables** (Settings → Variables → Actions):
  - `CSK_NAME` → name of the package (e.g., `pages`).
  - `CSK_TYPE` → type of the package (`module`, `plugin`, `theme`, `language`).
2. **A `release.yml` workflow** that calls the shared release workflow on every stable tag:
```yml
name: Release
run-name: Release ${{ github.ref_name }} by @${{ github.actor }}

on:
 push:
   tags:
     - '*.*.*'
     - '!*alpha*'
     - '!*beta*'

jobs:
 release:
   if: >
     startsWith(github.ref, 'refs/tags/') &&
     !contains(github.ref_name, 'alpha') &&
     !contains(github.ref_name, 'beta') &&
     !contains(github.ref_name, '+')
   uses: ciskeleton/.github/.github/workflows/package.yml@main
   with:
     name: ${{ vars.CSK_NAME }}
     type: ${{ vars.CSK_TYPE }}
```
This builds the ZIP and publishes it as a GitHub Release on every stable SemVer tag — no secrets required, entirely self-contained to your own repository.
3. **An entry in `allowlist.json`** in this repository, added by the CSK maintainer after review. This is what actually gets a package into the catalog — steps 1–2 alone just make your repo *capable* of releasing correctly, they don't add it anywhere.

To be eligible for the allowlist, a package must:

- Be **public** — the scheduled job here checks allow-listed repos with no installed credentials, so private repos can't be picked up.
- Tag stable SemVer releases (`x.y.z`, no `alpha`/`beta`) and publish each as a GitHub Release with a `<name>-<version>.zip` asset.
- Include a valid `metadata.json` at the repo root (title, description, screenshots, etc.) — packages without one are skipped from the catalog entirely.

Once your package meets these, contact maintainers with a link to your repository for review. If accepted, it's added to `allowlist.json` and picked up automatically on its next release.

> 🪄 A scheduled job in this repository checks every allow-listed package for new releases, downloads and verifies them, and updates the registry — fully decoupled from each package's own repository.

---

## Example
| Type | Example Repo | `CSK_NAME` | `CSK_TYPE` | Added Under |
| :--- | :----------: | :--------: | :--------: | :---------------------------- |
| Language | `lang-english` | `english` | `language` | `packages/languages/english` |
| Module | `module-pages` | `pages` | `module` | `packages/modules/pages` |
| Plugin | `plugin-oauth` | `oauth` | `plugin` | `packages/plugins/oauth` |
| Theme | `theme-classic` | `classic` | `theme` | `packages/themes/classic` |

---

> 🚀 CSK uses this monorepo to build update bundles and power its in-app marketplace.


## 🔗 Related Repositories

* [`core`](https://github.com/ciskeleton/core) — Main CSK Framework *(Private)*
* [`common`](https://github.com/ciskeleton/common) — CSK Shared Assets *(Public)*
* [`projects`](https://github.com/ciskeleton/projects) — All CSK projects *(Public index)*

---

> This repository is part of the **Ianhub CSK ecosystem**. Most submodules are private, but their structure and organization are visible for transparency and documentation.

---

## Licensing

This repository acts as a public index for CiSkeleton (CSK) packages.

The repository itself does not grant usage rights to the packages listed here. Each package, module, plugin, theme, or language pack is governed by its own license, terms, or access policy.

Some packages may be private or proprietary. Public visibility of this index, its folder structure, or its Git submodule references does not imply that the listed packages are open source or freely redistributable.

Third-party components used by individual CSK packages remain governed by their own respective licenses. Those notices should be included in the package or project that directly bundles or distributes them.

---

For licensing questions or additional usage rights, contact: **legal@ianhub.net**
