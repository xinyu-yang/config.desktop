# config.desktop

Debian 13 KDE desktop bootstrap and shell configuration.

Managed components:

```text
bash
neovim
tmux
lf
```

This desktop variant intentionally removes the old server-oriented fish and proxy
helpers. It also aligns defaults with the current machine:

- terminal: `konsole`
- browser env: `microsoft-edge`
- shell: `bash`

The `run` script is designed to be conservative on an existing desktop system:

- it links configs when safe,
- it skips files that already exist and are not managed by this repo,
- it prefers Debian packages for missing tools instead of building from source.

Prerequisites:

- `bash`
- `git`
- optional sudo access for package installation

Usage:

```bash
./run
```

Notes:

- XDG browser associations should use `microsoft-edge.desktop`.
- The repo bootstraps Neovim from `xinyu-yang/myvim` only when `~/.config/nvim`
  does not already exist.
