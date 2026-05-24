# rofi-vscode-picker

Pick a recent VS Code project via rofi and open it.

Reads the recent-workspaces list from VS Code's SQLite state DB (`~/.config/Code/User/globalStorage/state.vscdb`), shows them in the most recent order with `rofi -dmenu`, and opens the chosen folder with `code`.

## Why
I find it very useful to be able to quickly jump to any project/worktree without having to look for anything other than the project's name.

Previously I was using [Coffelius/rofi-code](https://github.com/Coffelius/rofi-code), but it doesn't work for rofi 2.0+ and has a `go` dependency.

## Requirements

- Python 3.10+ (stdlib only — no pip deps)
- `rofi`
- `code` (VS Code CLI)

## Install

```bash
ln -s "$(pwd)/rofi-vscode-picker" ~/.local/bin/rofi-vscode-picker
```

Or just call the script by absolute path from your sway/i3 binding.

## Sway binding

```
bindsym $mod+Shift+d exec rofi-vscode-picker
```

## What it skips

Entries that aren't a directly-openable local folder:
- `vscode-remote://` (dev containers, SSH targets)
- `vscode-vfs://` (GitHub web editor)
- Individual `fileUri` entries
- Folders that no longer exist on disk
