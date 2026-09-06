# Contributing to openDox

openDox is a single project spread across **three repositories**:

| role | repository | path | holds |
|---|---|---|---|
| assembly | [`opensoft/openDox`](https://github.com/opensoft/openDox) | `.` | this manifest, the pins, the gate |
| spec | [`opensoft/openDox-spec`](https://github.com/opensoft/openDox-spec) | `spec/` | requirements, decisions, acceptance |
| code | [`opensoft/openDox-code`](https://github.com/opensoft/openDox-code) | `code/` | the implementation and its tests |

This file is the ONE contribution posture for all three; each leg's own
`README.md` points back here rather than repeating it.

## Where things go

- **Issues** — file them on the assembly root,
  [`opensoft/openDox`](https://github.com/opensoft/openDox/issues), regardless
  of which leg the problem turns out to live in. Triage moves an issue to the
  right leg by reference, not by re-filing it.
- **Pull requests** — open them against the LEG that owns the change: a
  requirements or acceptance-criteria change goes to `opensoft/openDox-spec`,
  an implementation change to `opensoft/openDox-code`. A change that touches
  the project's own posture, manifest or pins (this repository's own files)
  goes to `opensoft/openDox` itself.
- **The lockstep pins** (the gitlink, `contracts/spec-pin.yaml` /
  `contracts/code-pin.yaml`, and any workflow `@<sha>` reference naming a leg)
  are **never hand-edited**. They move together, in one commit, by
  `scripts/bump-leg.py --root . --leg spec|code --to <commit>` — the tool
  that fetches the leg's new commit, recomputes its tree digest, rewrites the
  pin and any workflow reference, and runs the root's own validators before
  committing. A gitlink advanced by hand and a pin file advanced separately
  is exactly the drift `scripts/validate-pins.py` refuses on every pull
  request.

## Before you open a pull request

- Run that leg's own test suite and `validate` workflow locally where you
  can (`python -m pytest -q`; for `opensoft/openDox-spec`, also
  `OPENSPEC_TELEMETRY=0 openspec validate --all --strict`). For this
  assembly root: `make validate` (naming, manifest, lockstep pins).
- Every pull request against any of the three repositories runs a required
  `validate` check and gets an automatic Copilot review; branch protection
  on the default branch means it lands by pull request, never a direct push.

## License

openDox is licensed under the [Apache License 2.0](LICENSE) in all three
repositories. By contributing, you agree that your contribution is licensed
under the same terms — inbound is outbound, with no side agreement.

## Code of Conduct

Participation in this project is governed by
[CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). Report a violation the same way
[SECURITY.md](SECURITY.md) describes for a vulnerability: privately, not as
a public issue.
