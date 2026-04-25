# Workspace Instructions

## Lockfiles, Commits, Tags, And Releases
- Do not leave completed work uncommitted. After each coherent, validated change set, create a commit and push it in the same session.
- Use multiple commits and pushes when that keeps unrelated changes, partial validations, or follow-up fixes clearly separated. Prefer small, logically grouped commits over one mixed commit.
- This repo is asset-only and does not use a package-manager lockfile. Keep `.gitattributes` and Git LFS tracking rules correct when adding, replacing, or migrating large assets.
- Use lowercase annotated semver tags only. Do not invent ad-hoc labels such as `V1`, `torca-r07`, `pre-lfs-migration-*`, or similar one-off names.
- This repo follows the stable `v1.x` line. Stay on `v1` for routine work; only cut `v2` for an intentional breaking asset-delivery or repository-structure change.
- Before creating a new tag, check the latest tag in the active semver line and decide whether the new commit is still the same release milestone. If it is, move that existing tag forward to the new validated commit instead of minting a new version number.
- Keep the GitHub release aligned with that decision: when the commit still belongs to the same milestone, update or recreate the existing release so it points at the moved tag/current commit; only create a brand-new release when the change creates a genuinely new milestone.
- Cut a fresh semver tag and release only when the work crosses a real release boundary, such as a new deployable milestone, a materially different operator/user-facing state, or a version-line change that deserves its own notes and rollback point.
- Create an annotated tag when a curated asset set, public delivery structure, or LFS policy change is ready for downstream use.
- Create a GitHub release when that tag represents a named asset snapshot or delivery milestone that other repos or operators should consume. Release notes should summarize scope, validation, rollout notes, and any migration or recovery steps.
- If the existing tag or release history contains stale drafts, redundant entries, or ad-hoc labels, clean that history up instead of preserving clutter.
- Skip tags and releases for trivial doc-only edits, formatting-only changes, or routine housekeeping unless they change deployment, operations, or a consumer-facing contract.
- Do not publish releases for one-off asset drops or housekeeping unless they are part of a deliberate shipped snapshot.

## Dependency & Lockfile Discipline

- This repository currently has no package-managed build or lockfile. Do not invent dependency verification commands that cannot run here.
- If a `package.json`, workspace manifest, dependency range, lockfile, or dependency update tool is added later, treat the repo-root clean install path as the source of truth for deploy readiness.
- For npm-based additions, follow the root `npm ci` discipline: run `npm ci`, `npm run lint`, `npm run typecheck`, and `npm run build` from the repository root before committing package/dependency changes.
- If `npm ci` fails because `package.json` and `package-lock.json` are out of sync, run `npm install --package-lock-only --ignore-scripts --no-fund --no-audit`, rerun `npm ci`, and commit the lockfile with the related package change.
- Never commit or push dependency/package changes if the repo-root clean install fails.
