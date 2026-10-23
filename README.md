# runx — first-run walkthrough

A short, honest walkthrough of trying out [runx](https://github.com/runxhq/runx) — "the governed runtime for agent skill workflows, off the leash but on the record". Upstream links: https://runx.ai and https://github.com/runxhq/runx.

## What I tried

The smallest complete example from the README, on a fresh Linux machine:

```bash
git clone --depth 1 https://github.com/runxhq/runx.git
cd runx
npm install --global @runxhq/cli
runx skill ./examples/hello-world --run-id first-run -i message="Hello, Runx." --json
```

## What actually happened

It failed before running the example — with a YAML parse error in a **bundled** connector manifest:

```
connector execution binding is invalid: connector manifest
connectors/coinbase/cdp/connector.yaml is invalid: yaml: YAML parse failed:
operations.payment.x402.merchant.refund.amount: invalid type: map, expected a
YAML tag starting with '!' at line 102 column 7
```

In `connectors/coinbase/cdp/connector.yaml` the `payment.x402.merchant.refund.amount` field (line 102) is a plain map:

```yaml
amount:
  units: {"$argument": "/amount_minor"}
  currency: {"$argument": "/currency"}
```

while the validator expects a YAML scalar starting with a `!` tag (like the neighboring `template: {"$argument": "/resource"}` style). The example skill never gets to run because manifest validation blows up first.

I reported this upstream: https://github.com/runxhq/runx/issues/557

## Verdict so far

The concept is strong — skills as portable, URL-addressable expertise with explicit authority and verifiable receipts is exactly what agent tooling needs. But a first-time user who can't get past the quickstart won't stick around to see it. This looks like a small manifest/validator mismatch, very fixable. I'll re-run the quickstart once it's resolved and update these notes.

Env: Linux, Node v24.22.1, fresh `@runxhq/cli` install, 2026-10-23.
