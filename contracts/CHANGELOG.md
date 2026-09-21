# openDox Contract Changelog

Status: standard

The project's release history. A bundle is `dox-v<major>.<minor>` and is
identified by four coordinated values: `contract_bundle_version` in
[`manifest.yaml`](./manifest.yaml), that file's `entries:` rows with their
per-file `contract_schema_version` and SHA-256, an annotated
`dox-v<major>.<minor>` tag over the root commit that names both legs, and the
matching entry below. **Consumers pin the exact commit and digests — a movable
branch or tag is not a compatibility pin.** The root holds no contract bytes of
its own, so a bundle is the LEGS at the commits `contracts/spec-pin.yaml` and
`contracts/code-pin.yaml` name.

**Release-surface rule.** `dox-vN.M` selects `{ entry | entry.release_member ==
true }` from `manifest.yaml` — by declared field, never by a path heuristic.
Membership is catalog-driven from openxFactory's
`contracts/hermes-runtime/contract-index.yaml` and is not this project's to
assert.

**`Status: standard`, on the operator's word, with all four coordinated values
now in place.** This entry landed BEFORE its tag existed — openxFactory's own
lane/operator split (RULED ASK-9a → 1: *"the lane authors and lands the cut PR …
the annotated tag is Brett's act"*) — and while the tag did not exist a
`standard` header would have asserted a published bundle that did not, so the
header read `draft` through that window and the promotion was registered as an
open question on `opensoft/openxFactory` issue #656 (comment 5767092136).

**That window is closed.** `dox-v1.0` is cut and published: annotated tag object
`608236a19ccd93fbfccf01b96035ff257b3c4b19`, over `dc7aa08fe48c8d17b596b0daa1ce87cdc0472aca`, tagger
Brett Heap, 2026-09-21T20:59:17Z. So `contract_bundle_version` in
[`manifest.yaml`](./manifest.yaml), that file's `entries:` rows with their
per-file digests, the annotated tag, and the entry below now all name the same
bundle together — which is the coordinated identity
`opensoft/openXwallet`'s contract changelog describes and the reason it carries
`Status: standard` too. Promoted on Brett Heap's word, verbatim 2026-09-21:

> **"(a) for all four, (i) for the tag, keep going"**

— item 3, recorded at [#656 comment
5767804734](https://github.com/opensoft/openxFactory/issues/656#issuecomment-5767804734).
`openxFactory`'s own contract changelog still carries `draft` across twenty-plus
published releases and `docs/document-lifecycle.md` still does not mention a
changelog; neither was ever a rule, and neither is now an argument about this
one.

## Unreleased

- 2026-09-21: nothing pending. `openDox-spec` main is `8fe8c4c7`, the commit
  this bundle pins, and `openDox-code` carries no `contracts/` path at any
  commit — its main has advanced past this root's pin to `1d4ac83c` (#33, test
  hygiene behind the pin), which moves no contract byte.

## dox-v1.0 — 2026-09-21 (the first bundle: openDox's contract surface is the carved spec leg's three schemas, two of them openxFactory catalog release members consumed at this pin)

Realizes `split-opendox-two-layer-product` **§ 3.8** (`tasks.md` § 3). Cut under
RULED **(a)** — Brett Heap, 2026-09-21, `opensoft/openxFactory` issue #656
comment `5767052465`, on the RULING NEEDED at `5738327369`:

> **"(a) for both, cut the tags when the drafts are green."**

**Change class: the first bundle.** There is no predecessor to be compatible
with, so no migration path is owed and none is claimed. `contract_bundle_version`
moves `none` → `dox-v1.0` and `entries: []` gains three rows.

### What the bundle is

The root commit that names both legs, and those legs:

| leg | repository | commit | contract bytes |
|---|---|---|---|
| code | `opensoft/openDox-code` | `d816cf06f1c9752a39c2b71ba40adc4ae3f3bf66` | none — no `contracts/` path at any commit |
| spec | `opensoft/openDox-spec` | `8fe8c4c71c4da8d363394441ad9e2c9547e540a3` | the three schemas below |

| `id` | path in the spec leg | `sha256` | `release_member` |
|---|---|---|---|
| `xfactory-workbench-chat-turn` | `contracts/schemas/xfactory-workbench-chat-turn.schema.yaml` | `350bfedc02696e7281a42c0bdc9a25059bf7af14d16d89d9f07018d3e691dc1d` | **true** |
| `xfactory-workbench-model-catalog` | `contracts/schemas/xfactory-workbench-model-catalog.schema.yaml` | `e563cc9fc6ede03dfd62537935d0ae0842617d7de46702aee6ad9026aa021635` | **true** |
| `ideation-workbench` | `contracts/schemas/ideation-workbench.schema.yaml` | `d30438491119c20928fbe4e85088fc33682829eeb6558d87dafce651000faafc` | false |

**NO CONTRACT BYTE MOVED TO REACH THIS BUNDLE, AND THE TWO MEMBERS PROVE IT.**
`xfactory-workbench-chat-turn` and `xfactory-workbench-model-catalog` carry at
`8fe8c4c7` exactly the digests openxFactory recorded for them at
`contract-v3.7` and re-asserted at `contract-v4.0` (its relocation table's
`350bfedc…` and `e563cc9f…`) — recomputed here from the pinned leg's own object
store, not copied from that table. openxFactory *"no longer OWNS them but still
CONSUMES them"*; this is the bundle at the other end of that sentence.
`ideation-workbench` is absent from `contract-index.yaml`'s 51 rows, so its
`false` is a measurement and not a judgement.

### The floor, four parts, one evidence line each

`split-opendox-two-layer-product` § 8.2 — RULED four-part floor (OQ-1), ticked
2026-09-19 by `tasks.md` amendment #8 (openxFactory **#1124** → `3e3b4587`).
**None of these is "the tests passed"** and no part substitutes for another:

1. **The carve manifest** — openxFactory **#865** → `17167481`: 454 rows, every
   file in exactly one disposition and every edit in one of three closed
   classes, at `carve_commit b075fd91dc8fced8e1373825ba80220c33536bae`.
2. **The source→destination test mapping** (§ 5.4) — machine-checked at
   openxFactory **#1080** → `4b53ea99` (exit 0, Σ 4440 over 146 test-bearing
   rows), with clause (d) pinned at all three destinations: `openDox-code`
   **#29** → `373b05aa`, `openXdox-code` **#25** → `ab04453d`, and
   openxFactory's own `pytest-suite.yml` triple.
3. **The neutral conformance corpus green in EVERY destination** (§ 3.7) —
   `OK — 17 of 17` at a LANDED head in each: `openDox-code` `93ccc3dd`
   (re-read at main, #656 comment `5738152229`), `openXdox-code` `3ee8cd31`
   (`5736681367`), openxFactory `eb1880cb`.
4. **The snapshot-equivalence run's matching digests** (§ 5.5) — openxFactory
   **#1105** → `02967478`, with **#1110** → `313b2665` and **#1115** →
   `4101fbe9`. Per RULED **Q-P4 (a)** (#656 comment `5728856581`) this line also
   says § 4.4's domain profile reproduces openxFactory's own vocabulary.

### Provenance

The project was bootstrapped as three repositories by openRepoShape at
`e9c4827b` on 2026-09-06 (`split-opendox-two-layer-product` § 1) and released no
bundle until this one. Its contract bytes arrived by the carve recorded in
[`manifest.yaml`](./manifest.yaml)'s `carved_from:` — `opensoft/openxFactory` at
`b075fd91dc8fced8e1373825ba80220c33536bae`, tag `opendox-carve-0`, 123 code rows
and 56 spec rows.

### The tag

`dox-v1.0`, annotated, in `opensoft/openDox`, over the root commit that carries
these entries and names both legs. **Cut by the operator; no workflow makes it.**
Runbook `docs/opendox-cutover-runbook.md` § 9 Phase 6. Rollback is narrow and is
written first: delete the tag only before anything pins it — *a published bundle
is not unpublished*; after that the honest reversal is a following release.
