# Versioning

## Scheme

| Branch / Version | Purpose |
|------------------|---------|
| `main`           | Development branch |
| `v1.1.0`         | First Mario fork release |
| `v1.2.0`, `v1.3.0`, … | Future releases |

## Semantic Versioning

- **Patch** (1.1.x) — bug fixes, no API change
- **Minor** (1.x.0) — new features, backward compatible
- **Major** (x.0.0) — breaking changes

## Bumping versions

1. Update `package.json` in root and `packages/*`.
2. Or run: `npm run bump` then `npm version 1.2.0 --no-git-tag-version` at root.
3. Commit and tag: `git tag v1.2.0`
4. Update README badge and version table.
