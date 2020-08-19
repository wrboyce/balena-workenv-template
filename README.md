# balena-workenv-template

A [zsh-workenv](https://github.com/wrboyce/zsh-workenv) template for Balena development.

## Installation

Create a new working environment using this repository as the template

```bash
WENV_TEMPLATE="https://github.com/wrboyce/balena-workenv-template.git" mkwenv <wenv-name> [wenv-project-dir]
```

## Usage

### `balena aws <context>`

Switch AWS and K8s contexts between production / staging / playground.

### `balena devops-playbook`

Launch an interactive devops playbook using `fzf`, unfortuantely requires [my fork of `fzf`](https://github.com/junegunn/fzf/pull/1867) currently.

### `balena enter [-E <env-name>] <uuid> [container-id]`

Connect to the given device, on the given environment, via ssh.

### `balena env <env-name>`

Automatic environment switching and token handling for [`balena-cli`](https://github.com/balena-io/balena-cli).

A valid `env-name` is one of `prod`/`cloud`, `stag`/`staging`, `dev`, or `bob`.

### `balena envs`

List available/active balena-cli environments.

### `balena upgrade [version]`

Update `balena-cli` to the specified version. If no version is specified, use the latest tagged version.

### `bob bootstrap`

Create `/usr/local/bin/enter` on BoB host for easy container access, and optionally configure balena-engine
with a Docker registry mirror (defined by `BALENA_BOB_REGISTRY_MIRROR`)

### `bob build <service>`

Mark a service for building in the bob composefile.

### `bob import-image <device-type> <version> [file]`

Import an OS image into BoB either from staging or the provided image.

### `bob logs [service|"system"]`

Stream logs from BoB.

### `bob push [...]`

Push the latest changes to BoB; operates in live mode and pushes all services by default.

### `bob reinit`

Reinitialise the BoB composefile and dockerignore.

### `bob ssh [...]`

Open an SSH connection to the BoB host, optionally sending a command.

### `bob ssh-add [...]`

Add the BoB devices key to the SSH Agent.

### `bob unbuild <service>`

Pull the given service from the latest tagged Docker image.

### `bob upgrade [version]`

Rebase `balena-on-balena` against `origin/master` and recompile `bob-cli`.

## Configuration

Config goes in `${WORK_ENV}/config`

### `BALENA_ROOT`

Default: `${WENV_PROJ}`

### `BALENA_BOB`

Default: `${BALENA_ROOT}/bob`

### `BALENA_BOB_HOST`

Default: `10.10.10.10`

### `BALENA_BOB_DOMAIN`

Default: `balena-dev.com`

### `BALENA_BOB_REGISTRY_MIRROR`

Default: `None`

### `BALENA_CLI`

Default: `${BALENA_ROOT}/cli`

### `GIT_COMMITTER_EMAIL`

Default: `${USERNAME}@balena.io`

### `GIT_AUTHOR_EMAIL`

Default: `${USERNAME}@users.github.com`
