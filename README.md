# resin-workenv-template

A [zsh-workenv](https://github.com/wrboyce/zsh-workenv) template for resin.io development.

## installation

Create a new working environment using this repository as the template

```bash
WENV_TEMPLATE="https://github.com/wrboyce/resin-workenv-template.git" mkwenv <wenv-name> [wenv-project]
```

## usage

### `resin env <env-name> [env-url]`

Automatic environment switching and token handling for [`resin-cli`](https://github.com/resin-io/resin-cli).

`env-url` is optional if `env-name` is one of `prod`, `stag`, or `dev`.

### `resin update [version]`

Update `resin-cli` to the specified version. If no version is specified, update to the latest master build.

### `wiki [context] <search-term>`

Search the [resin wiki](https://github.com/resin-io/hq/wiki). If the first argument is numeric it will be treated as a context argument.

### `import-images`

Wrapper around the `import-images` tool, automatically providing [jenkins credentials](#jenkins).

### `rs`

Shortcut to `resin`.

### `ex`, `xc`

Shortcuts to edit/diff the `resin-containers/docker-compose.yml` file.

### `vv`

Shortcut for running `vagrant` commands against `resin-containers` guest.

### `vcmd <cmd>`

Run `cmd` on the `resin-containers` vagrant guest.

### `vdc`

Shortcut for running `docker-compose` on the `resin-containers` vagrant guest, supports two
convenience commands:

#### `vdc upd`

Shortcut for `vdc pull && vdc up --daemon`

#### `vdc build`

Shortcut for `vdc up --daemon --build`

#### `enter`

Shortcut for running `enter` on the vagrant guest.

#### `vlog`

Shortcut for viewing Docker logs from within the vagrant guest.

## configuration

Config goes in `${WORK_ENV}/config`

### resin-containers

#### `RESIN_ROOT`

Default: `${WENV_PROJ}`

#### `RESIN_CLI`

Default: `${RESIN_ROOT}/cli`

#### `RESIN_CONTAINERS`

Default: `${RESIN_ROOT}/containers`

#### `RESIN_WIKI`

Default: `${RESIN_ROOT}/hq.wiki`

#### `RESIN_WIKI_GREP`

Default: `rg`

The `grep`-style command used for searching the wiki, defaults to `ripgrep`.

### Vagrant

#### `RESIN_DEVENV_BRIDGE`, `RESIN_DEVENV_CPU`, `RESIN_DEVENV_MEM`

Default: `none`

Used by the [resin-containers](https://github.com/resin-io/resin-containers) `Vagrantfile` to specify guest configurations.

### Jenkins

Used by `import-images` when grabbing device images from Jenkins.

#### `RESIN_JENKINS_USER`

Default: `$(whoami)`

#### `RESIN_JENKINS_API_KEY`

Default: `none`
