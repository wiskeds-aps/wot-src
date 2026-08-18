# wot-src (fork)

This branch (`automation`) exists only to host the auto-sync workflow and is
set as this fork's **default branch** deliberately — it holds no game
source, and unlike the mirrored branches below it is never overwritten.

The actual decompiled client source lives on these branches, each kept as
an exact, force-synced mirror of the corresponding branch in the upstream
repo, [izeberg/wot-src](https://github.com/izeberg/wot-src):

- `EU`, `NA`, `ASIA`, `CN`, `CT`, `PT_RU`, `RU`

## Auto-sync

`.github/workflows/sync-upstream.yml` runs on a schedule (every 6 hours)
plus on manual dispatch. For each branch above it:

1. Hard-resets it to match upstream (`gh repo sync --force`).
2. If anything changed, opens a GitHub issue on this repo summarizing what
   changed (commit count, file list, compare link).

It lives here specifically so a real hard-reset sync of the source
branches can never delete it — a source branch is a pure, disposable
mirror of upstream and must never carry commits of its own.
