**Starting and managing sessions**

- Start a new session: `tmux` or `tmux new`
- Start a new named session: `tmux new -s session_name`
- Attach to last session: `tmux attach` or `tmux a`
- Attach to named session: `tmux attach -t session_name`
- List sessions: `tmux ls`
- Kill a session by name: `tmux kill-ses -t session_name`
- Kill all sessions but the current: `tmux kill-ses -a`
- Kill all sessions but 'myname': `tmux kill-ses -a -t myname`

**Windows (tabs)**

- Create new window: `Prefix + c`
- Move to next window: `Prefix + n`
- Move to previous window: `Prefix + p`
- List windows: `Prefix + w`
- Rename window: `Prefix + ,`
- Close current window: `Prefix + &`

**Panes (splits)**

- Vertical split: `Prefix + %`
- Horizontal split: `Prefix + "`
- Move to pane to the right: `Prefix + →`
- Move to pane to the left: `Prefix + ←`
- Move up to pane: `Prefix + ↑`
- Move down to pane: `Prefix + ↓`
- Go to next pane: `Prefix + o`
- Go to last active pane: `Prefix + ;`
- Convert pane to window: `Prefix + !`
- Kill pane: `Prefix + x`

**Copy mode**

- Enter copy mode: `Prefix + [`
- Paste from buffer: `Prefix + ]`
- Start selection: `Space`
- Copy selection: `Enter`
- Clear selection: `Esc`

**Resizing panes**

- Resize down: `resize-pane -D 20`
- Resize up: `resize-pane -U 20`
- Resize left: `resize-pane -L 20`
- Resize right: `resize-pane -R 20`

**Miscellaneous**

- List all shortcuts: `Prefix + ?`
- Show every session, window, pane, etc.: `Prefix + i`
- Reload config: `tmux source-file ~/.tmux.conf`
- Show config: `tmux show-options -g`

The default prefix is `Ctrl + b`. You can change it by modifying your `.tmux.conf` file. For example, to set the prefix to `Ctrl + a`, add this line to your `.tmux.conf` file: