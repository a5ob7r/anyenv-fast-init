# anyenv-fastinit

This is an anyenv plugin that privides alternative init command of anyenv,
which is faster than original.

This command reuses previous anyenv init command output as cache, so no
overhead to generate command list to be evaluated using shell. Also, this can
detect that caches is old and needs to recache wisely, when new envs were
installed.

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
