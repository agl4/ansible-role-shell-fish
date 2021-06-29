# Desktop fish role

Ansible role to install and configure fish shell. Intended to use on `localhost` for the current user.

## Requirements

None.

## Role Variables

None required.

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

None.

## Example Playbook

    - hosts: localhost
      vars:
      roles:
         - agoloncser.shell_fish

## License

BSD

## Author Information

https://github.com/agoloncser
