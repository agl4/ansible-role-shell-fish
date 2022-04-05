# Desktop fish role

[![Molecule testing](https://github.com/agoloncser/ansible-role-shell-fish/actions/workflows/ci.yml/badge.svg)](https://github.com/agoloncser/ansible-role-shell-fish/actions/workflows/ci.yml)

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

Define fish functions:

``` yaml
fish_functions:
  - name: hh
    definition: |
      function hh --description 'Fuzzy find history'
        eval (history | fzf --no-color --no-sort --exact)
      end
```

### `fish_env`

Set environment variables:

``` yaml
shell_env:
  - name: EDITOR
    value: vi
```

## Dependencies

On Ubuntu it depends on `agoloncser.ubuntu_ppa`.

## Example Playbook

``` yaml
    - hosts: localhost
      vars:
      roles:
         - agoloncser.shell_fish
```

## License

BSD

## Author Information

[github.com/agoloncser](https://github.com/agoloncser)
