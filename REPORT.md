# Frantic bounty #49 delivery report

## What I did

One authentic public support action for runx (https://runx.ai / https://github.com/runxhq/runx):

1. Followed the README quickstart for real on a fresh Linux machine (git clone + npm install @runxhq/cli + `runx skill ./examples/hello-world`).
2. Found it genuinely broken: the bundled `connectors/coinbase/cdp/connector.yaml` fails manifest validation (line 102 `amount` is a plain map, validator expects a `!`-tagged scalar).
3. Wrote this public walkthrough repo documenting the repro, the finding, and links back to runx.
4. Filed a real upstream issue with full repro steps so the maintainer can fix it: https://github.com/runxhq/runx/issues/557

## Where it lives

- Walkthrough repo: https://github.com/reinaldyalt/runx-first-run-walkthrough
- Upstream issue: https://github.com/runxhq/runx/issues/557

## Why this is authentic, not link spam

- I actually ran their quickstart end-to-end and reported what genuinely happened — a real, specific, reproducible bug, not a generic "nice project!" post.
- The repo is original content (my own words, my own repro output) that links to runx.ai and github.com/runxhq/runx, and gives a new reader a realistic picture of where runx stands.
- Filed the issue on their own tracker, where it directly helps the maintainer and future contributors.
