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
New packages register themselves automatically when they define:
- `CSK_NAME` variable → name of the package (e.g., `pages`).
- `CSK_TYPE` variable → type of the package (`module`, `theme`, etc.).
- `IANHUB_AGENT_CLIENT_ID` and `IANHUB_AGENT_PRIVATE_KEY` → for communication.

> 🪄 This system allows decentralized development while maintaining a synchronized ecosystem.

---

## Example
| Type | Example Repo | `CSK_NAME` | `CSK_TYPE` | `IANHUB_AGENT_*` | Added Under |
| :--- | :----------: | :--------: | :--------: | :--------------: | :---------- |
| Language | `lang-english` | `english` | `language` | `<secrets>` | `packages/languages/english` |
| Module | `module-pages` | `pages` | `module` | `<secrets>` | `packages/modules/pages` |
| Plugin | `plugin-oauth` | `oauth` | `plugin` | `<secrets>` | `packages/plugins/oauth` |
| Theme | `theme-classic` | `classic` | `theme` | `<secrets>` | `packages/themes/classic` |

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
