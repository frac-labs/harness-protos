# harness-protos

gRPC contracts shared by the frac-labs agentic harnesses (`frac`, `fractury`) and the in-cluster bridge / webhook-router / secrets services.

## Services (v1)

- `frac_labs.harness.v1.Bridge` — `EnqueueTicket`, `EmitEvent`
- `frac_labs.harness.v1.Secrets` — `MintGitHubToken`, `GetSecret`

Source: `proto/frac_labs/harness/v1/*.proto`

## Tooling

[`buf`](https://buf.build) for lint, breaking-change detection, and codegen.

- `buf lint` — STANDARD ruleset (see `buf.yaml`)
- `buf breaking --against '.git#branch=main'` — FILE policy
- `buf generate` — Go + TS-ESM stubs into `gen/go/` and `gen/ts/` (gitignored; built by the release workflow)

## Consuming

Once `v0.1.0` is tagged:

```
# Go
go get github.com/frac-labs/harness-protos@v0.1.0
import harnessv1 "github.com/frac-labs/harness-protos/gen/go/frac_labs/harness/v1"

# TypeScript (GitHub Packages, @frac-labs scope)
npm install @frac-labs/harness-protos@0.1.0
```

## Versioning

Package path carries the major version (`v1`). Breaking changes happen in a sibling package (`v2`), never in-place on `v1`.

## Provenance

Tracks `frac-labs/clawdiovascular#9` ("B1: harness-protos repo + gRPC contract"). Design comment lives on that issue.
