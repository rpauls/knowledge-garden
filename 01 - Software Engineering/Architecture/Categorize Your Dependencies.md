---
type: Article
tags:
  - node
  - frontend
  - backend
  - dependencies
  - project-structure
created: 2025-10-25 - 19:26
updated: 2025-10-25 - 19:26
---
# Categorize Your Dependencies

## Summary

The article proposes moving beyond the traditional `dependencies` / `devDependencies` split in `npm` by using `pnpm` catalogs to group packages into more meaningful categories (e.g., runtime, build‑time, framework, UI, testing). This finer granularity improves version management, makes upgrades clearer, and aids code reviews, especially in monorepos where different parts of a project have distinct needs. The author demonstrates how to define catalogs in `pnpm-workspace.yaml`, add comments for context, and reference them in `package.json`. While catalogs are still evolving and tooling support is limited, the approach offers a flexible way to capture the true purpose of each dependency, reducing noise in the manifest and fostering better collaboration. The article encourages developers to experiment with this method and contribute to its tooling ecosystem.

## Key Points

- **Beyond `dependencies` vs `devDependencies`** 
	- Traditional npm fields can’t express the many roles a package plays (runtime, build‑time, UI, testing, etc.).
- **pnpm catalogs** 
	- Introduce named catalogs in `pnpm-workspace.yaml` (e.g., `catalog:runtime`, `catalog:test`) and reference them in `package.json` via `catalog:<name>`.
- **Improved version visibility** 
	- Each catalog groups related packages, so upgrading a whole category (e.g., all UI libs) becomes a single, intentional change.
- **Cleaner manifests** 
	- Removing unrelated entries from `dependencies` reduces noise, making it easier for newcomers to see what truly matters for production.
- **Team communication** 
	- Comments can be added to `pnpm-workspace.yaml` to explain why a package lives in a particular catalog, fostering shared context.
- **Monorepo friendliness** 
	- Catalogs let different workspaces within a monorepo declare only the subsets they need, avoiding accidental coupling.
- **Tooling gaps** 
	- Current IDEs and lock‑file viewers don’t fully understand catalogs yet, so you may lose quick version glances in `package.json`. Expect ecosystem support to evolve.
- **Adoption strategy** 
	- Start by identifying high‑impact groups (e.g., framework, bundler, testing) and migrate those packages to catalogs; iterate as tooling improves.
- **Future‑proofing** 
	- As projects grow, catalogs provide a scalable way to add new dimensions (e.g., security‑related libs, experimental features) without proliferating custom fields.

## Subtopics

...

## Personal Thoughts

...

## Examples

...

## Related Content


- https://antfu.me/posts/categorize-deps

