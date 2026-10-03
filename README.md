# cataggar/arocc

A GitHub mirror of the Aro C frontend source required by Zig 0.17.

## Branches

- `zig17` mirrors the exact upstream commit
  `d0c8c4d9c55daa7ef6e40cf0f630a5b5e900989b` from
  [codeberg.org/ziglang/arocc](https://codeberg.org/ziglang/arocc).
- `master` retains the existing source from
  [Vexu/arocc](https://github.com/Vexu/arocc). The mirror workflow never changes it.
- `mirror` is the default, orphan branch containing only mirror automation and
  documentation. It does not modify upstream source or commit identities.

## Synchronization

The pinned `zig17` branch is synchronized daily at 5:25 AM Central Time
(`America/Chicago`, including daylight saving time). This deliberately does not
track Codeberg `master`, which has advanced to Zig 0.18 development.

To synchronize manually:

```sh
gh workflow run sync-zig17.yml --repo cataggar/arocc --ref mirror
```

The workflow can create the source branch on its first run. It uses Git protocol
v0, a bounded fetch, job-scoped write permissions, and an explicit destination
lease to refuse overwriting a concurrent update. Fetch failures fail the job;
they are not reported as successful synchronization. To advance the Zig 0.17
pin, update `UPSTREAM_COMMIT` in the workflow and this documentation together.
