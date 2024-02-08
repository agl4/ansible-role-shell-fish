# Desktop fish role

[![Molecule testing](https://github.com/agl4/ansible-role-shell-fish/actions/workflows/ci.yml/badge.svg)](https://github.com/agl4/ansible-role-shell-fish/actions/workflows/ci.yml)

Ansible role to configure fish shell. Intended to use on `localhost`
for the current user.

The `fish` shell must be installed prior using this role.

## Requirements

None.

## Role Variables

None required.

### `fish_config`

List, that adds lines to `config.fish`.

``` yaml
fish_config:
  - set -x LC_ALL en_US.UTF-8
  - set -x LC_CTYPE en_US.UTF-8
```

### `fish_vi`

Enables `fish_vi_key_bindings` when `true`.

### `fish_aliases`

Add aliases with this variable.

``` yaml
fish_aliases:
  - name: v
    definition: vagrant
  - name: bv
    definition: bumpversion
```

### `fish_paths`

Add directories to `PATH`.

``` yaml
fish_paths:
    - "$HOME/bin"
    - "$HOME/.local/bin"
```

### `fish_functions`

Define Fish functions. Will create a file for each entry in `functions/`.

``` yaml
fish_functions:
  - name: hh
    definition: |
      function hh --description 'Fuzzy find history'
        eval (history | fzf $__FZF_OPTIONS)
      end
```
### `fish_confd`

Create Fish conf.d definitions. This will create a file in `conf.d/` for each entry:

``` yaml
fish_confd:
  - name: hh
    definition: |
        __FZF_OPTIONS="--no-color --no-sort --exact"
```


### `fish_env`

Set environment variables:

``` yaml
shell_env:
  - name: EDITOR
    value: vi
```

## Dependencies

On Ubuntu it depends on `agl4.ubuntu_ppa`.

## Example Playbook

``` yaml
    - hosts: localhost
      vars:
      roles:
         - agl4.shell_fish
```

## License

BSD

## Author Information

[github.com/agl4](https://github.com/agl4)
