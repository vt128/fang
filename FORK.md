# Narrow nb1 runtime fork

This branch uses the actual Fang renderer. It is not a reimplementation of
Fang's help or error appearance.

- Upstream: [charmbracelet/fang](https://github.com/charmbracelet/fang).
- Runtime baseline: official `v2.0.1`, commit
  `d89b30af5d6d3a6e3871631d0b62afe2e8c97739`.
- Background option backport: `85dfbaf2981e59cd9c331cfe239c575cc601d542`.
- Equivalent pure upstream change based on upstream main
  `e4b230db8d1536e25c644d19431e777d1e209b69`:
  `b5b71473471de436a3d1f1115d750338da800143` on `feat/upstream-explicit-background-20261117`.
  Proposed upstream in [PR #111](https://github.com/charmbracelet/fang/pull/111).
  The pull request is open; no upstream acceptance is claimed here.

`WithDarkBackground(true)` and `WithDarkBackground(false)` explicitly choose
a background and skip terminal detection before any query can run. Omitting
the option preserves upstream's default detection. The existing color scheme,
help/error renderer, signal options and execution lifecycle are unchanged.

A separate module-path adaptation changes this branch to
`github.com/vt128/fang/v2` and updates its own example and external test imports.
Consumers can pin the public commit's canonical Go pseudo-version through a
normal `require` directive. No upstream tags are rewritten and no general
replacement exception is needed in nb1's release checks.

The original `LICENSE.md` remains unchanged. `UPGRADE_GUIDE_V2.md` documents
upstream's historical module migration and is retained as upstream material.
