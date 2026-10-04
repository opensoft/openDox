# openDox

The ASSEMBLY ROOT of the `opendox` project — the repository you clone.
It holds no product code of its own: it holds the manifest that says what this
project IS, the two legs as submodules, and the pins that say which commit of
each leg this project is.

Scaffolded from [opensoft/openRepoShape](https://github.com/opensoft/openRepoShape)
at `e9c4827b85f50503bbdd9e5b4fac9d6c3d0baf63`. Elected by Brett Heap on 2026-09-05, against
`openxFactory docs/project-repo-schema.md`.

## Get started

```sh
git clone --recurse-submodules https://github.com/opensoft/openDox.git
cd openDox
make bootstrap
```

`make bootstrap` puts each leg on the `main` branch **at its
pinned commit** (so you are not staring at a detached HEAD), runs the three
neutral validators, and prints whatever review authority a wallet register
names for this project — or says plainly that authority is not wallet-carried
here, and continues.

## Install and run

Python 3.12 or later is required (the code leg's `requires-python`). The local
start also needs a POSIX platform, so native Windows is refused by name, and an
ordinary user: it refuses to run as root. The standalone install and its one
start are two lines:

```sh
pip install "opendox[local]"
opendox generate-and-open --local …
```

The flag selects the local mode explicitly, and the `local` extra carries the
runtime's packages and the bundled PostgreSQL server that mode starts. After the
install, that start is the single command a user runs. It needs no sibling
product, no database of the user's own, no identity broker and no model. The
start launches the bundled server as its own child, keeps its data and its
socket under `OPENDOX_STATE_DIR` (default `$XDG_STATE_HOME/opendox`, else
`~/.local/state/opendox`; an absolute path, short enough for a Unix socket),
opens no TCP port for it, and stops it when the command stops.

In local mode the server binds loopback only, so a non-loopback `--host` is
refused. It also answers only a request whose `Host` names it
(`127.0.0.1:<port>` or `localhost:<port>`, or `[::1]:<port>` where it is bound
to `::1`): any other, such as a tunnel's or a proxy's name, gets a 403
`invalid_host`.

The `…` stands for the verb's own arguments, which follow it as every option
does. Two are required: `--repo-root`, the plain git repository of Markdown
documents to open (front matter is not required), and `--repository`, a name
for it, which the snapshot records as its repository id. The served actor is
that repository's `git config user.name`. `--actor` is only a claim, and it
must match an identity the install can establish, so it cannot name an
arbitrary person. With no established actor (no `user.name`, or an unmatched
`--actor`) the page is served without its edit and session actions, no console
file is written, and the start prints only the plain URL. `--no-open` launches
no browser, `--port N` fixes the port, and `opendox generate-and-open --help`
lists the rest.

**Opening the page.** With an established actor, the start writes a private
copy of the console's opening page, `<OPENDOX_STATE_DIR>/console/<port>.html`
(mode 0600, this user's only), and prints its location as a `file://` URL, never
the console token, with or without `--no-open`. Without `--no-open` the browser
is opened through that copy. To open the page again, open the printed `file://`
URL: the copy forwards to the server's page and carries the token there. The
plain `http://127.0.0.1:<port>/index.html` URL the start also prints loads the
page without the token. The copy is removed when the command stops.

A browser that cannot reach the default state directory (`~/.local/state`)
cannot open the copy: a Snap or Flatpak browser, and a Windows browser running
under WSL, are the known cases. This is a known limit of release 1. The start
prints one extra line saying so, with no token. The remedy is to set
`OPENDOX_STATE_DIR` to a non-hidden folder this user owns, and to restart the
command, so that the copy is written there.

**Where `opendox` comes from.** `opendox` is the distribution this project's
code leg builds: `code/` here, which is `opensoft/openDox-code` at the commit
`contracts/code-pin.yaml` pins. Its `pyproject.toml` names it `opendox` and
declares the `local` extra and the `opendox` console script. As of 2026-10-04
no release of it is published to PyPI, so the first line has nothing to resolve
from the default package index. Until one is, install the same distribution and
extra from a recursive clone of this repository, run from its root, with
`pip install "./code[local]"` in place of the first line, and run the second
line unchanged.

This root adds no `make` target for the command: its `Makefile` carries a row
in `contracts/shape-pin.yaml`, so the entry point stays the code leg's console
script.

## The three legs

| role | repository | path | holds |
|---|---|---|---|
| assembly | `opensoft/openDox` | `.` | this manifest, the pins, the gate |
| spec | `opensoft/openDox-spec` | `spec/` | requirements, decisions, acceptance |
| code | `opensoft/openDox-code` | `code/` | the implementation and its tests |

All three carry the GitHub topic `xf-project-opendox`, so the organisation's own search
surfaces the group without a checkout.

## Reading private legs in CI: a GitHub App first, `SHAPE_LEGS_TOKEN` as fallback

If `opensoft/openDox-spec` or `opensoft/openDox-code` is **private or internal**,
the `validate` workflow's default `GITHUB_TOKEN` cannot clone it as a
submodule.

Preferred: a dedicated GitHub App — permissions **Contents: Read-only** and
**Metadata: Read**, installed on this organisation with access to the legs —
mints a short-lived token at run time:

```sh
gh secret set SHAPE_LEGS_APP_ID --org <your-org> --body '<app id>'
gh secret set SHAPE_LEGS_APP_PRIVATE_KEY --org <your-org> < app-private-key.pem
```

Fallback: a fine-grained **`SHAPE_LEGS_TOKEN`** PAT, `contents:read` on the
LEGS ONLY:

```sh
gh secret set SHAPE_LEGS_TOKEN --org <your-org> --body '<token>'
```

**On the GitHub Free plan, set these as REPOSITORY secrets.** GitHub delivers
an ORGANISATION secret only to PUBLIC repositories on Free, so on a private
repository `secrets.SHAPE_LEGS_APP_ID` is the empty string — silently — the
App steps skip, and `validate` goes GREEN with the lockstep pin check degraded
away rather than red. Use `--repo <org>/<Repo>` in place of `--org <your-org>`
above, or upgrade the organisation to Team. (Measured on InkRouter,
2026-09-04.)

The root repository itself is always readable by the workflow's own default
token, so `actions/checkout` never carries a `token:` override — putting a
legs-scoped credential there instead is what broke the ROOT checkout with a
403 the first time a PAT was tried for real. Whichever credential resolves is
read only inside the guarded "fetch the legs (submodules)" step, scoped to
that step's `env:`, and used through a `git -c url.<...>.insteadOf=<...>`
rewrite covering both HTTPS and SSH leg URLs — it never touches the root
checkout.

`validate` tries the App first — a `mint a leg-reader token from the GitHub
App` step, scoped by `repositories:` to the legs this organisation itself
owns (a leg under a different owner is excluded with a warning, since an
installation token is per-owner) — and falls back to `SHAPE_LEGS_TOKEN` when
the App is not configured. A configured App that fails to mint fails the job
outright, naming both secrets and the required installation, rather than
degrading.

Without either credential the workflow does not go red on that account: it
checks out the root without submodules, tries `git submodule update --init
--recursive` best-effort, and — if that fails — still runs the naming and
manifest checks, skips `validate-pins.py` with a warning explaining why, and
only fails outright if a credential (App or PAT) **is** configured and the
fetch still failed — naming which source it used. That presence check reads
job-level `env: SHAPE_LEGS_APP_SET` / `SHAPE_LEGS_TOKEN_SET` booleans rather
than the `secrets` context directly in the step's `if:` — the `secrets`
context is not allowed in a step-level `if:` expression, and using it there
makes GitHub reject the whole workflow file instead of just that step.

## The lockstep invariant

For each leg, THREE things name the same commit and they move in ONE commit:

1. the **gitlink** — the `160000` entry recorded at the leg's path
2. **`commit:`** in `contracts/<role>-pin.yaml`
3. every **`.github/workflows/*.yml` `@<sha>`** reference naming that leg

`python3 scripts/validate-pins.py` (also `make pins`, also the `validate` check
on every pull request) refuses if they disagree, and recomputes the leg's tree
digest on top. Advancing a pin is therefore one commit that touches the
submodule, the pin file, and any workflow ref — never a bare `git submodule
update` followed by a commit.

This is written down because the family learned it the expensive way: seven
consecutive pin-syncs in the xFactory aggregation moved the gitlink alone and
left `validate` red on every pull request for a day, unnoticed because the
check runs on pull requests only.

## What the election confers

Nothing. Electing this shape changes no gate, no floor, no grant and no
clearance eligibility; a one-repository project is reviewed identically,
because the authority travels in the grants rather than in the layout. The
`role:` fields in `project.yaml` are navigation. A tool that reads `role: spec`
as "spec authority lives here" has quietly turned a layout into a governance
boundary, and is defective.

## Layout

```
AGENTS-shape.md                  the RULES OF THE SHAPE, for an agent (copied)
AGENTS.md                        this project's own instructions (yours)
CLAUDE.md                        one line, pointing at AGENTS.md
project.yaml                     the manifest — the SOURCE of this group
contracts/repository-naming.yaml the four naming families (copied from the shape)
contracts/spec-pin.yaml          the spec leg's commit + tree digest
contracts/code-pin.yaml          the code leg's commit + tree digest
contracts/shape-pin.yaml         the openRepoShape revision + per-file digests
scripts/bootstrap.py             the one command after a recursive clone
scripts/validate-manifest.py     project.yaml, and the legs' names
scripts/validate-pins.py         THE LOCKSTEP VALIDATOR
scripts/validate-repository-naming.py
scripts/repo_shape.py            shared helpers, standard library only
.github/workflows/validate.yml   the neutral gate, on pull_request
```

Everything under `scripts/`, plus `contracts/repository-naming.yaml` and
`AGENTS-shape.md`, is a COPY from `opensoft/openRepoShape`, digest-pinned in
`contracts/shape-pin.yaml`. Edit them upstream, not here — a local edit is
reported as drift. `AGENTS.md` and `CLAUDE.md` have no row and are this
project's own.

## Posture

This repository carries the openDox project's posture files:
[CONTRIBUTING.md](CONTRIBUTING.md) (how to contribute across all three
repositories), [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md), and
[SECURITY.md](SECURITY.md) (security reports go through GitHub's private
vulnerability-reporting form, never a public issue). All three repositories
share the [Apache License 2.0](LICENSE). In all three, the `validate` check
is a required status check on `main`, enforced by a repository ruleset — see
[docs/branch-protection.md](docs/branch-protection.md).

## Documentation

The doc index for this repository. Everything under `docs/` is listed here,
and a new document is linked from this table in the same pull request that
adds it — the xFactory family's standing rule, levelled across all six
`openDox`/`openXdox` repositories by the OQ-O scaffold pass
(`opensoft/openxFactory#656`).

| document | what it is |
|---|---|
| [docs/branch-protection.md](docs/branch-protection.md) | the repository ruleset that makes `validate` a required status check on `main`, its `evaluate` → `active` history, and the one policy difference between the two families |
