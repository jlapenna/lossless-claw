---
name: lossless-claw-source-dev
description: Maintain lossless-claw fork source, repository documentation and agent guidance with local ownership, evidence and runtime boundaries.
---

# Fork source maintenance

Read [AGENTS.md](../../../AGENTS.md) and [RELEASING.md](../../../RELEASING.md).
`src/db/config.ts` owns runtime configuration, `openclaw.plugin.json` owns host
schema/UI hints and docs/configuration.md owns the full reference. Bundled
`skills/lossless-claw/references/` owns operator context; keep it aligned with
those contracts rather than creating a separate option authority.

For code changes, use the existing package-scoped test/typecheck/build scripts
and focused tests at the changed boundary. `npm run release:verify` owns the
full release gate and is not a request to publish. Documentation maintenance
checks links, frontmatter and source consistency. Answer the Changeset question
in every PR: this internal maintainer-context change requires no npm release
note or compatibility/version bump. A future user-visible or compatibility
change follows the root guide's Changesets and declaration-sync rules.

Lossless preservation is an invariant: automatic repair or compaction never
grants deletion of user data. A source test does not prove a gateway loaded the
plugin, a summary is faithful or a user record survived a live migration. Keep
sessions, transcripts and credentials private; do not invoke doctor repair,
cleanup, migration, gateway restart or package publication for source upkeep.

## Repository delivery

Inspect the actual remotes, default branch and target GitHub repository before
publication. This task updates `jlapenna/lossless-claw`; ownership of a fork does not
authorize an upstream merge. Use a dedicated feature worktree from the freshly
fetched configured base, preserving other branches and sessions. Read
[worktree-hygiene](https://github.com/jlapenna/repo-tools/blob/main/plugins/repo-tools/skills/worktree-hygiene/SKILL.md)
and [land-pr](https://github.com/jlapenna/repo-tools/blob/main/plugins/repo-tools/skills/land-pr/SKILL.md)
for normal checked delivery and cleanup; never bypass protection or hooks.

## Harness upkeep

Use the [shared harness-maintenance workflow](https://github.com/jlapenna/repo-tools/blob/main/plugins/repo-tools/skills/harness-maintenance/SKILL.md), adapted from
[Ryan Lopopolo's field guide](https://github.com/lopopolo/harness-engineering/tree/226c8d35fb6ea3ed55467753dba6dea2b5fd5778). Corroborate observed failures and
repair their earliest owner, keeping the root guide a route and conditional
procedures in references. Preserve current contracts separately from chronology.
A source check proves structure or consistency; comparable fresh use is required
to claim improved agent behavior. Keep fork decisions local and refer to shared
implementations rather than copying them across repositories.
