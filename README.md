# anyenv-fast-init

This is an anyenv plugin that privides alternative init command of anyenv,
which is faster than original.

This command reuses previous anyenv init command output as cache, so no
overhead to generate command list to be evaluated using shell. Also, this can
detect that caches is old and needs to recache wisely, when new envs were
installed.

## Example Execution Speed

About 3.5X ~ 10X times faster than original init.

```sh
# How to get command execution time below table
$ time (eval "$(command)")

# When
$ ls ~/.anyenv/envs
.keep
nodenv/
pyenv/
rbenv/
```

| command                        | time (s)    | note      |
| --                             | --          | --        |
| anyenv fast-init               | 0.07 ~ 0.03 | use cache |
| anyenv fast-init --cache-clear | 0.30 ~ 0.17 | no cache  |
| anyenv init - --no-rehash      | 0.24 ~ 0.15 |           |
| anyenv init -                  | 0.30 ~ 0.24 |           |

## Installation

```sh
$ mkdir -p $(anyenv root)/plugins
$ git clone https://github.com/a5ob7r/anyenv-fast-init.git $(anyenv root)/plugins/anyenv-update
```

## Usage

```sh
# In your rc file, remove or make comment out eval "$(anyenv init -)".
eval "$(anyenv fast-init)"
```
