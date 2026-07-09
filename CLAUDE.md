# ansible-nvm-role

Ansible role that installs NVM (Node Version Manager), a specific Node.js version, and optional global npm packages on Debian-based systems.

## Project structure

```text
tasks/
  main.yml        # entry point — orchestrates the four task groups
  nvm.yml         # downloads and sets up NVM, configures shell profile
  node.yml        # installs Node.js via nvm, sets default version
  pkgs.yml        # installs global npm packages (skipped when nvm_npm_pkgs is empty)
  permission.yml  # fixes .nvm directory ownership and copies .npmrc
files/
  .npmrc          # npm registry config copied into .nvm/
molecule/default/ # molecule test scenario
  molecule.yml    # docker driver config, junit report output
  prepare.yml     # creates testuser with sudo in the debian:bullseye container
  converge.yml    # runs the role with test variables
  verify.yml      # asserts nvm, node, .bashrc, .npmrc are correctly installed
```

## Role variables

| Variable | Default | Description |
| --- | --- | --- |
| `nvm_user` | `jenkins` | OS user that owns the NVM installation |
| `nvm_group` | `jenkins` | OS group for NVM directory ownership |
| `nvm_working_path` | `/var/lib/jenkins` | Home directory of `nvm_user` |
| `nvm_dest` | `/var/lib/jenkins/.nvm` | NVM installation directory |
| `nvm_version` | `0.39.7` | NVM release to install |
| `nvm_node_version` | `20.11.0` | Node.js version to install via NVM |
| `nvm_npm_pkgs` | `[]` | List of `{pkg, version}` dicts to install globally |

## Testing with Molecule

Tests run inside a `debian:bullseye` Docker container. Docker must be running locally.

### Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r molecule/default/requirements.txt
```

### Run the full test cycle

```bash
molecule test
```

This runs: `prepare` → `converge` → `verify` → `destroy`.

### Useful individual steps during development

```bash
molecule converge          # apply the role (re-runs are idempotent)
molecule verify            # run assertions only
molecule login             # open a shell in the test container
molecule destroy           # remove the container
molecule test --destroy=never  # keep container after failure for inspection
```

### JUnit test reports

After `molecule test`, XML reports are written to:

```text
molecule/default/reports/
├── ansible-converge.xml
└── ansible-verify.xml
```

GitLab CI publishes these automatically via the `artifacts.reports.junit` key.

## Linting

Uses `ansible-lint` with the `min` profile.

```bash
ansible-lint
```

Key rules enforced:

- **fqcn** — all module calls and `become_method` must use fully-qualified names (`ansible.builtin.copy`, `ansible.builtin.sudo`)
- **no-free-form** — modules must use YAML key/value form, not inline `key=value` strings
- **jinja[spacing]** — Jinja2 variables must have spaces: `{{ var }}` not `{{var}}`
- **no-jinja-when** — `when:` clauses must not wrap expressions in `{{ }}`: use `when: var | length > 0`
- **no-changed-when** — `shell`/`command` tasks must declare `changed_when`
- **yaml[truthy]** — use `true`/`false`, not `yes`/`no`
- **yaml[octal-values]** — file modes must be quoted strings: `mode: "0755"` not `mode: 0755`

## Commits

This project follows [Conventional Commits](https://www.conventionalcommits.org/).

### Format

```text
<type>(<scope>): <description>

[optional body]
```

### Types

| Type | When to use |
| --- | --- |
| `feat` | New capability added to the role |
| `fix` | Bug fix in task logic |
| `chore` | CI, tooling, dependency updates — no role logic change |
| `refactor` | Code restructure with no behaviour change |
| `test` | Molecule scenarios or verify tasks only |
| `docs` | README, CLAUDE.md only |

### Scope (optional)

Use the task file name without extension: `nvm`, `node`, `pkgs`, `permission`, `ci`.

### Examples

```text
feat(node): support installing multiple Node.js versions
fix(nvm): run install.sh after downloading to create nvm.sh
chore(ci): switch runner to shell executor with venv
test: add verify assertions for .npmrc permissions
refactor: replace deprecated include with include_tasks
docs: update role variables table in README
```

### Rules

- Subject line: imperative mood, no period, max 72 characters
- Do not reference internal ticket numbers in the subject line
- Breaking changes: add `!` after the type/scope and describe in the body
