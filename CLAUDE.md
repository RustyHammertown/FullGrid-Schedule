# ⛔ STOP — this is GENERATED OUTPUT, do not edit by hand

This repo (`FullGrid-Schedule`) is the **published artifact** the FullGrid app
reads at runtime (`schedule.json`, `series.json`, `standings.json`,
`circuits.json`, `session-groups.json`, `series-groups.json`, `sources.json`,
`tags.json`, `broadcasts.json`). **Every one of these files is regenerated from
source on every push** to the `fullgrid` repo by a GitHub Action
(`publish-schedule.yml`). So:

- **Editing a `*.json` file here is futile** — the next push to `fullgrid`
  re-exports it from `fullgrid/src/` and overwrites your change. (This has bitten
  us: a hand-edited `schedule.json` broadcast was wiped minutes later by an
  unrelated source push.)
- **Make the change in the `fullgrid` repo instead**, then push there; the
  Action publishes here automatically.

## Where things actually live (in the `fullgrid` repo, `src/`)

| You want to change… | Edit in `fullgrid/src/` |
|---|---|
| Series metadata: label, color, broadcast/where-to-watch, `notTelevisedCategories`, `resultsUrl`, tags | `theme.ts` → `SERIES` |
| Events, sessions, times, per-session broadcasts | `data.ts` |
| Standings / points | `standings.ts` |
| Series-tab buckets | `seriesGroups.ts` |
| Practice/Qualifying toggle groups | `theme.ts` → `SERIES_SESSION_GROUPS` |
| Sources / links / socials | `sources.ts` |
| Circuit coords / info | `circuits.ts` / `circuit_info.ts` |
| Tag taxonomy | `tags.ts` |
| Broadcaster → URL map | `broadcasts.ts` |

**Every series in the app IS defined in `fullgrid/src/theme.ts` `SERIES`.** If you
ever conclude a series "isn't in the seed / only exists in this JSON", you are in
the WRONG repo — open `fullgrid` and `grep` for it (use the series **id**, e.g.
`ginettagta`, not a guessed name like `ginetta`). Verify with `grep`/read before
claiming anything is missing; do not guess.

Read `fullgrid/CLAUDE.md` for the full workflow.
