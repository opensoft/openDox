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

**`Status: standard` was first reached on the operator's word, with all four
coordinated values in place for `dox-v1.0`.** This entry landed BEFORE its tag
existed — openxFactory's own lane/operator split (RULED ASK-9a → 1: *"the lane
authors and lands the cut PR … the annotated tag is Brett's act"*) — and while
the tag did not exist a `standard` header would have asserted a published
bundle that did not, so the header read `draft` through that window and the
promotion was registered as an open question on `opensoft/openxFactory` issue
#656 (comment 5767092136). That window closed 2026-09-21: `dox-v1.0` is cut and
published, annotated tag object `608236a19ccd93fbfccf01b96035ff257b3c4b19`, over
`dc7aa08fe48c8d17b596b0daa1ce87cdc0472aca`, tagger Brett Heap,
2026-09-21T20:59:17Z, promoted on Brett Heap's word, verbatim:

> **"(a) for all four, (i) for the tag, keep going"**

— item 3, recorded at [#656 comment
5767804734](https://github.com/opensoft/openxFactory/issues/656#issuecomment-5767804734).

**`Status: draft` again over `dox-v1.1`'s own window, for the SAME reason, and
`standard` again once that window closed.** The cut PR
(`opensoft/openDox#14`) moved `contract_bundle_version` to `dox-v1.1` and added
its manifest row and the `dox-v1.1` section before the annotated `dox-v1.1` tag
existed — the same lane/operator split, on the SAME rule (RULED ASK-9a → 1).
RULED — Brett Heap, 2026-09-29, `opensoft/openxFactory` issue #656 comment
5894235642: *"Same as v1.0 (Recommended)"* — the lane authors and lands the cut
PR, and the annotated tag is cut over that root commit when the draft is green,
mirroring dox-v1.0's own `5767052465`. That window closed 2026-09-29: `dox-v1.1`
is cut and published, annotated tag object
`851a28e966d011518c19b0abd321502288ac12ea`, over
`520052139d10e98c2894abafa315fa924a6fd495` (the landed commit of #14), tagger
Brett Heap, 2026-09-29T18:43:27Z. The header promoted back to `standard` by the
same act as before, on the rule this paragraph registered while the window was
open, so no second open question was needed. `dox-v1.0` itself is unaffected:
its own tag, entries and digests stand as published above.

**`Status: draft` again over `dox-v1.2`'s own window, for the SAME reason, and
`standard` again now that the window has closed.** The cut PR
(`opensoft/openDox#20`, plan 038 T060) moved `contract_bundle_version` to
`dox-v1.2` and added its three manifest rows and the `dox-v1.2` section before
the annotated `dox-v1.2` tag existed — the same lane/operator split, on the SAME
rule (RULED ASK-9a → 1). R2Q22 (a) — Brett Heap, 2026-10-05,
`opensoft/openxFactory` issue #656 comment 6003486656, *"Accept all 25
recommended (Recommended)"* — gave openDox-spec the three health schemas and the
root one more `dox-v1.y` minor, and batch Q's 9.5 addendum
(`opensoft/openxFactory#1248`) reads: *"The cut is made on Brett Heap's cut
word, as `dox-v1.1`'s was (RULED `5894235642`)."* RULED — Brett Heap,
2026-10-06, `opensoft/openxFactory` issue #656 comment 6022291206: *"Cut
dox-v1.2 now (Recommended)"* — the cut word, given once the cut PR had landed.
That window closed 2026-10-06: `dox-v1.2` is cut and published, annotated tag
object `58538ff33a953ffd5dfa9b44a7edabd75dada00b`, over
`6a9f4902285029b4fb02753e2b79be0a137302c5` (the landed commit of #20), tagger
Brett Heap, 2026-10-06T17:58:45Z. The header promotes back to `standard` by the
same act as before, on the rule this paragraph registered while the window was
open, so no second open question was needed. `dox-v1.0` and `dox-v1.1` are
unaffected: their own tags, entries and digests stand as published.

`openxFactory`'s own contract changelog still carries `draft` across
twenty-plus published releases and `docs/document-lifecycle.md` still does not
mention a changelog; neither was ever a rule, and neither is now an argument
about this one.

## Unreleased

- 2026-10-06: nothing pending. `openDox-spec` main is `7db9438b`, the commit
  `dox-v1.2` pins. `openDox-code` carries no top-level
  `contracts/` path; `contracts/code-pin.yaml` pins `dede32b4` (plan 034 T087's
  phase-3 root pin, unmoved by this cut) — that is the BUNDLE'S pin, not a claim
  about the leg's own current `main`, which has since advanced independently of
  any contract byte.

## dox-v1.2 — 2026-10-06 (an additive minor: openDox's three health schemas, plan 038 T040)

Realizes plan 038 **T040** and **T060**
(`specs/038-opendox-document-tool-self-maintenance/`, `opensoft/openxFactory`),
Ruled R2Q22 (a) (`#656` comment `6003486656`), under batch Q's 9.5 addendum
(`opensoft/openxFactory#1248`). Cut on Brett Heap's cut word, as `dox-v1.1`'s
was (RULED `5894235642`); the lane asks for that word once this cut PR lands,
and it is recorded on `#656`.

**Change class: an additive minor.** `contract_bundle_version` moves
`dox-v1.1` → `dox-v1.2`. `entries:` gains three rows; the four `dox-v1.1` rows are
unedited in substance — only their `commit:` field advances with the spec
leg's pin, to the same commit this cut PR records below, because the leg's
gitlink and `contracts/spec-pin.yaml` move in the one commit
`scripts/validate-pins.py` requires. None of their `sha256` digests changes.

### What the bundle is

The root commit that names both legs, and those legs:

| leg | repository | commit | contract bytes |
|---|---|---|---|
| code | `opensoft/openDox-code` | `dede32b4b6f3d0f147d599776f83628c5af8ff3d` | none of its own — no top-level `contracts/` path (unchanged by this cut; last moved by plan 034 T087, unrelated). Its `src/opendox/contracts/` holds packaged COPIES of four of the spec leg's schemas, recorded at `f7ee3c76` by `copies.yaml` (plan 034 T057), whose `sha256` equal the four `dox-v1.1` rows below; the three new schemas are copied after this cut (plan 038 T041, T047, T054) |
| spec | `opensoft/openDox-spec` | `7db9438b4cc4446ab4e6ab5b552c220312deccc9` | the seven schemas below (`opensoft/openDox-spec#17`, squash-merged; same tree, `f143e7dc`, as its branch head `58383189`) |

| `id` | path in the spec leg | `sha256` | `release_member` |
|---|---|---|---|
| `xfactory-workbench-chat-turn` | `contracts/schemas/xfactory-workbench-chat-turn.schema.yaml` | `350bfedc02696e7281a42c0bdc9a25059bf7af14d16d89d9f07018d3e691dc1d` | **true** (unchanged) |
| `xfactory-workbench-model-catalog` | `contracts/schemas/xfactory-workbench-model-catalog.schema.yaml` | `e563cc9fc6ede03dfd62537935d0ae0842617d7de46702aee6ad9026aa021635` | **true** (unchanged) |
| `ideation-workbench` | `contracts/schemas/ideation-workbench.schema.yaml` | `d30438491119c20928fbe4e85088fc33682829eeb6558d87dafce651000faafc` | false (unchanged) |
| `opendox-snapshot` | `contracts/schemas/opendox-snapshot.schema.yaml` | `f9e3e111af1d4bd4c377c933027d81b582ae2b0a395b66f4e4621992454a584a` | false (unchanged) |
| `opendox-health-finding` | `contracts/schemas/opendox-health-finding.schema.yaml` | `6fb9b29f23a4270fa0310624d9e59b5d82e9888a5168600671e90ed30f781016` | false |
| `opendox-health-packs` | `contracts/schemas/opendox-health-packs.schema.yaml` | `8a7309eed0db788ea715b868cccfe4d5031cd7750862dc22abb2874df07ebfca` | false |
| `opendox-health-dispositions` | `contracts/schemas/opendox-health-dispositions.schema.yaml` | `f904bded8333b6e5f9edff756727a6c31cd9a7bfb050a66a76c212db2f0f1103` | false |

**The three health schemas are `false` by measurement, exactly as
`ideation-workbench` and `opendox-snapshot` are**: each is absent from
openxFactory's `contracts/hermes-runtime/contract-index.yaml` (its 51 rows,
read at openxFactory `main` `51456835`), so membership is not this project's to
assert (`manifest.yaml`'s own release-surface rule). `opendox-health-finding` is
one finding as `opendox health list --json` emits it, a shape the engine reads
and not a file kind (N-15); `opendox-health-packs` is `health/packs.yaml` and
`opendox-health-dispositions` is `health/dispositions.yaml`, each a file kind
whose `kind` constant equals its id.

### Provenance

No contract byte moved to reach this bundle from a source outside the arc:
the three schemas are new content the T040 writer authored in the spec leg from
plan 038's `contracts/health-finding.md`, `contracts/health-packs-manifest.md`
and `contracts/health-exceptions.md`, digest-verified above from the pinned
leg's own object store, not copied from anywhere. `dox-v1.0`'s own carve
provenance (`manifest.yaml`'s `carved_from:`) is unaffected and unchanged.

### The tag

`dox-v1.2`, annotated, in `opensoft/openDox`, over this root commit. **Not cut
by this pull request.** Cut by the operator on Brett Heap's cut word, which the
lane asks for once this cut PR lands (plan 038 T060; batch Q's 9.5 addendum),
the same two-step shape as `dox-v1.1`'s own comment `5894235642`. Runbook
`docs/opendox-cutover-runbook.md` § 9 Phase 6.

## dox-v1.1 — 2026-09-29 (an additive minor: openDox's own neutral snapshot contract, plan 034 T053)

Realizes plan 034 **T053** (`specs/034-opendox-standalone-operation/`,
`opensoft/openxFactory`), Ruled R1Q11 (a) and R1Q12 (a) (`#656` comment
`5850003126`). Cut under RULED — Brett Heap, 2026-09-29, `opensoft/openxFactory`
issue #656 comment `5894235642`:

> **"Same as v1.0 (Recommended)."**

**Change class: an additive minor.** `contract_bundle_version` moves
`dox-v1.0` → `dox-v1.1`. `entries:` gains one row; the three `dox-v1.0` rows are
unedited in substance — only their `commit:` field advances with the spec
leg's pin, to the same commit this cut PR records below, because the leg's
gitlink and `contracts/spec-pin.yaml` move in the one commit
`scripts/validate-pins.py` requires. None of their `sha256` digests changes.

### What the bundle is

The root commit that names both legs, and those legs:

| leg | repository | commit | contract bytes |
|---|---|---|---|
| code | `opensoft/openDox-code` | `2d116415159b721b55613fe20a159afc46202d1f` | none — no `contracts/` path at any commit (unchanged by this cut; last moved by plan 034 T039, unrelated) |
| spec | `opensoft/openDox-spec` | `f7ee3c763b3af4581daf1cd54406e5111e9358e6` | the four schemas below (`opensoft/openDox-spec#16`, squash-merged; same tree, `7b00d19e`, as its branch head `cd49eb25`) |

| `id` | path in the spec leg | `sha256` | `release_member` |
|---|---|---|---|
| `xfactory-workbench-chat-turn` | `contracts/schemas/xfactory-workbench-chat-turn.schema.yaml` | `350bfedc02696e7281a42c0bdc9a25059bf7af14d16d89d9f07018d3e691dc1d` | **true** (unchanged) |
| `xfactory-workbench-model-catalog` | `contracts/schemas/xfactory-workbench-model-catalog.schema.yaml` | `e563cc9fc6ede03dfd62537935d0ae0842617d7de46702aee6ad9026aa021635` | **true** (unchanged) |
| `ideation-workbench` | `contracts/schemas/ideation-workbench.schema.yaml` | `d30438491119c20928fbe4e85088fc33682829eeb6558d87dafce651000faafc` | false (unchanged) |
| `opendox-snapshot` | `contracts/schemas/opendox-snapshot.schema.yaml` | `f9e3e111af1d4bd4c377c933027d81b582ae2b0a395b66f4e4621992454a584a` | false |

**`opendox-snapshot` is `false` by measurement, exactly as `ideation-workbench`
is**: absent from openxFactory's `contracts/hermes-runtime/contract-index.yaml`
(the same 51 rows dox-v1.0 measured against), so membership is not this
project's to assert (`manifest.yaml`'s own release-surface rule). It covers
what openDox's own neutral generator writes over a plain repository and what
its views read, with no consumer installed; openXdox-spec's own
`ideation-dashboard-snapshot` is unchanged and untouched (R1Q12 (a)) — the two
contracts are siblings, not a migration.

### Provenance

No contract byte moved to reach this bundle from a source outside the arc:
the schema is new content the T053 writer authored in the spec leg, digest-
verified above from the pinned leg's own object store, not copied from
anywhere. `dox-v1.0`'s own carve provenance (`manifest.yaml`'s `carved_from:`)
is unaffected and unchanged.

### The tag

`dox-v1.1`, annotated, in `opensoft/openDox`, over this root commit. **Not cut
by this pull request.** Cut by the operator when the draft is green, RULED
`opensoft/openxFactory#656` comment `5894235642`, the same two-step shape as
`dox-v1.0`'s own comment `5767052465`. Runbook `docs/opendox-cutover-runbook.md`
§ 9 Phase 6.

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
