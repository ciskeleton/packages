# 🧩 CiSkeleton Packages

The official package distribution repository for the **CiSkeleton (CSK) framework**.

This repository brings together the source references, downloadable archives, and catalog metadata for official CSK packages. It supports independent package development while providing a centralized, reliable source for the CSK catalog and distribution system.

## 📂 Repository Structure

```text
packages/
├── packages/
│   ├── languages/       # Language package submodules
│   ├── modules/         # Module package submodules
│   ├── plugins/         # Plugin package submodules
│   └── themes/          # Theme package submodules
├── dist/
│   ├── languages/       # Downloadable language ZIP archives
│   ├── modules/         # Downloadable module ZIP archives
│   ├── plugins/         # Downloadable plugin ZIP archives
│   ├── themes/          # Downloadable theme ZIP archives
│   └── system/
│       ├── core.zip     # CSK core distribution
│       └── common.zip   # CSK shared assets distribution
├── metadata/
│   ├── languages/       # Language catalog metadata
│   ├── modules/         # Module catalog metadata
│   ├── plugins/         # Plugin catalog metadata
│   └── themes/          # Theme catalog metadata
├── allowlist.json       # Approved packages
├── README.md
└── LICENSE.md
```

The directory tree illustrates the intended organization. Individual package directories, archives, and metadata files are populated as packages are added.

## 📦 Package Sources

Packages are maintained in independent Git repositories and integrated into this repository as Git submodules.

Each package type has its own directory under `packages/`:

| Type | Directory | Description |
| :--- | :--- | :--- |
| Languages | `packages/languages/` | Language and translation packs |
| Modules | `packages/modules/` | Extensions that provide application functionality |
| Plugins | `packages/plugins/` | Integrations and additional capabilities |
| Themes | `packages/themes/` | Themes and presentation layers |

For example, the `pages` module is maintained in its own repository and referenced here as a submodule:

```text
packages/modules/pages/
```

This separation allows packages to be developed, versioned, and released independently of the central distribution repository.

Submodule references identify specific commits of their respective repositories. Updating a submodule therefore updates the referenced source revision rather than automatically tracking its latest commit.

## 📥 Distribution Archives

The `dist/` directory contains the ZIP archives served by the CSK catalog for package downloads.

Archives are organized by package type and use the package name as their filename.

| Package | Distribution Path |
| :--- | :--- |
| Pages module | `dist/modules/pages.zip` |
| OAuth plugin | `dist/plugins/oauth.zip` |
| Classic theme | `dist/themes/classic.zip` |
| English language | `dist/languages/english.zip` |
| CSK core | `dist/system/core.zip` |
| CSK common assets | `dist/system/common.zip` |

The same convention applies to all supported package types.

### System Distributions

The `dist/system/` directory is reserved for the framework's core distribution and shared assets.

Unlike ordinary extensions, these archives are not organized under the module, plugin, theme, or language directories.

- **`core.zip`** — the CSK core distribution.
- **`common.zip`** — shared assets used by the CSK ecosystem.

These archives are part of the distribution infrastructure and are maintained separately from ordinary extension packages.

## 🗂️ Catalog Metadata

The `metadata/` directory stores copies of package metadata independently of the corresponding source repositories.

Metadata is organized by package type and package name, allowing the catalog to retrieve package information without depending on the availability of the original repository.

For example:

```text
metadata/
├── languages/
│   └── english.json
├── modules/
│   └── pages.json
├── plugins/
│   └── oauth.json
└── themes/
    └── classic.json
```

The filenames above illustrate the naming convention; the actual files depend on the packages registered in the repository.

### Why Metadata Is Stored Separately

A package's metadata must remain available even if its source repository becomes private, is deleted, or is otherwise inaccessible.

Maintaining independent metadata copies allows the CSK catalog to continue displaying registered packages without relying on live requests to their original repositories.

The metadata directory is therefore a persistent catalog resource, not merely a temporary cache of upstream repository information.

Metadata should be updated when package information changes and validated before it is published to the catalog.

## ✅ Package Allowlist

The `allowlist.json` file defines the packages approved for inclusion in the CSK distribution and catalog.

A package's presence in an upstream repository or as a Git submodule does not, by itself, establish that it is approved for distribution.

Package registration and maintenance must ensure that:

- The package is explicitly approved.
- Its source reference points to the intended repository.
- Its distribution archive corresponds to the intended package version.
- Its catalog metadata is valid and available.
- Its licensing and distribution requirements are satisfied.

Only packages accepted into the distribution process should be exposed through the catalog.

The allowlist is an administrative control, not a substitute for verifying package integrity, ownership, or licensing.

## ⚙️ Distribution and Maintenance

This repository serves as the central coordination point for package distribution.

Its responsibilities include:

1. **Source references** — maintaining Git submodule references to independent package repositories.
2. **Distribution archives** — maintaining the ZIP files used for package downloads.
3. **Catalog metadata** — preserving the information needed to display packages in the CSK catalog.
4. **Package approval** — maintaining the allowlist of accepted packages.
5. **Distribution consistency** — ensuring that package references, archives, metadata, and approval records remain consistent.

These responsibilities are related but distinct. A package source, its downloadable archive, and its catalog metadata are separate resources and must be maintained accordingly.

Changes to one resource should not be assumed to update the others automatically.

## 🔗 Related Repositories

- **[CiSkeleton](https://github.com/ciskeleton)** — The framework organization.
- **[CSK Common](https://github.com/ciskeleton/common)** — shared assets for the CSK ecosystem.

Individual modules, plugins, themes, and language packs are maintained in their respective repositories.

## 📄 Licensing

This repository is licensed under the MIT License. The license applies to this repository's own content, including its original documentation and workflows.

It does not grant a blanket license to the packages it references or distributes. Individual packages may have their own licenses, terms, and redistribution requirements. The applicable package license governs the use of each package, subject to any other applicable permissions or agreements.

See [`LICENSE.md`](LICENSE.md) for the licensing terms applicable to this repository.

For licensing questions or additional permissions, contact **legal@ianhub.net**.

---

Maintained by **[Kader Bouyakoub](https://github.com/bkader)**, trading as **[Ianhub](https://www.ianhub.dz)** as part of the CiSkeleton ecosystem.
